# C++ 实现简单容器

##### ubuntu22 创建docker0网桥
1. 创建配置文件`/etc/netpaln/docker0.yaml`

动态获取IP
```
network:
  version: 2
  ethernets:
    eno1:
      dhcp4: false
      dhcp6: false
  bridges:
    br0:
      interfaces: [eno1]
      dhcp4: true
      parameters:
        stp: false
      dhcp6: false
```

固定IP
```
network:
  version: 2
  ethernets:
    eno1:
      dhcp4: false
      dhcp6: false
  bridges:
    br0:
      interfaces: [eno1]
      dhcp4: false
      addresses: [172.16.0.2/24]
      routes:
        - to: default
          via: 172.16.0.1
      nameservers:
        addresses: [114.114.114.114]
      parameters:
        stp: false
      dhcp6: false
```
2. 应用配置
`sudo netplan apply`

项目启动后，宿主机看不到自己的vthIP，因为没有设置
