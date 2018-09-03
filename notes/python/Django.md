# Django 笔记

- 安装

    ```bash
    pip3 install Django
    ```

- 连接mysqldb报错，在python3中只支持pymysql，所以在导入MYSQLdb时会报错，需在`__init__.py`中加入两句话:  
 import pymysql  
 pymysql.install_as_MySQLdb()  

- no models 'on_delete'报错  

```python
 book = models.ForeignKey(BookInfo)
 # python3 在models中使用上面的语句使用python manage.py makemirgrations报错，下面语句解决
 book = models.ForeignKey('BookInfo', 'on_delete=models.CASCADE,')
 ```