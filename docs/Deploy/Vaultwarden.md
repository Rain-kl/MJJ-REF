
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

```
mkdir -p ./data/nginx
mkdir -p ./data/ssl
cd ./data
openssl req -x509 -newkey rsa:4096 -sha256 -days 3650 -nodes -keyout ssl/key.pem -out ssl/cert.pem -subj "/CN=vaultwarden"

vim nginx/nginx.conf
```

```
events { worker_connections 1024; }

http {
  server {
    listen 443 ssl;
    server_name _;

    ssl_certificate     /ssl/cert.pem;
    ssl_certificate_key /ssl/key.pem;

    # WebSocket（Vaultwarden 通知）
    location /notifications/hub {
      proxy_pass http://vaultwarden:80;
      proxy_http_version 1.1;

      proxy_set_header Upgrade $http_upgrade;
      proxy_set_header Connection "upgrade";

      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto $scheme;

      proxy_read_timeout 86400;
    }

    # 普通 HTTP 请求
    location / {
      proxy_pass http://vaultwarden:80;

      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto $scheme;

      proxy_read_timeout 86400;
    }
  }
}
```


