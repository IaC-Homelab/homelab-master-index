# homelab-master 🏡☁️
Central repo for building, configuring, and deploying the entire homelab stack.  
Goal: push-button infra, best practices, and as cloud-agnostic as possible. ✨

<br>

*update: New Task board: [GitHub Project 📋](https://github.com/users/pukar10/projects/1)*
<br><br>

## Project Index 🚀

### 🖥️ Proxmox & VMs
- [`proxmox-deploy`](https://github.com/pukar10/proxmox-deploy)  
  Provision and configure VMs on Proxmox with Terraform + Cloud-Init.

### ☸️ Kubernetes
- [`k3-automation`](https://github.com/pukar10/k3-automation)  
  Deploy a lean Kubernetes cluster

### 🔐 Certificates & Secrets
- [`cert-manager-launch`](https://github.com/pukar10/cert-manager-launch)  
  Internal TLS via cert-manager

- `external-secrets-launch` (TBA)  
  Sync secrets between external secret stores and Kubernetes secrets, or generate your own

### 🗄️ Data & Auth
- [`cloudnativepg-launch`](https://github.com/pukar10/cloudnativepg-launch)  
  Manage Postgres clusters using CloudNativePG

- [`keycloak-launch`](https://github.com/pukar10/keycloak-launch)  
  Central SSO and identity management
<br><br>


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
🧑🏼‍🏭