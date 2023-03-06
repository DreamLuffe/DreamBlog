---
title: "(全网最详细)Mysql下载安装和配置方法(看了必成功)"
subtitle: ""
date: 2023-03-06T10:27:18+08:00
# draft: true
author: "DreamLuffe"
authorLink: "https://github.com/DreamLuffe"
authorEmail: ""
description: ""
keywords: ""
license: ""
comment: false
weight: 0

tags:
- Mysql
categories:
- 技术

---


## Mysql下载
#### MySQL官网下载地址：[MySQL](https://dev.mysql.com/downloads/)  
![在这里插入图片描述](https://img-blog.csdnimg.cn/0159921b5377462b9bd77ebf15528acd.png)
#### 点击进行下载
![在这里插入图片描述](https://img-blog.csdnimg.cn/2ea67446f65b4b8980f9ca0e40b668e8.png)
### 解压到你想要安装的目录
* 新建my.ini文件复制以下内容粘贴进去
* 修改basedir=<font color="#dd0000">安装的目录</font>，datadir=<font color="#dd0000">安装的目录</font>\data
```pach
[mysqld]
#设置3306端口
port=3306
#设置mysql的安装目录
basedir=
#设置mysql数据库的数据的存放目录
datadir=\data
#允许最大连接数
max_connections=200
#允许连接失败的次数。这是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=10
#服务端使用的字符集默认为UTF8
character-set-server=utf8
#创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
#默认使用“mysql_native_password”插件认证
default_authentication_plugin=mysql_native_password
```
我的安装目录：D:\variable\MySQL\mysql-8.0.32-winx64
![在这里插入图片描述](https://img-blog.csdnimg.cn/5437f8d388d3411080c057a597cf1338.png)
配置环境变量
![在这里插入图片描述](https://img-blog.csdnimg.cn/580bcc150b8746bc86cc35dbce0d79ed.png)


使用管理员打开cmd
输入mysqld --initialize-insecure --user=mysql,初始化数据库，并设置默认root为空，初始化完成后，在mysql根目录中会自动生成data文件
```bash
mysqld --initialize-insecure --user=mysql
```
再输入mysqld -install,为windows安装mysql服务，默认服务名为mysql
出现service successfully installed.表示配置完成
```bash
mysqld -install
```
启动数据库net start mysql,
```bash
net start mysql
启动服务
启动服务成功
```
输入mysql -u root -p ,不用输入密码直接回车
出现mysql>配置完成
![在这里插入图片描述](https://img-blog.csdnimg.cn/c82c5cbcb61e4be18391dc1d2fc9d240.png)
输入(alter user user() identified by "密码";)
```bash
alter user user() identified by "密码";
```
mysql退出 mysql>quit;
输入net stop mysql关闭数据库
