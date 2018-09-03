- navicat在Linux(deepin)下的破解  
    先找到navicat的目录
    ```bash
    whereis navicat  # /usr/share/navicat/Navicat
    ```  
    进入到目录下，里面有一个Navicat.exe，把这个文件复制到Windows下，使用Patch-Navicat.exe破解，然后替换原来的Navicat.exe  
    替换后重新给权限  
    ```bash
    sudo chmod -R 777 Navicat.exe
    ```
    [Patch-Navicat.exe网盘下载](https://pan.baidu.com/s/1Ew2OMbUh1Pmsp0GpeLXKqA)  
