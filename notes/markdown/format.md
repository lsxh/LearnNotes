# markdowm格式

## 换行

1. 使用`<br>`

1. 末尾加两个以上空格 回车

1. 空格使用`$nbsp;`

## 插入代码

使用``````

![img](./imgs/insert.png)

## 表格

* 简单方法  

```markdown
Name | Academy | score
- | :-: | -:
Harry Potter | Gryffindor| 90
Hermione Granger | Gryffindor | 100
Draco Malfoy | Slytherin | 90
```

Name | Academy | score
- | :-: | -:
Harry Potter | Gryffindor| 90
Hermione Granger | Gryffindor | 100
Draco Malfoy | Slytherin | 90

* 原生方法  

```markdown
| Name | Academy | score |
| - | :-: | -: |
| Harry Potter | Gryffindor| 90 |
| Hermione Granger | Gryffindor | 100 |
| Draco Malfoy | Slytherin | 90 |
```

| Name | Academy | score |
| - | :-: | -: |
| Harry Potter | Gryffindor| 90 |
| Hermione Granger | Gryffindor | 100 |
| Draco Malfoy | Slytherin | 90 |

* 使用html中的table  

```html
<table>
  <tr>
    <th width=10%, bgcolor=yellow >参数</th>
    <th width=40%, bgcolor=yellow>详细解释</th>
    <th width="50%", bgcolor=yellow>备注</th>
  </tr>
  <tr>
    <td bgcolor=#eeeeee> -l </td>
    <td> use a long listing format  </td>
    <td> 以长列表方式显示（显示出文件/文件夹详细信息）  </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00>-t </td>
    <td> sort by modification time </td>
    <td> 按照修改时间排序（默认最近被修改的文件/文件夹排在最前面） </td>
  <tr>
    <td bgcolor=rgb(0,10,0)>-r </td>
    <td> reverse order while sorting </td>
    <td>  逆序排列 </td>
  </tr>
</table>
```

<table>
  <tr>
    <th width=10%, bgcolor=yellow >参数</th>
    <th width=40%, bgcolor=yellow>详细解释</th>
    <th width="50%", bgcolor=yellow>备注</th>
  </tr>
  <tr>
    <td bgcolor=#eeeeee> -l </td>
    <td> use a long listing format  </td>
    <td> 以长列表方式显示（显示出文件/文件夹详细信息）  </td>
  </tr>
  <tr>
    <td bgcolor=#00FF00>-t </td>
    <td> sort by modification time </td>
    <td> 按照修改时间排序（默认最近被修改的文件/文件夹排在最前面） </td>
  <tr>
    <td bgcolor=rgb(0,10,0)>-r </td>
    <td> reverse order while sorting </td>
    <td>  逆序排列 </td>
  </tr>
</table>