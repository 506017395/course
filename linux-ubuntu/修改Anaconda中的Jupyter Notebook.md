```
jupyter notebook --generate-config
```

进入当前用户目录下的 `.Jupyter`文件夹,编辑 ` jupyter_notebook_config.py`文件

找到

```
## The directory to use for notebooks and kernels. 
#c.NotebookApp.notebook_dir = ''
```

将其改为

```
## The directory to use for notebooks and kernels. 
c.NotebookApp.notebook_dir = 'E:\Jupyter'
```

其中`E:\Jupyter`为我的工作空间，你可以改成你自己的