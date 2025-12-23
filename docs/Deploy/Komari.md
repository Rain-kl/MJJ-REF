
## 部署

```
version: '3.8'
services:
  komari:
    image: ghcr.io/komari-monitor/komari:latest
    container_name: komari
    ports:
      - "25774:25774"
    volumes:
      - ./data:/app/data
    restart: unless-stopped
```

## 三网延迟

- 河北

|联通|移动|电信|
|---|---|---|
|`he-cu-v4.ip.zstaticcdn.com:80`|`he-cm-v4.ip.zstaticcdn.com:80`|`he-ct-v4.ip.zstaticcdn.com:80`|

- 山西

|联通|移动|电信|
|---|---|---|
|`sx-cu-v4.ip.zstaticcdn.com:80`|`sx-cm-v4.ip.zstaticcdn.com:80`|`sx-ct-v4.ip.zstaticcdn.com:80`|

- 辽宁

|联通|移动|电信|
|---|---|---|
|`ln-cu-v4.ip.zstaticcdn.com:80`|`ln-cm-v4.ip.zstaticcdn.com:80`|`ln-ct-v4.ip.zstaticcdn.com:80`|

- 吉林

|联通|移动|电信|
|---|---|---|
|`jl-cu-v4.ip.zstaticcdn.com:80`|`jl-cm-v4.ip.zstaticcdn.com:80`|`jl-ct-v4.ip.zstaticcdn.com:80`|

- 黑龙江

|联通|移动|电信|
|---|---|---|
|`hl-cu-v4.ip.zstaticcdn.com:80`|`hl-cm-v4.ip.zstaticcdn.com:80`|`hl-ct-v4.ip.zstaticcdn.com:80`|

- 江苏

|联通|移动|电信|
|---|---|---|
|`js-cu-v4.ip.zstaticcdn.com:80`|`js-cm-v4.ip.zstaticcdn.com:80`|`js-ct-v4.ip.zstaticcdn.com:80`|

- 浙江

|联通|移动|电信|
|---|---|---|
|`zj-cu-v4.ip.zstaticcdn.com:80`|`zj-cm-v4.ip.zstaticcdn.com:80`|`zj-ct-v4.ip.zstaticcdn.com:80`|

- 安徽

|联通|移动|电信|
|---|---|---|
|`ah-cu-v4.ip.zstaticcdn.com:80`|`ah-cm-v4.ip.zstaticcdn.com:80`|`ah-ct-v4.ip.zstaticcdn.com:80`|

- 福建

|联通|移动|电信|
|---|---|---|
|`fj-cu-v4.ip.zstaticcdn.com:80`|`fj-cm-v4.ip.zstaticcdn.com:80`|`fj-ct-v4.ip.zstaticcdn.com:80`|

- 江西

|联通|移动|电信|
|---|---|---|
|`jx-cu-v4.ip.zstaticcdn.com:80`|`jx-cm-v4.ip.zstaticcdn.com:80`|`jx-ct-v4.ip.zstaticcdn.com:80`|

- 山东

|联通|移动|电信|
|---|---|---|
|`sd-cu-v4.ip.zstaticcdn.com:80`|`sd-cm-v4.ip.zstaticcdn.com:80`|`sd-ct-v4.ip.zstaticcdn.com:80`|

- 河南

|联通|移动|电信|
|---|---|---|
|`ha-cu-v4.ip.zstaticcdn.com:80`|`ha-cm-v4.ip.zstaticcdn.com:80`|`ha-ct-v4.ip.zstaticcdn.com:80`|

- 湖北

|联通|移动|电信|
|---|---|---|
|`hb-cu-v4.ip.zstaticcdn.com:80`|`hb-cm-v4.ip.zstaticcdn.com:80`|`hb-ct-v4.ip.zstaticcdn.com:80`|

- 湖南

|联通|移动|电信|
|---|---|---|
|`hn-cu-v4.ip.zstaticcdn.com:80`|`hn-cm-v4.ip.zstaticcdn.com:80`|`hn-ct-v4.ip.zstaticcdn.com:80`|

- 广东

|联通|移动|电信|
|---|---|---|
|`gd-cu-v4.ip.zstaticcdn.com:80`|`gd-cm-v4.ip.zstaticcdn.com:80`|`gd-ct-v4.ip.zstaticcdn.com:80`|

