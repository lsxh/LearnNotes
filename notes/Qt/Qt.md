# Qt 笔记

- Deepin下安装Qt  
  - 可以在官网上下载源码编译安装。
  - 在深度商店里安装，安装后打开Kit没有Qt版本，在终端执行  
  ```bash  
  sudo apt-get install qt5-default #或
  sudo apt-get install qt-sdk
  ```  
  重启编译器就能找到Qt5版本了

- 使用**QWebView**控件编译报错，在 .pro 文件中加入 QT += webkit webkitwidgets 提示unknown models 在终端执行
```bash
 sudo apt-get install libqt5webkit5-dev
```

- 手动编译Qt过程
  1. 生成解决方案(qmake -project)
  2. 生成Makefile问价(qmake)
  3. 生成可执行文件(make)