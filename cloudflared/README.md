Cloudflared tunnel setup

This repo does not store Cloudflare tunnel credentials. Keep the credentials JSON
outside of git and mount it into the container.

Setup
1) Create a tunnel (example):
   cloudflared tunnel create appflowy

2) Copy the generated credentials JSON into this repo folder as:
   cloudflared/credentials.json

3) Update cloudflared/config.yml:
   - Set tunnel: <your-tunnel-id>
   - Keep credentials-file: /etc/cloudflared/credentials.json

4) Start the tunnel:
   docker compose -f docker-compose-cloudflared.yml up -d

Security
- Never commit credentials JSON.
- If exposed, delete/rotate the tunnel in Cloudflare and replace credentials.json.
