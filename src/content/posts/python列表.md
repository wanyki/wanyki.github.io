---
title: 列表
published: 2023-08-07 15:44:26
tags: [python]
---

### 列表

#### append

##### 通过append可以向列表添加元素

```python
A = ['xiaoWang','xiaoZhang','xiaoHua']

print("-----添加之前，列表A的数据-----")
for temp_name in A:
    print(temp_name)

#提示、并添加元素
temp = input('请输入要添加的学生姓名:')
A.append(temp)#temp作为一个加入到A

print("-----添加之后，列表A的数据-----")
for temp_name in A:
    print(temp_name)
```

#### extend

##### 通过extend可以将另一个集合中的元素逐一添加到列表中

```python
A.extend(B)#B里的内容分别作为一个加入到A
print(A)
```

#### 遍历方式

```python
for temp_name in A:
    print(temp_name)
for name in range(0,2):
    print(A[name])
```

#### insert

##### insert(index, object) 在指定位置index前插入元素object

```python
a = [0, 1, 2]
a.insert(1, 3)
print(a)
print:[0, 3, 1, 2]
```

#### in,not in

```python
A=[1,2,3,4,5]
B=[6,7,8,9,0]
if 99 in A:
    print("yes")
else:
    print("no")
```

#### index, count

index和count与字符串中的用法相同

```python
>>> a = ['a', 'b', 'c', 'a', 'b']
>>> a.index('a', 1, 3) # 注意是左闭右开区间
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: 'a' is not in list
>>> a.index('a', 1, 4)
3
>>> a.count('b')
2
>>> a.count('d')
0
```

#### 删除元素("删"del, pop, remove)

```python
del movie_name[2]：根据下标进行删除
movie_name.pop()：删除最后一个元素
movie_name.remove('指环王')：根据元素的值进行删除
```

#### 排序(sort, reverse)

sort方法是将list按特定顺序重新排列，默认为由小到大，参数reverse=True可改为倒序，由大到小。

reverse方法是将list逆置。

```python
>>> a = [1, 4, 2, 3]
>>> a
[1, 4, 2, 3]
>>> a.reverse()
>>> a
[3, 2, 4, 1]
>>> a.sort()
>>> a
[1, 2, 3, 4]
>>> a.sort(reverse=True)
>>> a
[4, 3, 2, 1]
```

