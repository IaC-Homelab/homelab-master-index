# Bootstrap

1. Create admin user
```bash
sudo adduser admin
sudo usermod -aG sudo admin
```


2. Initial upgrades, packages, and setup
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y ca-certificates git curl vim

# Generate ssh-key
ssh-keygen -t ed25519 -C "subedipukar@gmail.com"

# Configure git user and email
git config --global user.name "Pukar Subedi"
git config --global user.email "subedipukar@gmail.com"
```



3. Install Docker
```bash
# 3.1 Remove any conflicting packages
sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc podman-docker containerd runc | cut -f1)

# 3.2 Add Docker offical GPG key
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# 3.3 Add Docker repo to apt sources
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

# 3.4 Install 
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# 3.5 Add user to docker group
sudo usermod -aG docker "$USER"

# 3.6 logout and login

# 3.7 Verify
sudo systemctl status docker
docker run --rm hello-world
```



4. Install docker-compose
```bash
# 4.1 Update & install 
sudo apt-get update
sudo apt-get install docker-compose-plugin

# 4.2 Verify
docker compose version
```



5. Install Node via nvm
```bash
# 5.1 Download and install nvm:
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash

# 5.2 in lieu of restarting the shell
\. "$HOME/.nvm/nvm.sh"

# 5.3 Download and install Node.js:
nvm install 24

# 5.4 Verify  Node.js & npm version:
node -v 
npm -v
```
