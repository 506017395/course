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

###### 4.

!(https://thumbnail10.baidupcs.com/thumbnail/d5c9c43aebdcd941fdc1adb8821d1b42?fid=3479087869-250528-762910013814356&time=1546567200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-YTTFJpwgGqc%2B2m01U8m0krEOZkY%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=79629003473047677&dp-callid=0&size=c256_u256&quality=90&vuk=-&ft=video)