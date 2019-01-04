###### 1.桌面创建一个文件：

```
touch ~/Desktop/pycharm.desktop
```

###### 2.编辑这个文件，添加以下内容（Exec是sh文件位置，icon是图标文件位置）

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Pycharm
Icon=/home/du/Documents/pycharm-community-2017.3.3/bin/pycharm.png
Exec=/home/du/Documents/pycharm-community-2017.3.3/bin/pycharm.sh
MimeType=application/x-py;
Name[en_US]=pycharm
```

###### 3.保持好上面的内容之后，给文件授权可执行

```
chmod u+x ~/Desktop/pycharm.desktop
```

###### 4.双击这个桌面文件，这个文件就从文本图标，变成了程序图标

###### 5.把这个文件复制到系统APP目录里面，这样在系统程序里面就可以找到了

```
sudo cp ~/Desktop/pycharm.desktop /usr/share/applications/
```

