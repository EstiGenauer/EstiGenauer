# 👋 Esther Genauer

## DevOps & Cloud Engineer · AWS · Terraform · CI/CD · Kubernetes

![AWS](https://img.shields.io/badge/AWS-Cloud-orange)
![Terraform](https://img.shields.io/badge/Terraform-IaC-purple)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI%2FCD-2088FF)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestration-blue)
![Docker](https://img.shields.io/badge/Docker-Containers-blue)
![Linux](https://img.shields.io/badge/Linux-System-yellow)

🌐 **Portfolio:** [portfolio-esther-genauer.vercel.app](https://portfolio-esther-genauer.vercel.app) · 📫 EstherGenauer@gmail.com

DevOps & Cloud Engineer at **GEMIT Diamonds**, a diamond trade-finance startup. I build and run the AWS platform with Terraform, ship it with GitHub Actions and OIDC, and give developers safe, fast access to what they need.

I come from software development (C#, Python), so I read the code I deploy and can fix it when a release needs it. I also take on freelance deployment projects.

---

# 💼 Experience

### DevOps Engineer · GEMIT Diamonds · 2026 – Present

*Diamond trade-finance marketplace · two-person DevOps team · two systems (Core and Compliance) and two development teams*

I own the Core system's infrastructure and Git workflow, and work across the Compliance system's infrastructure too.

**Cloud platform: AWS with Terraform**
- Built the Core platform as Terraform modules with remote state in S3: VPC, ALB with path-based routing, ECS Fargate (Spot in staging), private encrypted RDS PostgreSQL 16 with SSL enforced, ECR, Secrets Manager, SQS with a dead-letter queue, WAF, and S3 + CloudFront for the React frontend.
- Kept staging costs down with a NAT instance instead of a NAT Gateway and office-hours schedules that stop NAT, ECS and RDS outside working hours. Fixed NAT forwarding so it survives those restarts.
- Terraform plans run on pull requests with a read-only IAM role.

**CI/CD: GitHub Actions with OIDC**
- Moved both repos to trunk-based delivery: a merge to `main` deploys to staging, and production deploys from a manual dispatch behind a GitHub Environment.
- Backend deploy order: build an image tagged with the Git SHA, run the Alembic migrations as a one-shot ECS task with the same image (the deploy stops if they fail), roll the ECS service, then poll the health endpoint.
- Frontend deploy: build, sync to S3 (long-lived cache for assets, no cache for HTML), invalidate CloudFront, smoke test.
- Added hard-fail quality gates on pull requests: lint, format, types, migration checks, tests with coverage and a Docker build on the backend; ESLint, typecheck and Vitest on the frontend (test setup built from zero). Sped up pipelines with Docker Buildx layer caching (GitHub Actions cache) and npm caching.
- GitHub OIDC everywhere, with no stored AWS keys. Debugged a failing `AssumeRoleWithWebIdentity` by adding GitHub's org/repo-ID subject format to the IAM trust policy.

**Access, security and containers**
- Developer database access through SSM port-forwarding tunnels (no public database, no SSH), with a shared DML-only role for the developers of both systems, plus tunnel scripts and setup docs.
- Runtime secrets flow from Secrets Manager into ECS task definitions. Scoped IAM access to Amazon Bedrock for the Compliance system's AI copilot and OCR.
- Audited the Dockerfiles of both APIs and hardened them: secrets only at runtime, one image for every environment, non-root read-only containers with all capabilities dropped, `tini` as PID 1, pinned base-image digests, and faster cold builds (3:08 → 1:53).
- When a release needs it, I work in the application code too: Alembic migrations, HMAC-signed integration endpoints, and a production startup hotfix.

### Freelance Deployment Projects

- Taking on deployment projects for clients.

### DevOps Engineering Practicum · AWS Infrastructure for SBL · 2026

- Designed AWS infrastructure for a SaaS platform: reusable Terraform modules, CodePipeline/CodeBuild CI/CD, and CloudWatch/Grafana monitoring. Details below.

---

# 🛠 Tech Stack

| Category | Technologies |
|-----------|--------------|
| ☁️ Cloud | AWS (ECS Fargate, ECR, ALB, VPC, RDS, S3, CloudFront, SQS, IAM, Secrets Manager, Systems Manager, WAF, CloudWatch, EC2, Bedrock) |
| 🏗 Infrastructure as Code | Terraform (Modules, Remote State in S3, Environments, PR plans) |
| ☸️ Containers & Orchestration | Docker, Docker Compose, Kubernetes, Helm |
| 🚀 CI/CD | GitHub Actions (OIDC, Environments, trunk-based CD), Argo CD, AWS CodePipeline, AWS CodeBuild, Azure DevOps |
| 📊 Monitoring & Observability | Prometheus, Grafana, Loki, Promtail, Alertmanager, CloudWatch |
| 🔐 Security | IAM, Least Privilege, OIDC, Secrets Management, SSM tunnels, WAF, Trivy, TruffleHog |
| 🐧 Operating Systems | Linux |
| 💾 Databases | PostgreSQL, Amazon RDS, Alembic migrations |
| 🔧 Version Control | Git, GitHub |
| 💻 Programming | Python, Java, C#, JavaScript, TypeScript |

---

# ⭐ Featured Projects

## ☁️ AWS Infrastructure for SBL

A cloud infrastructure project designed with production principles using AWS and Terraform.

### Highlights

✅ Built reusable Terraform modules  
✅ Created separated Staging and Production environments  
✅ Automated infrastructure provisioning using Infrastructure as Code  
✅ Built CI/CD workflows using AWS CodePipeline and CodeBuild  
✅ Secured database access using AWS Systems Manager without public exposure  
✅ Implemented monitoring and alerting using CloudWatch, SNS, Lambda, and Slack notifications  
✅ Integrated Grafana Cloud using IAM AssumeRole  
✅ Applied security best practices including IAM least privilege and Secrets Manager  
✅ Defined AWS WAF and Auto Scaling cost-optimization schedules for production in Terraform  

### Architecture

```text
Developer
    |
GitHub Repository
    |
CI/CD Pipeline
    |
Terraform
    |
AWS Cloud

├── Default VPC
├── Security Groups
├── Elastic Beanstalk
├── RDS PostgreSQL
├── IAM
├── Secrets Manager
├── Systems Manager
├── AWS WAF
└── CloudWatch
        |
       SNS
        |
      Lambda
        |
      Slack
```

## 🤖 AI Learning Platform

[View Repository](https://github.com/EstiGenauer/ai-learning-platform)

End-to-End Cloud Native Learning Platform with AI integration.

A full-stack application built and deployed using modern DevOps practices.

### Technologies

React + TypeScript · .NET Web API · PostgreSQL · Docker · Kubernetes · Helm · GitHub Actions · Prometheus · Grafana · Loki

### Features

✅ JWT Authentication  
✅ AI-generated personalized learning content  
✅ Containerized application architecture  
✅ Kubernetes deployment  
✅ Automated CI/CD pipelines  
✅ Monitoring and logging infrastructure  
✅ Infrastructure automation  

## 🌍 Translator Platform

[View Repository](https://github.com/EstiGenauer/app-translator)

A containerized microservices-based translation application.

### Technologies

Node.js · PostgreSQL · Docker · Kubernetes · Helm · LibreTranslate

### Implemented

✅ Dockerized services  
✅ Kubernetes deployments  
✅ Helm-based configuration management  
✅ Service communication architecture  
✅ CI/CD automation workflows  

---

# 📚 Currently Learning

- Advanced AWS Architecture
- Production Kubernetes Patterns
- Platform Engineering
- MLOps Foundations
- FinOps and Cloud Cost Optimization

# 🌱 Engineering Philosophy

DevOps is not only about tools — it is about creating reliable systems and improving the way software is delivered.

I enjoy understanding systems end-to-end:
from application code, through infrastructure and automation, to deployment, monitoring, and continuous improvement.

I am always looking for opportunities to learn, collaborate, and build better engineering solutions.

# 📫 Connect With Me

- GitHub: https://github.com/EstiGenauer
- Email: EstherGenauer@gmail.com
- Portfolio: https://portfolio-esther-genauer.vercel.app


