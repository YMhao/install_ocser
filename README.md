# 一键安装配置ocsver脚本

目前只在ubuntu16.04上测试，不支持其他系统

# 运行脚本

bash install_ocserv.sh  [Your hostname or IP] [organization]

# 新建用户

sudo ocpasswd -c /etc/ocserv/ocpasswd [your usename]

# 配置系统

sudo vim /etc/sysctl.conf
```
net.ipv4.ip_forward=1
```

保存生效
```
sudo sysctl -p
```

iptable
```
sudo apt-get install iptables-persistent
sudo iptables -A INPUT -p tcp --dport 4433 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 4433 -j ACCEPT
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
```

关闭

```
sudo systemctl stop ocserv.socket
```

run
```
sudo ocserv -c /etc/ocserv/ocserv.conf
```
