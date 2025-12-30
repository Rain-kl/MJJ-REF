## 介绍

自托管知识库, 知识平台

## 1) 新建文件 docker-compose.yml


```
services:
  mariadb:
    image: mariadb:11
    container_name: bookstack_db
    environment:
      - MARIADB_ROOT_PASSWORD=change_me_root
      - MARIADB_DATABASE=bookstack
      - MARIADB_USER=bookstack
      - MARIADB_PASSWORD=change_me_dbpass
    volumes:
      - ./data/db:/var/lib/mysql
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "mariadb-admin", "ping", "-h", "127.0.0.1", "-pchange_me_root"]
      interval: 5s
      timeout: 3s
      retries: 30

  bookstack:
    image: lscr.io/linuxserver/bookstack:latest
    container_name: bookstack
    depends_on:
      - mariadb
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Asia/Taipei
      # 對外訪問的網址：http://10.0.0.5:6875 或 https://wiki.example.com
      - APP_URL=http://YOUR_HOST_OR_DOMAIN:6875
      # APP_KEY 下一步會生成後再填
      - APP_KEY=base64:PASTE_YOUR_APP_KEY_HERE

      - DB_HOST=mariadb
      - DB_PORT=3306
      - DB_USERNAME=bookstack
      - DB_PASSWORD=change_me_dbpass
      - DB_DATABASE=bookstack
      # 需要非同步工作（信件/ webhook 等）可用 database
      # - QUEUE_CONNECTION=database
    volumes:
      - ./data/bookstack:/config
    ports:
      - "6875:80"
    restart: unless-stopped
```

## 2) 生成 APP_KEY 并启动

  
先生成 APP_KEY（linuxserver 官方建議用容器指令產生）：

```
docker run -it --rm --entrypoint /bin/bash lscr.io/linuxserver/bookstack:latest appkey
```

## 3) 登入與初始化

打開：

- http://YOUR_HOST_OR_DOMAIN:6875

預設管理員帳號密碼（linuxserver 映像預設）：

- admin@admin.com
- password 

登入後第一件事：**改密碼**、改預設管理員信箱（安全）。