- 海南

|联通|移动|电信|
|---|---|---|
|`hi-cu-v4.ip.zstaticcdn.com:80`|`hi-cm-v4.ip.zstaticcdn.com:80`|`hi-ct-v4.ip.zstaticcdn.com:80`|

- 四川

|联通|移动|电信|
|---|---|---|
|`sc-cu-v4.ip.zstaticcdn.com:80`|`sc-cm-v4.ip.zstaticcdn.com:80`|`sc-ct-v4.ip.zstaticcdn.com:80`|

- 贵州

|联通|移动|电信|
|---|---|---|
|`gz-cu-v4.ip.zstaticcdn.com:80`|`gz-cm-v4.ip.zstaticcdn.com:80`|`gz-ct-v4.ip.zstaticcdn.com:80`|

- 云南

|联通|移动|电信|
|---|---|---|
|`yn-cu-v4.ip.zstaticcdn.com:80`|`yn-cm-v4.ip.zstaticcdn.com:80`|`yn-ct-v4.ip.zstaticcdn.com:80`|

- 陕西

|联通|移动|电信|
|---|---|---|
|`sn-cu-v4.ip.zstaticcdn.com:80`|`sn-cm-v4.ip.zstaticcdn.com:80`|`sn-ct-v4.ip.zstaticcdn.com:80`|

- 甘肃

|联通|移动|电信|
|---|---|---|
|`gs-cu-v4.ip.zstaticcdn.com:80`|`gs-cm-v4.ip.zstaticcdn.com:80`|`gs-ct-v4.ip.zstaticcdn.com:80`|

- 青海

|联通|移动|电信|
|---|---|---|
|`qh-cu-v4.ip.zstaticcdn.com:80`|`qh-cm-v4.ip.zstaticcdn.com:80`|`qh-ct-v4.ip.zstaticcdn.com:80`|

- 内蒙古

|联通|移动|电信|
|---|---|---|
|`nm-cu-v4.ip.zstaticcdn.com:80`|`nm-cm-v4.ip.zstaticcdn.com:80`|`nm-ct-v4.ip.zstaticcdn.com:80`|

- 广西

|联通|移动|电信|
|---|---|---|
|`gx-cu-v4.ip.zstaticcdn.com:80`|`gx-cm-v4.ip.zstaticcdn.com:80`|`gx-ct-v4.ip.zstaticcdn.com:80`|

- 西藏

|联通|移动|电信|
|---|---|---|
|`xz-cu-v4.ip.zstaticcdn.com:80`|`xz-cm-v4.ip.zstaticcdn.com:80`|`xz-ct-v4.ip.zstaticcdn.com:80`|

- 宁夏

|联通|移动|电信|
|---|---|---|
|`nx-cu-v4.ip.zstaticcdn.com:80`|`nx-cm-v4.ip.zstaticcdn.com:80`|`nx-ct-v4.ip.zstaticcdn.com:80`|

- 新疆

|联通|移动|电信|
|---|---|---|
|`xj-cu-v4.ip.zstaticcdn.com:80`|`xj-cm-v4.ip.zstaticcdn.com:80`|`xj-ct-v4.ip.zstaticcdn.com:80`|

- 北京

|联通|移动|电信|
|---|---|---|
|`bj-cu-v4.ip.zstaticcdn.com:80`|`bj-cm-v4.ip.zstaticcdn.com:80`|`bj-ct-v4.ip.zstaticcdn.com:80`|

- 天津

|联通|移动|电信|
|---|---|---|
|`tj-cu-v4.ip.zstaticcdn.com:80`|`tj-cm-v4.ip.zstaticcdn.com:80`|`tj-ct-v4.ip.zstaticcdn.com:80`|

- 上海

|联通|移动|电信|
|---|---|---|
|`sh-cu-v4.ip.zstaticcdn.com:80`|`sh-cm-v4.ip.zstaticcdn.com:80`|`sh-ct-v4.ip.zstaticcdn.com:80`|

- 重庆

|联通|移动|电信|
|---|---|---|
|`cq-cu-v4.ip.zstaticcdn.com:80`|`cq-cm-v4.ip.zstaticcdn.com:80`|`cq-ct-v4.ip.zstaticcdn.com:80`|

## 感谢

- https://zstaticcdn.com/

- https://www.nodeseek.com/post-68572-1