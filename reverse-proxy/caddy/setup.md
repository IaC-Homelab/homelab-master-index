1. Create LXC container from Debian

2. ssh in - if no internet check `/etc/resolv.conf` pointing to right DNS

3. Update, upgrade, install packages
```bash
# 1. Initial setup
apt update && apt upgrade -y

apt install vim

apt install -y --no-install-recommends \
  ca-certificates curl vim htop
  
# 2. Install Caddy
apt install -y debian-keyring debian-archive-keyring apt-transport-https

curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' \
  | gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg

curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' \
  | tee /etc/apt/sources.list.d/caddy-stable.list

apt update
apt install -y caddy

# 3. Verify installation
systemctl status caddy
``` 

4. Configure caddyfile
```bash

{
        # We're behind Cloudflare Tunnel, so let Cloudflare handle HTTPS.
        # Caddy will just speak plain HTTP on port 80.
        auto_https off
}

# Default "catch-all" site - useful as a landing page / sanity check
:80 {
        # Set this path to your site's directory.
        root * /usr/share/caddy

        # Enable the static file server.
        file_server
}

http://app.pukarsubedi.com {
        #reverse_proxy 10.0.0.126:3000
        respond "Hello from app.pukarsubedi.com via Caddy �~_~N~I" 200
}
```

4. Create a tunnel from Cloudflare to reverse proxy. Install connector.

5. `vim /etc/cloudflared/config.yml`
```bash
tunnel: HOMELAB-TUNNEL-NAME
credentials-file: /root/.cloudflared/TUNNEL_ID.json

ingress:
  - hostname: app.YOURDOMAIN.com
    service: http://127.0.0.1:80
  - hostname: media.YOURDOMAIN.com
    service: http://127.0.0.1:80
  - service: http_status:404
```

7. vim /etc/systemd/system/cloudflared.service
```bash
# Ensure --config option is there and poiting to /etc/cloudflared/config.yml
ExecStart=/usr/bin/cloudflared --no-autoupdate --config /etc/cloudflared/config.yml tunnel run --token

# Restart
systemctl daemon-reload
systemctl enable cloudflared
systemctl restart cloudflared
systemctl status cloudflared
systemctl restart caddy
```

8. Verify at URL