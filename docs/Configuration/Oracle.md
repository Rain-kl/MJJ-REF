
## 开放端口网络不通的问题

**开启或清除iptables**

```css
sudo iptables -PINPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -F
sudo apt-get purge netfilter-persistent
```

甲骨文小鸡还需要在子网中的安全列表中对入口规则和出口规则进行更改，对0.0.0.0/0的所有协议放行

**停用防火墙**

```bash
sudo systemctl stop firewalld
sudo systemctl disable firewalld
```

**直接删除iptables规则**

```
sudo rm -rf /etc/iptables && reboot
```

**当然可以选择开放部分端口**

```
sudo iptables -I INPUT -s 0.0.0.0/0 -p tcp --dport 8888 -j ACCEPT
sudo iptables -I INPUT -s 0.0.0.0/0 -p tcp --dport 80 -j ACCEPT
sudo iptables -I INPUT -s 0.0.0.0/0 -p tcp --dport 443 -j ACCEPT
sudo iptables-save
sudo apt-get update
sudo apt-get install iptables-persistent -y
sudo netfilter-persistent save
sudo netfilter-persistent reload
```
