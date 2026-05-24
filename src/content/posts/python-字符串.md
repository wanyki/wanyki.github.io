---
title: python 字符串
published: 2023-08-07 09:12:22
tags: [python]
---

### 字符串

```python
name = '峰哥'
age = 33
format_string1 = f'我的名字是 {name}, 我的年龄是 {age}'
format_string2 = f"我的名字是 {name}, 我的年龄是 {age}"
format_string3 = F'''我的名字是 {name}, 我的年龄是 {age}'''
format_string4 = F"""我的名字是 {name}, 我的年龄是 {age}"""
#这些都一样
```

```python
name = "abcdef\""
print(name)
# print:abcdef"
name = 'abcdef'
print(name[0:3]) # 取 下标0~2 的字符 [0,3)
name = 'abcdef'
print(name[2:]) # 取 下标为2开始到最后的字符
name = 'abcdef'
print(name[1:-1]) # 取 下标为1开始 到 最后第2个之间的字符
print(s[::-1])  # 从后向前，按步长为1进行取值
```

### 字符串函数方法

```python
mystr = 'hello world itcast hello world and hello world itcastcpp hello world'
print(mystr.index("t",0,len(mystr)))#与find用法相同，但如果没找到返回错误
print(mystr.find("t",0,len(mystr)))#没找到返回-1
print(mystr.replace("hello","np",mystr.count("hello")))
teststr="haha nihao a \t heihei \t woshi nide \t hao \npengyou"
re=teststr.split()
print(re)
print(re[-2])
print(mystr.split(" ",2))#前一个变量表示分割标识，后一个变量表示分割几次
#print:['hello', 'world', 'itcast hello world and hello world itcastcpp hello world']
str="_"
li=["my","name","is","jwq"]
print(str.join(li))
#print:my_name_is_jwq
```

