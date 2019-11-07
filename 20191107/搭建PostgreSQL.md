# 搭建PostgreSQL

---

### Lunix系统下搭建(推荐)

##### 准备

* 参考：[Linux下PostgreSQL数据库安装、配置与日常服务管理](https://www.linuxidc.com/Linux/2017-11/148411.htm)  
* 环境：Lunix Centos 7
* 数据库：PostgreSQL 12
    - [下载地址](https://www.postgresql.org/download/linux/redhat/)

##### Yum仓库安装

* 注册仓库

```
yum install https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm
```
* 下载安装包
    - 默认安装地址`/usr/pgsql-12`
    - 会生成Lunix`postgres`用户，默认没有密码
```
yum install postgresql12-server postgresql12-plpython postgresql12-libs postgresql12-devel postgresql12-contrib postgresql12
```
* 初始化数据库并配置自动启动
    - 默认数据库实例地址`/var/lib/pgsql/12/data`
```
/usr/pgsql-12/bin/postgresql-12-setup initdb
systemctl enable postgresql-12
systemctl start postgresql-12
```

* 设置系统变量
    - 编辑`vim /etc/profile`，文件内添加以下指令
    ```
    #export PGDATA=/var/lib/pgsql/12/data
    export PGHOME=/usr/pgsql-12/
    export PATH=$PGHOME/bin:$PATH
    ```
    - 使用`source /etc/profile`生效变量
    
* `-bash-4.2$`的解决办法
```
cp /etc/skel/.bashrc /var/lib/pgsql
```


### Windows系统下搭建




