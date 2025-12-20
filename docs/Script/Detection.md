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

![](assets/Detection/file-20251220163502277.png)

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

![](assets/Detection/file-20251220163502276.png)
#### [itdog](https://www.itdog.cn/)
![](assets/Detection/file-20251220163502275.png)

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

