###### 1.安装

key验证

```
wget http://nginx.org/keys/nginx_signing.key
```

```
sudo apt-key add nginx_signing.key
```

编辑 /etc/apt/sources.list 文件

```
sudo vim /etc/apt/sources.list
```

添加下面代码

```
deb http://nginx.org/packages/ubuntu/ xenial nginx
deb-src http://nginx.org/packages/ubuntu/ xenial nginx
```

更新源

```
sudo apt-get update
```

安装

```
sudo apt-get install nginx
```

设置开机自启动

```
systemctl enable nginx.service
```

重启nginx

```
systemctl restart nginx.service
```

查看状态

```
systemctl status nginx.service
```

检查是否安装成功

浏览器中输入服务器IP地址，可以看到`Welcome to nginx!`说明安装成功!

###### 2.nginx指定配置文件启动

```
# 不运行，仅测试配置文件
$ nginx -t configPath

# 从指定路径加载配置文件
$ nginx -c configPath

# 测试执行配置文件
$ nginx -t -c configPath
```

###### 3.nginx配置文件结构

```
main    # 全局设置
events{     # 工作模式，连接配置
    ....
}
http{       # http的配置
    ...
    upstream xxx{...}   # 负载均衡配置
    server{             # 主机设置
        ...
        location xxx{   # URL匹配
            ...
        }
    }
}
```

`ubuntu中默认配置文件: /etc/nginx/nginx.conf`

###### 4.项目静态文件配置(对接nginx)

```
- myniginx.conf配置(对应项目static的目录位置)
    #静态文件配置
    location /static {
        #别名
        alias /var/www/Python1807AXF/static/;
    }

- 关闭nginx
    pkill -9 nginx
    
- 对应配置文件启动
    nginx -c mynginx.conf
    
- 浏览器访问静态文件(确保能够访问项目的静态文件)
    http://112.74.55.3/static/base/css/reset.css
```

###### 5.uWSGI

```
- 安装(安装在虚拟环境中!!!)
    $ pip install uwsgi
    
- 项目目录中 添加 uwsgi.ini文件
    # 即是在axf目录中添加
    touch uwsgi.ini
    
- 配置uwsgi.ini文件(测试: 直接使用uwsgi，而不对接nginx)
    # uwsgi基本使用没问题，再对接上nginx，即打开socket，关闭http
    [uwsgi]
    # 使用nginx连接时 使用
    #socket=0.0.0.0:8000
    # 直接作为web服务器使用
    http=0.0.0.0:8010
    # 配置工程目录
    chdir=/var/www/axf/Python1807AXF
    # 配置项目的wsgi目录。相对于工程目录
    wsgi-file=Python1807AXF/wsgi.py
    
    #配置进程，线程信息
    processes=1
    threads=1
    enable-threads=True
    master=True
    pidfile=uwsgi.pid
    daemonize=uwsgi.log

- 使用
    # 启动
    $ uwsgi --ini uwsgi.ini  
    # 停止
    $ uwsgi --stop uwsgi.ini

# 访问测试(确保uswgi能够启动项目)
    http://112.74.55.3:8010/axf/
```

查看进程: ps -ef | grep uwsgi
关闭对应服务: pkill -9 uwsgi

###### 6.uWSGI与Nginx对接

```
- uwsig.ini文件
    [uwsgi]
    # 使用nginx连接时 使用
    socket=0.0.0.0:8000
    # 直接作为web服务器使用
    #http=127.0.0.1:8010
    # 配置工程目录
    chdir=/var/www/axf/PythonAXF
    # 配置项目的wsgi目录。相对于工程目录
    wsgi-file=PythonAXF/wsgi.py
    
    #配置进程，线程信息
    processes=1
    threads=1
    enable-threads=True
    master=True
    pidfile=uwsgi.pid
    daemonize=uwsgi.log

- mynginx.conf配置文件
    #默认请求
    location / {
        #导入了uwsgi的配置
        include /etc/nginx/uwsgi_params;
        #设定了uwsig服务器位置
        uwsgi_pass 127.0.0.1:8000;
    }
    location /2048 {
        #别名
        alias /var/www/game/2048/;
    }
    #静态文件
    location /static{
        alias /var/www/axf/Python1807AXF/static/;
    }

- 浏览器访问
    http://112.74.55.3/axf/
```

###### 7.负载均衡

一台Nginx服务器可以处理5W的并发数量，但假如有10W，20W并发如何解决？负载均衡。
负载均衡模块，通过一个调度算法来实现客户IP到后台服务器的负载平衡。

```
# 负载均衡模块
upstream atom_server{
    ip_hash;
    server 10.112.13.45:8000;
    server 12.33.243.2:8000;
    server 183.21.78.89:8000 down;
    server 19.2.34.27:8000 weight=3;
    server 17.12.12.89:8000 backup;
    fair;
}

location / {
    proxy_pass http://atom_server;
}

# weight 负载权重
# down 当前server不参数负载均衡
# backup 当其他机器全挂了或满负荷时使用此服务
# ip_hash 按每个请求的hash结果分配
# fair 按后台响应时间分(第三方)
```

` uwsgi错误1`

```
启动uwsgi时，错误: 提示没有 'uwsgi_params'

#默认请求
    location / {
        #导入了uwsgi的配置
        include /etc/nginx/uwsgi_params;
        #设定了uwsig服务器位置
        uwsgi_pass 127.0.0.1:8000;
    }
    location /2048 {
        #别名
        alias /var/www/game/2048/;
    }
    location /static{
        alias /var/www/axf/Python1807AXF/static/;
    }
```

比较常见的是uwsgi_params缺少问，这可以直接指定包含路径!

` uwsgi错误2`

```
问题描述:
    uwsgi --ini uwsgi.ini 启动项目
    但浏览器访问时，显示服务器内部错误

问题分析:
    查看运行日志: uwsgi.log
    Traceback (most recent call last):
    File "Python1807AXF/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ImportError: No module named django.core.wsgi
unable to load app 0 (mountpoint='') (callable not found or import error)

    项目运行环境是在虚拟环境中，而uwsgi并没安装到虚拟环境导致的!
    通过whereis uwsgi可以查看到!
    
解决:
    方式一: 卸载掉uwsgi，在虚拟环境中重新安装uwsgi即可
    方式二: 虚拟环境安装uwsgi，并直接使用虚拟环境中的uwsgi启动uwsgi.ini文件
```

该问题是最最常见，最最容易出问题的！！！