# Mistakes log

Every error I hit while deploying, with the cause, the fix, and the lesson. Newest week first.

---

## Week 1: Docker + EC2 + Nginx

### 1. Next.js build killed on a 1 GB instance
- **Symptom:** `docker compose build` stopped during `next build`. No clear error, and no containers were created.
- **Cause:** the instance ran out of memory, and Linux killed the build process.
- **How I checked:** `free -h`, and `sudo dmesg | grep -i "out of memory"`.
- **Fix:** added a 2 GB swap file.
  ```bash
  sudo fallocate -l 2G /swapfile && sudo chmod 600 /swapfile
  sudo mkswap /swapfile && sudo swapon /swapfile
  ```
- **Lesson:** a silent build failure on a small server is often memory. Check before changing code.

### 2. `ENOSPC: no space left on device`
- **Symptom:** `npm ci` and `next build` failed with ENOSPC.
- **Cause:** the default EC2 root disk was about 7 GB, and Docker images, build cache and the swap file filled it.
- **How I checked:** `df -h /` and `docker system df`. Docker itself used under 1 GB, so the disk was simply too small.
- **Fix:** resized the EBS volume to 20 GB in the console, then grew the partition and filesystem while the instance kept running.
  ```bash
  lsblk
  sudo growpart /dev/nvme0n1 1
  sudo resize2fs /dev/nvme0n1p1
  df -h /
  ```
- **Lesson:** cleaning caches is not a fix when the disk is too small. Check the size first.

### 3. Browser timed out, but the containers were healthy
- **Symptom:** `ERR_CONNECTION_TIMED_OUT`, while `curl localhost:3000` returned 200 on the server.
- **Cause:** the security group did not allow the port from my IP.
- **Fix:** added inbound rules, then later switched to port 80 only through Nginx.
- **Lesson:** if it works on the server but not from outside, it's the network (security group, my changing IP), not Docker.

### 4. Frontend called an empty API URL
- **Symptom:** `WARN The "NEXT_PUBLIC_API_URL" variable is not set. Defaulting to a blank string.`
- **Cause:** `NEXT_PUBLIC_*` values are baked into the JavaScript at build time, and Compose reads `${VAR}` only from a `.env` next to the compose file or from `--env-file`, not from `env_file:`.
- **Fix:** passed the URL as a build arg and built with the right file.
  ```bash
  docker compose --env-file ./frontend/.env up -d --build client
  ```
- **Lesson:** changing a `NEXT_PUBLIC_` value needs a rebuild, not a restart. Also, the browser calls the API, so the URL must be reachable from the browser, not a Docker service name.

### 5. `docker compose` YAML error
- **Symptom:** `yaml: line 2: did not find expected key`.
- **Cause:** one service (`nginx:`) was indented with 3 spaces instead of 2.
- **Fix:** rewrote the file with a heredoc to avoid editor indentation problems, then validated with `docker compose config`.
- **Lesson:** run `docker compose config` before `up`.

### Bonus: `git clone` returned 403 for a private repo
- **Cause:** a fine-grained token cannot access another user's personal repo, even as a collaborator.
- **Fix:** a short-lived classic personal access token with `repo` scope, deleted after cloning.
- **Lesson:** keep tokens short-lived and never commit them. A read-only deploy key is the better long-term option.
