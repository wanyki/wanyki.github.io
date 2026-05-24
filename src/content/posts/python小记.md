---
title: python小记
published: 2023-08-05 19:03:20
tags: [python]
---

### 变量

```python
age=10
print(age)#整型
print("age is %d" % age)
age = 18
name = "xiaohua"
print("我的姓名是%s, 年龄是%d" % (name, age))
password = input("请输入密码:")
print('您刚刚输入的密码是:%s' % password)
password = input("请输入密码:")
password = eval(password)#格式化为原来类型
print('您刚刚输入的密码是:%d' % password)
```

| 格式符号 |            转换            |
| :------: | :------------------------: |
|    %c    |            字符            |
|    %s    |           字符串           |
|    %d    |      有符号十进制整数      |
|    %u    |      无符号十进制整数      |
|    %o    |         八进制整数         |
|    %x    | 十六进制整数（小写字母0x） |
|    %X    | 十六进制整数（大写字母0X） |
|    %f    |           浮点数           |
|    %e    |   科学计数法（小写'e'）    |
|    %E    |   科学计数法（大写“E”）    |
|    %g    |      ％f和％e 的简写       |
|    %G    |       ％f和％E的简写       |

### 输出

```python
print("*",end=" ")	#有end=" ",输出结束没有换行
```

### for循环

```python
name="Myname"
for x in name:
    print(x)
for i in range(5):
    print(i)    
for x in range(0,10):#[0,10)
```
