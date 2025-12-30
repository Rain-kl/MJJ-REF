
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

  bookstack:
    image: lscr.io/linuxserver/bookstack:latest
    container_name: bookstack
    depends_on:
      - mariadb
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Asia/Taipei
      # 你對外訪問的網址(很重要)：例如 http://10.0.0.5:6875 或 https://wiki.example.com
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

