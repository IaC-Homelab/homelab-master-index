# Bootstrap

1. Updates & basic packages
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y ca-certificates git curl vim
```



2. Install Docker
```bash
# 2.1 Remove any conflicting packages
 sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc podman-docker containerd runc | cut -f1)

# 2.2 Add Docker offical GPG key
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# 2.3 Add Docker repo to apt sources
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

# 2.2 Install 
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# 2.3 Add user to docker group
sudo usermod -aG docker "$USER"

# 2.5 Verify (might have to relogin)
sudo systemctl status docker
docker run --rm hello-world
```



3. Install docker-compose
```bash
# 3.1 Update & install 
sudo apt-get update
sudo apt-get install docker-compose-plugin

# 3.2 Verify
docker compose version
```



3. Install Node
```bash
# 3.1 Download and install nvm:
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash

# 3.2 in lieu of restarting the shell
\. "$HOME/.nvm/nvm.sh"

# 3.3 Download and install Node.js:
nvm install 24

# 3.4 Verify  Node.js & npm version:
node -v 
npm -v
```