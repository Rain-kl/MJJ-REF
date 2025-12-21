
# 集群管理

## 内网组建

- tailscale 安装

```
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up --authkey xxx
```

- zerotier 卸载

```
sudo systemctl stop zerotier-one
sudo systemctl disable zerotier-one
sudo apt remove zerotier-one  -y 2>/dev/null || sudo yum remove zerotier-one -y
sudo rm -rf /var/lib/zerotier-one
```

## 服务器监控

- komari 探针

```
bash <(curl -sL https://raw.githubusercontent.com/komari-monitor/komari-agent/refs/heads/main/install.sh) -e xxx -t xxx

sudo journalctl -u komari-agent -f
```

卸载 agent

```
sudo systemctl stop komari-agent
sudo systemctl disable komari-agent
sudo rm /etc/systemd/system/komari-agent.service
sudo systemctl daemon-reload
sudo systemctl stop komari-agent && sudo systemctl disable komari-agent && sudo rm -f /etc/systemd/system/komari-agent.service && sudo systemctl daemon-reload && sudo rm -rf /opt/komari/agent /var/log/komari
```

## 网络通信

### SUI

```
VERSION=1.2.2 && bash <(curl -Ls https://raw.githubusercontent.com/alireza0/s-ui/$VERSION/install.sh) $VERSION
```

### Gost

```
sudo vim /etc/systemd/system/gost.service
```

```
[Unit]
Description=GO Simple Tunnel
After=network.target
Wants=network.target

[Service]
Type=simple
ExecStart=/usr/bin/gost -api "http://<admin>:<password>@0.0.0.0:50000"
Restart=always

[Install]
WantedBy=multi-user.target
```

```
sudo systemctl daemon-reload
sudo systemctl enable gost
sudo systemctl restart gost
```
