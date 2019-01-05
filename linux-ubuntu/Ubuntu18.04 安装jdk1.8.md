###### 1.先到官网下载压缩包

###### 2.解压

```
tar -zxvf jdk-8u171-linux-x64.tar.gz
```

###### 3.移动到制定目录

将文件从下载目录 挪到`/usr/local`下

```
sudo mv jdk1.8.0_171  /usr/local/jdk1.8
```

###### 4.设置环境变量

```
sudo vim /etc/profile 
```

在文件末尾加入

```
export JAVA_HOME=/usr/local/jdk1.8
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=.:${JAVA_HOME}/bin:$PATH
```

###### 5.使配置生效

```
source /etc/profile 
```

###### 6.检查是否安装成功

```
java -version
```

