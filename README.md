# devops-learning-journey

I'm a Full Stack Developer (Vue.js, React, Node.js, TypeScript) learning DevOps in public.

For about 6 months I've **studied** DevOps concepts. Now I'm **building and documenting** them hands-on, so this repo records what I actually run, what breaks, and what I learn from it.

> **Honest status:** the learning map below is what I've studied. The 30-day build log is where I turn it into practice. Items are only marked done once I've run them myself.

---

## Learning map (studied)

| # | Area | Topics |
|---|------|--------|
| 01 | **Foundations** | Domain vs IP, VMs and SSH, EC2 servers, Nginx, CI/CD, process management |
| 02 | **Docker** | Docker Engine and CLI, images and containers, Dockerfile, layers, registry, networks, volumes |
| 03 | **AWS** | Vertical scaling, Auto Scaling Groups, Elastic Load Balancer, ECR and ECS, logging and monitoring, Prometheus and Grafana, serverless backend |
| 04 | **Kubernetes** | Nodes and clusters, kubectl and manifests, Deployments and ReplicaSets, Services (ClusterIP, NodePort, LoadBalancer), Namespaces, Ingress and Ingress controller, ConfigMaps and Secrets, volumes, HPA, resource requests and limits |
| 05 | **GitOps and packaging** | Helm, GitOps, ArgoCD |

---

## 30-day build log (practiced)

I'm using one project, **E-waste Trade Hub** (MERN stack), as the base for every step.

| Week | Goal | Status |
|------|------|--------|
| 1 | Dockerize the app (Dockerfile, docker-compose). Deploy on EC2 behind Nginx, with SSH access. | ⬜ Not started |
| 2 | GitHub Actions CI/CD: build, test, push to ECR, deploy to ECS | ⬜ Not started |
| 3 | Kubernetes on minikube or kind: Deployment, Service, Ingress, ConfigMap, Secret, HPA. Package with Helm. | ⬜ Not started |
| 4 | GitOps with ArgoCD, plus Prometheus and Grafana monitoring | ⬜ Not started |

Status key: ⬜ not started · 🟨 in progress · ✅ done and working

---

## Repo structure

```
devops-learning-journey/
├── README.md
├── notes/                  # short notes per topic (what I understood, in my own words)
│   ├── 01-foundations.md
│   ├── 02-docker.md
│   ├── 03-aws.md
│   ├── 04-kubernetes.md
│   └── 05-gitops.md
├── week-1-docker-ec2/      # Dockerfile, docker-compose.yml, nginx.conf, README
├── week-2-cicd-ecs/        # .github/workflows, ECS task definition, README
├── week-3-kubernetes/      # manifests/, helm-chart/, README
├── week-4-gitops-monitoring/  # argocd/, prometheus/, grafana/, README
└── mistakes.md             # things that broke and how I fixed them
```

Each `week-*` folder has its own README with:
1. What I built
2. Architecture diagram or screenshot
3. Commands I ran
4. What broke and how I fixed it
5. What I'd do differently

---

## Rules I'm following

- Only claim what I've actually run.
- No secrets, keys, or credentials in the repo. I use `.env.example` and placeholders.
- No company or client code. Everything here is built on my own projects.
- Set an AWS billing alarm first, and shut down resources after each session.

---

## Posts

I share progress on LinkedIn as I go.

- Post 1: *6 months of DevOps, my learning map* (link coming)
- Post 2: *30 days of DevOps, the plan* (link coming)

---

## About me

**Tarang Ladumor** · Full Stack Developer · Vadodara, India
LinkedIn: https://www.linkedin.com/in/ladumortarang/
Email: tarangladumor@gmail.com

Feedback is welcome. If you spot a mistake or know a better way, please open an issue.
