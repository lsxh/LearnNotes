# git安装、简单的配置(Linux)

**git安装**
apt包管理安装

```bash
sudo apt-get install git
```

yum命令编译安装

* 官网下载源码

* 解压

* 编译安装(安装前要先安装依赖包)

```bash
yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel gcc perl-ExtUtils-MakeMaker
```

```bash
make prefix=/usr/local/git all
make prefix=/usr/local/git install
```

**git简单配置(用户、邮箱的配置)**

username

```bash
git config --global user.name "lsxg"
```

email

```bash
git config --global user.email "lsxg@qq.com"
```

**配置环境变量**

vim /etc/profile

加入export 

PATH=$PATH:/usr/local/git/bin 

生效配置文件 source /etc/profile