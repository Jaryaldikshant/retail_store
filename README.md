# 🛒 Retail Store App 

A simple online store app that shows how modern cloud applications work using **AWS**, **Kubernetes**, and **automated deployments**.

## 🎯 What is this?

This is a **demo retail store** (like a mini Amazon) that demonstrates:
- How to build apps with **microservices** (small, independent parts)
- How to deploy on **AWS cloud** using **Kubernetes**
- How **GitOps** works (code changes automatically update your app)

## 🏗️ What's inside?

The store has 5 main parts:

| Service | What it does | Built with |
|---------|-------------|------------|
| **UI** | The website you see | Java |
| **Catalog** | Shows products | Go |
| **Cart** | Shopping cart | Java |
| **Orders** | Order history | Java |
| **Checkout** | Payment process | Node.js |

## 🚀 How does it work?

1. **Code lives in GitHub** (this repo)
2. **GitHub Actions** builds the app when you make changes
3. **Terraform** creates all the AWS infrastructure
4. **Kubernetes (EKS)** runs the app containers
5. **ArgoCD** keeps everything in sync automatically

Your Code → GitHub → AWS → Running App


## ⚡ Quick Start

**Prerequisites:** Install these first:
- AWS CLI
- Terraform
- kubectl
- Docker
- Helm

**Deploy the app:**

1. Clone this repo
git clone https://github.com/Jaryaldikshant/retail_store.git
cd retail_store

2. Configure AWS
aws configure

3. Create the infrastructure
cd terraform/
terraform init
terraform apply -target=module.retail_app_eks -target=module.vpc --auto-approve

4. Connect to your cluster
aws eks update-kubeconfig --name retail-store --region <your-region>

5. Deploy everything else
terraform apply --auto-approve

6. Get your app URL
kubectl get svc -n ingress-nginx

Visit the EXTERNAL-IP in your browser!
text

## 🔧 How to make changes

1. **Edit code** in the `src/` folders
2. **Push to GitHub** - GitHub Actions will build new images
3. **ArgoCD automatically updates** your running app
4. **That's it!** Your changes are live

## 📊 Monitor your app

**Check if everything is running:**
kubectl get pods -n retail-store

text

**Access ArgoCD dashboard:**
Get password
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d

Access UI
kubectl port-forward svc/argocd-server -n argocd 8080:443

Go to https://localhost:8080 (user: admin)
text

## 🧹 Clean up

Remove everything:
terraform destroy --auto-approve