
## 系统设置

```
apt update -y
apt install -y sudo curl wget vim iperf3
timedatectl set-timezone Asia/Shanghai
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

