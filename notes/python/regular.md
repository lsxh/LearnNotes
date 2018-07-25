# 正则表达式

## 常用匹配符

- 脱字符(^)  或 \A  
 ^from : 匹配任何以from作为起始的字符串  
- 美元符号($) 或 \Z  
 end$ : 匹配任何以end作为结尾的字符串
- 边界匹配 \b 和 \B  
 \b : 匹配一个单词的边界  
 \B : 单词中间匹配  
 \bthe : 任何以the开头的字符串
 \bthe\b : 匹配the
 \Bthe  : 匹配中间含有the的字符串
- 择一匹配(|):从多个匹配中选择其中一个匹配模式(at|a|the)
- . :匹配'\n'以外的任意一个字符
- \d ：数字(digit)0-9  
  \D :非数字
- \s :空白即 空格 或 Tab  
  \S :非空白
- \w :匹配单词字符 a-z A-Z 0-9 _  
  \W :匹配非单词字符  
- '*' :一个字符出现 0次 或 无数次  
- '+' :至少出现一次
- ？ ：匹配前一个字符出现 0 次 或 1次
- {m} :指定前一个字符出现 m 次  
  {m,} :指定前一个字符至少出现 m 次  
  {m,n} :指定前一个字符出现 m 到 n 次

## 创建字符集([])

- 匹配方括号内包含的一切字符  
 a[bc]d : abd acd  
 [ab][cd] : ac ad bc bd  
 [a-c5-7] : [a b c 5 6 7]

## 常用模块

### re(Regular Expression)模块

- re.I忽略大小写
- re.L表示特殊字符集\w,\W,\b,\B,\s,\S
- re.M表示多行模式
- re.S '.' 包括换行符在内的任意字符
- re.U表示特殊字符集\w,\W,\b,\B,\d,\D,\s,\D

```python
import re
"""re中的match"""
re.match(pattern，string)  # 匹配不成功返回None，匹配成功返回一个对象
result = re.match(pattern,string)  # result 为一个对象或None
result.group()  # 返回匹配的结果
re.match(pattern,string).group()  # 返回匹配到的结果
# -------pattern---------
re.match(".","abc").group()  #  结果 a
re.match("\d\d", "wq221").group()  # 结果 None
re.match("..\d\d", "wq221").group()  # 结果 22
re.match("\D\D\d\d", "wq221").group()  # 结果 wq22
re.match("\d*","1234").group()  # 结果 1234
re.match("\d*","abcd").group()  # 结果 ''
re.match("\d+","123abcd").group()  # 结果 123
re.match("\d?","abc").group()  # 结果 ''
re.match("\d?","123abc").group()  # 结果 1
# r"string" 原始字符串,加上 r 后能自动转义
re.match("\d?",r"123abc").group()
```

```python
import re
"""  
re中的compile:Compile a regular expression pattern, returning a pattern object.  
compile(pattern [, flags]) ，该函数根据包含的正则表达式的字符串创建模式对象。可以实现更有效率的匹配。在直接使用字符串表示的正则表达式进行search,match和findall操作时，python会将字符串转换为正则表达式对象。而使用compile完成一次转换之后，在每次使用模式的时候就不用重复转换。
"""
text = 'a,b,,,,c d'
reObj = re.compile('[, ]+')  # 返回一个模式对象
reObj.split(text)  # ['a', 'b', 'c', 'd']

re.split('[, ]+',text)  # ['a','b','c','d']
```

12