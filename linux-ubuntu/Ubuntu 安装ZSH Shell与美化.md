###### 1.安装ZSH Shell

```
sudo apt-get update
```

```
sudo apt-get install zsh
```

###### 2.查看其版本

```
zsh --version
```

###### 3.设置ZSH为默认Shell

使用以下命令找出 ZSH Shell 的路径

```
whereis zsh
```

将 ZSH 设置为当前登录用户的默认 Shell

```
sudo usermod -s /usr/bin/zsh $(whoami)
```

` 重启计算机`

在计算机重启后打开终端会出现提示,按键盘数字键 `2`，ZSH 会使用推荐的设置创建一个新的 ~/.zshrc 配置文件

###### 4.为ZSH安装Powerline和Powerline字体

```
sudo apt-get install powerline fonts-powerline
```

###### 5.安装ZSH Powerlevel9k美化主题

```
sudo apt-get install zsh-theme-powerlevel9k
```

装好之后执行以下命令在 Ubuntu 上启用 Powerlevel9k ZSH 主题

```
echo "source /usr/share/powerlevel9k/powerlevel9k.zsh-theme" >> ~/.zshrc
```

现在打开一个新的终端窗口，您就可以看到 ZSH Shell 的新外观了

