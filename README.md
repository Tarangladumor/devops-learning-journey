# devops-learning-journey

I'm a Full Stack Developer (Vue.js, React, Node.js, TypeScript) learning DevOps in public.

For about 6 months I've **studied** DevOps concepts. Now I'm **building and documenting** them hands-on, so this repo records what I actually run, what breaks, and what I learn from it.

> **Honest status:** the learning map below is what I've studied. The build log is where I turn it into practice. A week is marked done only after I've run it myself.

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

## Build log (practiced)

I'm building on a Next.js + Node/Express app I contribute to (the app's repos are private, so this repo holds only the DevOps files, with names and secrets removed).

| Week | Goal | Status |
|------|------|--------|
| 1 | Dockerize frontend and backend. Deploy on EC2 behind an Nginx reverse proxy. | ✅ Done: [week-1-docker-ec2](./week-1-docker-ec2) |
| 2 | GitHub Actions CI/CD: build, test, push to ECR, deploy to ECS | ⬜ Not started |
| 3 | Kubernetes on minikube or kind: Deployment, Service, Ingress, ConfigMap, Secret, HPA. Package with Helm. | ⬜ Not started |
| 4 | GitOps with ArgoCD, plus Prometheus and Grafana monitoring | ⬜ Not started |

Status key: ⬜ not started · 🟨 in progress · ✅ done and working

---

## Mistakes log

Everything that broke, and how I fixed it: [mistakes.md](./mistakes.md)

---

## Repo structure

```
devops-learning-journey/
├── README.md
├── mistakes.md
├── .gitignore
└── week-1-docker-ec2/
    ├── README.md
    ├── docker-compose.yml
    ├── Dockerfile.frontend
    ├── Dockerfile.backend
    ├── .env.example
    ├── server.env.example
    ├── nginx/default.conf
    └── docs/architecture.png
```

Each `week-*` folder has its own README: what I built, the architecture, the commands I ran, what broke, and what I'd do differently.

---

## Rules I'm following

- Only claim what I've actually run.
- No secrets, keys, or credentials in the repo. I use `.env.example` and placeholders.
- No company or client code, and no private project names.
- Set an AWS billing alarm first, and stop or terminate resources after each session.

---

## Posts

- Post 1: 6 months of DevOps, my learning map (add link)
- Post 2: Dockerized app on AWS EC2, and the 5 things that broke (add link)

---

## About me

**Tarang Ladumor** · Full Stack Developer · Vadodara, India
LinkedIn: https://www.linkedin.com/in/ladumortarang/
Email: tarangladumor@gmail.com

Feedback is welcome. If you spot a mistake or know a better way, please open an issue.
