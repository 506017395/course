###### 1.选择mysql数据库
```
use mysql;
```
###### 2.更改密码
```
update user set authentication_string=PASSWORD("你的密码") where User='root';
```
###### 3. 如果没这一行可能也会报一个错误，因此需要运行这一行
```
update user set plugin="mysql_native_password";
```
###### 4.更新所有操作
```
flush privileges;
```
###### 5.退出重进
```
quit
```
