###### 1.下载编译好的包解压

- 移动到 `/usr/local `目录下

```
sudo mv **** /usr/local
```

`**** `是nodejs文件夹

###### 2.设置环境变量

- 编辑 `/etc/profile`

```
sudo vi /etc/profile
```

- 在最后添加

```
# jdk 1.8
export JAVA_HOME=/usr/local/jdk1.8.0_191
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib

# node.js
export NODE_HOME=/usr/local/nodejs
export NODE_PATH=$NODE_HOME/node_global
export PATH=.:$JAVA_HOME/bin:$PATH:$NODE_HOME/bin:$NODE_PATH/bin
```

###### 3.测试是否配置成功

```
node -v
```

```
npm -v
```

上述两条命令会分别打印 node和npm的版本

###### 4.设置全局安装路径及全局缓存路径

```
sudo mkdir /usr/local/nodejs/node_global /usr/local/nodejs/node_cache
```

```
npm config set prefix "/usr/local/nodejs/node_global"
```

```
npm config set cache "/usr/local/nodejs/node_cache"
```

