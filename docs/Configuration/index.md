# Debian/Ubuntu



## 网络配置

### 设置静态IP(Debian)

```
vim /etc/networking/interfaces
```

```
auto eth0
iface eth0 inet static
 address 192.168.1.10
 netmask 255.255.255.0
 gateway 192.168.1.1
 dns-nameservers 8.8.8.8
```

```
systemctl restart networking
```

systemd-resolved 服务是用来提供本机应用软件与DNS 解析服务的，其包含解析主机名称、IP 地址、域名、DNS 资源记录等，Ubuntu修改DNS就需要通过此服务来完成！

## 权限配置

### sudo无需密码

```bash
USER_NAME="${SUDO_USER:-$(whoami)}"
echo "$USER_NAME ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/99-nopasswd-$USER_NAME > /dev/null \
&& sudo chmod 0440 /etc/sudoers.d/99-nopasswd-$USER_NAME \
&& sudo visudo -cf /etc/sudoers.d/99-nopasswd-$USER_NAME
```

```bash
sudo visudo -f /etc/sudoers.d/99-nopasswd-user
your_username ALL=(ALL) NOPASSWD: ALL
```


## 个性化配置

### 设置中文

1、安装locales

```
apt install locales -y
```

2、添加配置

```bash
dpkg-reconfigure locales
```

 3、重启

