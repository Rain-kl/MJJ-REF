
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

