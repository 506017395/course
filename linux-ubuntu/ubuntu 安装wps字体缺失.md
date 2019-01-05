###### 1.从官网下载安装wps for Linux

```
sudo dpkg -i wps-office_10.1.0.5672~a21_amd64.deb
```

###### 2.下载缺失的字体文件，然后复制到Linux系统中的/usr/share/fonts文件夹中

`百度网盘永久链接:`https://pan.baidu.com/s/1glkTa1DJja9FMlgWyPTXRg

- 下载完成后，解压并进入目录中，继续执行

```
sudo cp * /usr/share/fonts
```

- 执行以下命令,生成字体的索引信息

```
sudo mkfontscale
```

```
sudo mkfontdir
```

- 运行fc-cache命令更新字体缓存

```
sudo fc-cache
```

`重启wps即可，字体缺失的提示不再出现`









