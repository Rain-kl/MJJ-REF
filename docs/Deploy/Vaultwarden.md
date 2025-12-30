
## 反代域名版

```
version: "3.9"

services:
  vaultwarden:
    image: vaultwarden/server:latest
    container_name: vaultwarden
    restart: unless-stopped
    ports:
      - "20080:80"
    volumes:
      - ./data:/data
    environment:
      WEBSOCKET_ENABLED: "true"
      SIGNUPS_ALLOWED: "false"
      ADMIN_TOKEN: "請替換成高強度隨機字串"

```

## 内置SSL版

```
version: "3.9"

services:
  vaultwarden:
    image: vaultwarden/server:latest
    container_name: vaultwarden
    restart: unless-stopped
    networks:
      - vw-net
    volumes:
      - ./data/vaultwarden:/data
    environment:
      WEBSOCKET_ENABLED: "true"
      SIGNUPS_ALLOWED: "false"
      ADMIN_TOKEN: "passwd"

  ssl-proxy:
    image: nginx:alpine
    container_name: vaultwarden-ssl
    restart: unless-stopped
    networks:
      - vw-net
    ports:
      - "20043:443"
    volumes:
      - ./data/ssl:/ssl:ro
      - ./data/nginx/nginx.conf:/etc/nginx/nginx.conf:ro

networks:
  vw-net:
    driver: bridge
```

