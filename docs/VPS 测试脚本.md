
此处内容仅为备份, 详细参阅[作者原文](https://meowvps.com/blog/script/*https://blog.03k.org/post/ue-ddns.html*)

### 融合脚本

#### [融合怪](https://github.com/spiritLHLS)

```
curl -L https://gitlab.com/spiritysdx/za/-/raw/main/ecs.sh -o ecs.sh && chmod +x ecs.sh && bash ecs.sh
```

最强大的一键脚本之一，顺序测试和单项测试覆盖极为广泛，基本一键完成。

#### [NodeQuality](https://www.nodeseek.com/post-297125-1)

```
bash <(curl -sL https://run.NodeQuality.com)
```

MJJ最喜爱的一键脚本，也是最方便的，买机卖机都是默认看这个作为测试结果

#### [脚本工具箱](https://kejilion.sh/index-zh-CN.html)

```
bash <(curl -sL kejilion.sh)
```

超多功能，一键开启linux管理之旅

### ip质量

#### [IP质量体检脚本](https://github.com/xykt/IPQuality)

```
bash <(curl -Ls https://IP.Check.Place)
//指定检测网卡
bash <(curl -Ls https://IP.Check.Place) -i eth0
//指定代理服务器
bash <(curl -Ls https://IP.Check.Place) -x http://username:password@proxyserver:port
bash <(curl -Ls https://IP.Check.Place) -x https://username:password@proxyserver:port
bash <(curl -Ls https://IP.Check.Place) -x socks5://username:password@socksproxy:port
```

#### [ipdata](https://ipdata.co/)

![](assets/VPS%20测试脚本/file-20251220150920887.png)

### 网络质量

#### [网络质量体检脚本](https://github.com/xykt/NetQualit)

```
bash <(curl -Ls https://Net.Check.Place)
```

#### [nexttrace](https://github.com/nxtrace/NTrace-core)

```
curl -sL nxtrace.org/nt |bash
nexttrace 1.0.0.1
```

#### [pingpe](https://ping.pe/)


#### [itdog](https://www.itdog.cn/)

#### [BGPTOOLS](https://bgp.tools/)

### 流媒体测试

#### [流媒体测试](https://github.com/lmc999/RegionRestrictionCheck)

```
bash <(curl -L -s check.unlock.media)
```

最全的流媒体测试平台，常见不常见的基本全都有

### 性能测试

#### bench

```
wget -qO- bench.sh | bash
```

#### [yabs](https://github.com/masonr/yet-another-bench-script)

```
curl -sL https://yabs.sh | bash
或者
wget -qO- yabs.sh | bash
```

### 网络调优(BBR/TCP)

#### [BBR](https://blog.ylx.me/)

```
wget http://sh.xdmb.xyz/tcp.sh && bash tcp.sh
```

#### [TCP](https://xdmb.xyz/)

```
wget sh.xdmb.xyz/d11.sh && bash d11.sh
```

一般不太用，这个参数太暴力

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

