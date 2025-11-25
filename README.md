# Homeops 🏡⚙️  
_The ops brain for homelabs._

This repo is the **control center** for my homelab:

- Index of all my homelab repos
- Notes, guides, and “what did Past Me do to make this work?”
- Troubleshooting logs so Future Me doesn’t suffer (as much)

Goal: **documented, repeatable home infra** that feels more like a tiny cloud and less like a pile of sticky notes.

***Update**: New [Task board📋](https://github.com/users/pukar10/projects/1)*
<br><br>

## 🚀 Project Index (Other Repos)

### 🖥️ VMs (Proxmox)

- [`proxmox-deploy`](https://github.com/pukar10/proxmox-deploy)  
  Provision and configure VMs on Proxmox with Terraform + Cloud-Init.


### ☸️ Kubernetes

- [`k3-automation`](https://github.com/pukar10/k3-automation)  
  Deploy a lean Kubernetes cluster.


### 🔐 Certificates & Secrets

- [`cert-manager-launch`](https://github.com/pukar10/cert-manager-launch)  
  Internal TLS via cert-manager.

- `external-secrets-launch` (TBA)  
  Sync secrets between external secret stores and Kubernetes secrets, or generate your own.


### 🗄️ Data & Auth

- [`cloudnativepg-launch`](https://github.com/pukar10/cloudnativepg-launch)  
  Manage Postgres clusters using CloudNativePG.

- [`keycloak-launch`](https://github.com/pukar10/keycloak-launch)  
  Central SSO and identity management.


*(Add more as the homelab expands: media, monitoring, CI, etc.)*

<br>

## Roadmap ✅➡️🚧

### Done ✅
- [x] List desired homelab services and their purpose
- [x] Terraform to deploy VMs
- [x] Ansible to configure and install K3s
- [x] Ansible to configure and install Rook-Ceph
- [x] Upgrade to Proxmox 9
- [x] Decide secrets strategy (storage, push, usage)
- [x] Choose deployment strategy (Bootstrap vs ArgoCD) → **ArgoCD** 🎯

### Next Up 🚧
Refactor the **cp-deploy** project to use an ArgoCD *App of Apps* pattern to bootstrap:

- [ ] MetalLB
- [ ] ingress-nginx
- [ ] cert-manager
- [ ] external-secrets
- [ ] Infisical
- [ ] Bitwarden
- [ ] Rook-Ceph
- [ ] CloudNativePG (CNPG)
- [ ] Keycloak
- [ ] Gitea
- [ ] Nexus
- [ ] ArgoCD
- [ ] Kubernetes Dashboard
- [ ] Paperless
- [ ] Plex

<br>

## 📚 Docs, Notes & How-Tos

This repo will also hold markdown notes under something like `docs/` or `notes/`.

🧑🏼‍🏭
