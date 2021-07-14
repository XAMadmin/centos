#### IT运维技术支持

##### 1. centos安装及配置

[vmware安装centos教程](https://blog.csdn.net/babyxue/article/details/80970526)

+ ***\*配置ip地址等信息在/etc/sysconfig/network-scripts/ifcfg-ens33文件里做如下配置：\****

```python
vi   /etc/sysconfig/network-scripts/ifcfg-ens33
修改内容：
TYPE="Ethernet"   # 网络类型为以太网
BOOTPROTO="static"  # 手动分配ip
NAME="ens33"  # 网卡设备名，设备名一定要跟文件名一致
DEVICE="ens33"  # 网卡设备名，设备名一定要跟文件名一致
ONBOOT="yes"  # 该网卡是否随网络服务启动
IPADDR=""  # 该网卡ip地址就是你要配置的固定IP，如果你要用xshell等工具连接，220这个网段最好和你自己的电脑网段一致，否则有可能用xshell连接失败
GATEWAY=""   # 网关
NETMASK="255.255.255.0"   # 子网掩码
DNS1="8.8.8.8"    # DNS，8.8.8.8为Google提供的免费DNS服务器的IP地址
```

+ **\*在/etc/sysconfig/network文件里增加如下配置\***
```python
命令：
vi /etc/sysconfig/network
修改：
NETWORKING=yes # 网络是否工作，此处一定不能为no
```

+ ***\**\*配置公共DNS服务(可选)\*\**\***

```python
在/etc/resolv.conf文件里增加如下配置
nameserver 8.8.8.8
```

+ ***关闭防火墙***

```shell
systemctl stop firewalld # 临时关闭防火墙
systemctl disable firewalld # 禁止开机启动
```

+ ***重启服务***

```python
service network restart
```

##### 2. SQL Server安装

[Centos7安装SQL Server教程](https://www.pianshen.com/article/72531071885/)

##### 3. docker安装

```
curl -fsSL https://get.docker.com | bash -s docker --mirror aliyun
启动docker：
sudo systemctl start docker
```

##### 4. centos开机自启

[开机自启脚本教程](https://www.cnblogs.com/longchengruoxi/p/11451062.html)

```shell
这里介绍常用脚本：
1、因为在centos7中/etc/rc.d/rc.local的权限被降低了，所以需要赋予其可执行权
chmod +x /etc/rc.d/rc.local
2、赋予脚本可执行权限
假设/usr/local/script/autostart.sh是你的脚本路径，给予执行权限
chmod +x /usr/local/script/autostart.sh
3、打开/etc/rc.d/rc.local文件，在末尾增加如下内容
/usr/local/script/autostart.sh
```



