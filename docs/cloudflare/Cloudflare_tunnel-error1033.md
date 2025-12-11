# Cloudflare tunnel Error 1033
```bash
# 1. Get token id from Cloudflare dashboard

# 2. Update token in reverse proxy 
sudo vim /etc/systemd/cloudflared.service

# 3. Ensure nameserver is correct
sudo vim /etc/resolv.conf

# 4. Restart cloudflared service
sudo systemctl daemon-reload
sudo systemctl start cloudflared
sudo systemctl status cloudflared

# Done!
```