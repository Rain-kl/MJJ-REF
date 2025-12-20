
## 修改DNS【Ubuntu22.04】

## 问题

通常我们知道，修改dns的几个途径

- /etc/resolv.conf
- /etc/netplan/01-netcfg.yaml

修改上面两个文件，一般情况下，可以解决，但是在一次使用新安装的ubuntu22.04的时候，发现，无论怎么修改，dig解析域名都是往127.0.0.53发送，哪怕在缓存中的已经生效

查看缓存中生效的配置

```bash
cat /run/systemd/resolve/resolv.conf
```

## 解决方法

需要删掉或者修改 **/etc/resolv.conf** 文件名

先修改dns配置

```bash
nano /etc/systemd/resolved.conf
```

```bash
[Resolve]
DNS=8.8.8.8 114.114.114.114
```

删除或者修改文件名

```bash
mv /etc/resolv.conf /etc/resolv.conf.bak
```

将 **/etc/systemd/resolved.conf** 新建快捷方式为 **/etc/resolv.conf**

```bash
ln -s /run/systemd/resolve/resolv.conf /etc/
```

最后重启网络

```bash
systemctl restart systemd-resolved
systemctl restart NetworkManager
```