###### 1.设置root密码，可以修改成和ubuntu用户一样，方便记忆。先使用ubuntu用户ssh登录腾讯云，然后执行命令

```
sudo passwd root
```

接着输入root密码，屏幕不会像Windows那样出现星号，输完密码敲回车键就可以了，要输入两次密码

###### 2.修改ssh登录的配置，即/etc/ssh/sshd_config文件，修改为允许root登录，可以执行命令

```
sudo vim /etc/ssh/sshd_config
```

注意：这里的sudo前缀不可少，否则接下来的修改无法保存。进入vim编辑，用方向键向下滚动找到`PermitRootLogin`这项，按下insert键进入插入模式，将PermitRootLogin后面的prohibit-password改为yes，再按下Esc键，然后依次按下:键(英文冒号键)、w键和q键，最后按下回车键，保存修改成功。

###### 3.重启ssh服务使刚才的ssh配置的修改生效，执行命令

```
sudo service ssh restart
```

