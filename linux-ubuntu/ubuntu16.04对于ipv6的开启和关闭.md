###### 1.编辑99-sysctl.conf文件

```
sudo vim /etc/sysctl.d/99-sysctl.conf
```

###### 2.复制并粘贴以下3行在文件的底部。

```
net.ipv6.conf.all.disable_ipv6 = 1#0
net.ipv6.conf.default.disable_ipv6 = 1#0
net.ipv6.conf.lo.disable_ipv6 = 1#0
```

###### 3.保存并关闭文件。 然后执行以下命令加载上述更改。

```
sudo sysctl -p
```

###### 4.现在运行以下命令。 您应该看到1，这意味着IPv6已成功禁用。

```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```