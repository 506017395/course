###### 1.安装

```
sudo apt-get install terminator
```

###### 2.修改配置文件

```
cd ~/.config/terminator/ && sudo gedit config
```

###### 3.修改如下，必要时删除中文注释

```
[global_config]
  title_transmit_bg_color = "#d30102"
  focus = system
  suppress_multiple_term_dialog = True
[keybindings]
[profiles]
  [[default]]
    palette = "#2d2d2d:#f2777a:#99cc99:#ffcc66:#6699cc:#cc99cc:#66cccc:#d3d0c8:#747369:#f2777a:#99cc99:#ffcc66:#6699cc:#cc99cc:#66cccc:#f2f0ec"
    background_color = "#2D2D2D" # 背景颜色
    background_image = None  
    background_darkness = 0.85
    cursor_color = "#2D2D2D" # 光标颜色
    cursor_blink = True # 光标是否闪烁
    foreground_color = "#EEE9E9" # 文字的颜色
    use_system_font = False # 是否启用系统字体
    font = Ubuntu Mono 13  # 字体设置，后面的数字表示字体大小
    copy_on_selection = True # 选择文本时同时将数据拷贝到剪切板中
    show_titlebar = False # 不显示标题栏，也就是 terminator 中那个默认的红色的标题栏
[layouts]
  [[default]]
    [[[child1]]]
      type = Terminal
      parent = window0
      profile = default
    [[[window0]]]
      type = Window
      parent = ""
[plugins]
```

###### 4.卸载自带的终端(可以不卸载,不影响后续操作)

```
sudo apt-get remove --purge gnome-terminal
```



###### 5.在右键菜单中添加open in termintor

https://blog.csdn.net/bestBT/article/details/81221378?utm_source=blogxgwz2

###### 6.下面的都是从上面的连接里弄过来的

安装 Nautilus-actions

```
sudo add-apt-repository ppa:daniel-marynicz/filemanager-actions
```

```
sudo apt-get install filemanager-actions-nautilus-extension
```

通过上面两句话添加PPA并且安装Nautilus-actions 

使用`fma-config-tool` 启动配置界面

Command > Path

```
/usr/bin/terminator
```

Command > Parameters

```
--working-directory=%d/%b
```

将其设置为顶级菜单

设置 Runtime preferences 下面的 menu layout去勾