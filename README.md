<div align="center">
  
# Homeops 🏡⚙️  
[![Proxmox Version](https://img.shields.io/badge/Proxmox-9.1.1-blue?logo=proxmox)](https://www.proxmox.com/en/proxmox-virtual-environment/overview)
[![K3s Version](https://img.shields.io/badge/K3s-v1.34.1-brightgreen?logo=kubernetes)](https://k3s.io/)
[![MetalLB Version](https://img.shields.io/badge/MetalLB-v0.15.2-9cf)](https://metallb.github.io/metallb)
[![Ingress NGINX Version](https://img.shields.io/badge/ingress--nginx-5.2.1-orange?logo=nginx)](https://kubernetes.github.io/ingress-nginx)

This repo is the **control center** for my homelab.    

</div>

- Index of various homelab repos
- Notes, guides, and “what did Past Me do to make this work?”
- Troubleshooting logs so Future Me doesn’t suffer (as much)

Goal: **documented, repeatable home infra** that feels more like a tiny cloud and less like a pile of sticky notes.


> [!TIP]  
> 🆕 Check out the project board: **[Task Board 📋](https://github.com/users/pukar10/projects/1)**
<br>

## 📚 Docs, Notes & How-Tos

This repo will also hold notes under something like `docs/` or `notes/`, including:

- Setup walkthroughs
- “Break/fix” postmortems
- Upgrade procedures
- Architecture diagrams and decisions
<br>

## 📂 Project Index

### 🧱 Terraform

- [`proxmox-automate`](https://github.com/pukar10/proxmox-deploy)  
  Provision and configure VMs on Proxmox using **Terraform + Cloud-Init**.

### ☸️ Kubernetes

- [`k3-automate`](https://github.com/pukar10/k3-automation)  
  Deploy a lean Kubernetes cluster.

  #### 🔐 Certificates & Secrets
  
  - [`cert-manager-launch`](https://github.com/pukar10/cert-manager-launch)  
    Internal TLS.
  
  - `external-secrets-launch` *(TBA)*  
    Sync secrets between external secret stores and Kubernetes secrets, or generate your own.
  
  #### 🗄️ Data & Auth
  
  - [`cloudnativepg-launch`](https://github.com/pukar10/cloudnativepg-launch)  
    Manage Postgres clusters.
  
  - [`keycloak-launch`](https://github.com/pukar10/keycloak-launch)  
    Central **SSO and identity provider** for apps and services.

🌐 Web Apps
  - [`pukarsubedi.com`](https://github.com/pukar10/pukar10.github.io)
    * [`pukarsubedi.com`](https://pukarsubedi.com/) hosted on github created with Jekyll
    * [`app.pukarsubedi.com`](https://app.pukarsubedi.com/) → 🔒 tunnel → 🪟 Caddy reverse proxy → 🖥️ homelab servers hosting apps!
  <br>


Happy Homelabbing 🧑🏼‍🏭
