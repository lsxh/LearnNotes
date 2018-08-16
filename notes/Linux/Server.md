# Linux下LAMP环境的搭建

## Centos下Lamp环境的搭建

### nginx(编译安装)

- gcc 安装(编译)

 ```bash  
 yum install gcc-c++
 ```

- PCRE pcre-devel 安装  
 PCRE(Perl Compatible Regular Expressions) 是一个Perl库，包括 perl 兼容的正则表达式库。nginx 的 http 模块使用 pcre 来解析正则表达式，所以需要在 linux 上安装 pcre 库，pcre-devel 是使用 pcre 开发的一个二次开发库。nginx也需要此库。

 ```bash
 yum install -y pcre pcre-devel
 ```

- zlib 安装  
 zlib 库提供了很多种压缩和解压缩的方式， nginx 使用 zlib 对 http 包的内容进行 gzip ，所以需要在 Centos 上安装 zlib 库。

 ```bash
 yum install -y zlib zlib-devel
 ```

- OpenSSL 安装  
 OpenSSL 是一个强大的安全套接字层密码库，囊括主要的密码算法、常用的密钥和证书封装管理功能及 SSL 协议，并提供丰富的应用程序供测试或其它目的使用。  
 nginx 不仅支持 http 协议，还支持 https（即在ssl协议上传输http），所以需要在 Centos 安装 OpenSSL 库。

 ```bash
 yum install -y openssl openssl-devel
 ```

- 官网下载源码

 ```bash
 wget https://nginx.org/download/nginx-1.12.2.tar.gz
 ```  

- 解压  

 ```bash
 tar -zxvf nginx-1.12.2.tar.gz
 ```

- 进入目录

 ```bash
 cd nginx-1.12.2
 ```

- 使用默认配置,将nginx安装到/usr/local/nginx下

 ```bash
 ./configure --prefix=/usr/local/nginx
 ```

- 编译安装

 ```bash
  make && sudo make install
 ```

- 添加链接到/usr/bin 下，便于快速启动

```bash
sudo ln -s /usr/local/nginx/sbin/nginx /usr/bin/nigix
```

- nginx的进程管理

 ```bash
     sudo nginx  # 启动
     sudo nginx -s stop  # 强制停止
     sudo nginx -s quit  # 等待nginx任务处理完毕后停止
     sudo nginx -s reload  # 重载配置文件
     ps aux|grep nginx  # 查看进程是否启动
 ```

- 直接使用yum命令在线安转nginx

 ```bash
 sudo yum install nginx -y
 ```

### php

- 安装扩展和依赖库  

 ```bash
 yum install gcc bison bison-devel zlib-devel libmcrypt-devel mcrypt mhash-devel openssl-devel libxml2-devel libcurl-devel bzip2-devel readline-devel libedit-devel sqlite-devel jemalloc jemalloc-devel
 ```

- 添加用户和组

 ```bash
 groupadd www
 useradd -g www -s /sbin/nologin www
 ```

- 下载php源码  

 ```bash
 wget http://cn2.php.net/distributions/php-5.6.30.tar.gz
 ```  

- 解压  

 ```bash
 tar zvxf php-5.6.30.tar.gz
 cd php-5.6.30
 ```

- 编译参数

 ```bash
 ./configure --prefix=/usr/local/php \
--with-config-file-path=/usr/local/php/etc \
--enable-inline-optimization --disable-debug \
--disable-rpath --enable-shared --enable-opcache \
--enable-fpm --with-fpm-user=www \
--with-fpm-group=www \
--with-mysql=mysqlnd \
--with-mysqli=mysqlnd \
--with-pdo-mysql=mysqlnd \
--with-gettext \
--enable-mbstring \
--with-iconv \
--with-mcrypt \
--with-mhash \
--with-openssl \
--enable-bcmath \
--enable-soap \
--with-libxml-dir \
--enable-pcntl \
--enable-shmop \
--enable-sysvmsg \
--enable-sysvsem \
--enable-sysvshm \
--enable-sockets \
--with-curl --with-zlib \
--enable-zip \
--with-bz2 \
--with-readline
 ```

- 编译 安装

 ```bash
 make && sudo make install
 ```

- 配置文件

 ```bash
 cp php.ini-development /usr/local/php/etc/php.ini
 #php-fpm 服务
 cp /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf
 cp sapi/fpm/init.d.php-fpm /etc/init.d/php-fpm
 chmod +x /etc/init.d/php-fpm
 chkconfig --add php-fpm
 chkconfig on php-fpm
# service php-fpm start
```

### mariadb

- 安装配置  

 ```bash
 sudo yum install mariadb-server mariadb -y
 ```

- 启动服务并设置密码

 ```bash
 systemctl start mariadb.service  # 启动服务
 /usr/bin/mysql_secure_installation  # 输入命令，按提示设置密码
 ```

- 远程连接

- 开启端口

    ```bash
    iptables -A INPUT -p tcp -m tcp --dport 3306 -j ACCEPT  # 向所有ip开启3306端口
    ```
    ```bash
    iptables -A INPUT -p tcp -s 138.111.21.11 -dport 3306 -j ACCEP  # 指定ip开启
    ```
    ```bash
    service iptables save
    ```
    ```bash
    service iptables restart
    ```
    ```bash
     iptables -L -n  # 查看iptables
    ```  
    但在centos7中使用了增强版firewall，上面的命令就不好使了，得执行下面的命令  
    ```bash
    firewall-cmd –zone=public –add-port=3306/tcp –permanent  # 防火墙打开3306端口
    ```

```bash
mysql -uroot -p  # 进入mariadb，执行下面的命令
```

- 在数据库mysql 中的user表中可以看到默认是只能本地连接的，所有可以添加一个用户  
    1. 针对指定ip  
    ```mysql
    create user 'root'@'192.168.10.10' identified by 'password';  
    ```
    1. 针对全部ip  
    ```mysql
    create user 'root'@'%' identified by 'password';  
    ```
- 授权用户：  
    1. 给用户最大权限  
    ```mysql
    grant all privileges on *.* to 'root'@'%' identified by 'password';  
    ```
    1. 给部分权限(test 数据库)  
    ```mysql
    grant all privileges on test.* to 'root'@'%' identified by 'password' with grant option;  
    ```
- 刷新权限表
    ```mysql
    flush privileges;
    ```

```mysql
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%'IDENTIFIED BY '123456' WITH GRANT OPTION;  # 允许任何ip以root用户登录，123456是远程访问的密码，修改成你需要密码
flush privileges; #刷新一下
```