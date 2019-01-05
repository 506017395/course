##### 1.查看node版本

```
node -v
```

###### 2.注册cnpm代替npm

```
npm install cnpm -g --registry=https://registry.npm.taobao.org
```

`常见问题：如果成功cnpm但无法使用命令  则是环境Path变量问题 手动添加，如";C:\Program Files\nodejs\node_modules"`

###### 3.安装vue脚手架vue-cli

```
cnpm install -g vue-cli
```

- 查看vue版本

```
vue -V
```

###### 4.安装webpack支持

```
cnpm install webpack -g
```

###### 5.初始化项目

- CD定位到项目位置

```
vue init webpack my-project
```

- 安装依赖项

```
cnpm install
```

- 启动项目

```
cnpm run dev
```

