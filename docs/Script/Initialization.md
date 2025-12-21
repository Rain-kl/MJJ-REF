
## 安装1panel

```
bash -c "$(curl -sSL https://resource.fit2cloud.com/1panel/package/v2/quick_start.sh)"
```

## 系统设置

```
apt update -y
apt install -y sudo curl wget vim iperf3 tmux btop vnstat fd-find

timedatectl set-timezone Asia/Shanghai
```

- 添加 swap

```
wget -O swap.sh https://raw.githubusercontent.com/yuju520/Script/main/swap.sh && chmod +x swap.sh && clear && ./swap.sh
```

- 添加 zram

```
sudo apt install -y systemd-zram-generator && echo -e "[zram0]\nzram-size = ram / 2\ncompression-algorithm = lz4\nswap-priority = 100" | sudo tee /etc/systemd/zram-generator.conf >/dev/null && sudo systemctl daemon-reload && sudo systemctl restart systemd-zram-setup@zram0.service && swapon --show
```

## 网络优化

### BBR 调优

```jsx
wget <http://sh.xdmb.xyz/tcp.sh> && bash tcp.sh
```

>*ICMP不可达喵*: 
>
>一般无脑选11，BBR+FQ即可，有时候可以用13的BBR+CAKE，还有人说PIE好用，其实一般11就行了，其他容易越调越垃圾。
>
> 每个服务器都不同，这个脚本可用可不用，我一般默认开11的


## 安全设置

- 修改 ssh 端口

修改为1022 端口

```
sudo sed -i 's/^#\?Port 22.*/Port 1022/g' /etc/ssh/sshd_config
```

- 配置fail2ban

```
apt install fail2ban
vim /etc/fail2ban/jail.local
```

```
[DEFAULT]
#忽略的IP列表,不受设置限制（白名单）
ignoreip = 127.0.0.1
#允许ipv6
allowipv6 = auto
#日志修改检测机制（gamin、polling和auto这三种）
backend = systemd
#针对各服务的检查配置，如设置bantime、findtime、maxretry和全局冲突，服务优先级大于全局设置
[sshd]
#是否激活此项（true/false）
enabled = true
#过滤规则filter的名字，对应filter.d目录下的sshd.conf
filter = sshd
#ssh端口
port = ssh
#动作的相关参数
action = iptables[name=SSH, port=ssh, protocol=tcp]
#检测的系统的登陆日志文件
logpath = /var/log/secure
#屏蔽时间，单位：秒
bantime = 86400
#这个时间段内超过规定次数会被ban掉
findtime = 86400
#最大尝试次数
maxretry = 3
```

```
sudo systemctl enable fail2ban
sudo systemctl restart fail2ban
fail2ban-client status
```


### 大杂烩
#### [DDNS脚本](https://github.com/kkkgo/UE-DDNS)

```
curl -skLo ue-ddns.sh ddns.03k.org  
sh ue-ddns.sh
然后根据提示完成操作
最后设置定时任务
sudo apt-get update
sudo apt-get install cron
crontab -e
*/10 * * * * /root/(你脚本的名字)@cloudflare_IPV4_URL.sh
```


## 感谢

- [【配置优化】我拿到VPS服务器必做的那些事](https://linux.do/t/topic/160305)
- [常见脚本推荐](https://meowvps.com/blog/script/)
