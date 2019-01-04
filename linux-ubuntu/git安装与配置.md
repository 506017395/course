###### 1.安装

```
sudo apt-get install git
```

###### 2.检测是否安装成功

```
git --version
```

###### 3.设置GIT

后续代码是托管到GitHub中的，所以这里直接设置成GitHub的用户名和GitHub邮箱

```
git config --global user.email "506017395@qq.com"
```

```
git config --global user.name "506017395"
```

###### 4.GitHub中SSH认证

生成key,   与上面填写的邮箱与之对应

```
ssh-keygen -t rsa -C "506017395@qq.com"
```

备注: 连续三次回车，密码是设置为空

###### 5.复制.ssh目录中的id_rsa.pub文件内容，即是key(当前用户的目录下)

使用cat查看key

```
cat ~/.ssh/id_rsa.pub
```

复制打印出来的key

###### 6.在github中添加key

```
View profile and more -> settings -> SSH and GPG keys -> New SSH key
备注:
不要最后的邮箱!! 
ssh-rsa和KEY之间就一个空格，后面都不能出现空格，即是一行!
```

###### 7.检测是否添加成功

```
ssh git@github.com
```





###### 关联远程仓库

```
- 添加远程仓库并起名叫origin
    $ git remote add origin https://github.com/cxy/Git.git

- 查看现有的服务器列表
    $ git remote -v
```

删除远程仓库的关联

```
  $ git remote rm origin
```