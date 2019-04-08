## **python的原生字符串不能以反斜杠结尾的问题**

```  
print(r'C:\')  # 错误
print(r'C:\\') # 正确   建议写法print(r'C:''\\')
```

### 布尔类型是整型的子类

```
# exp1
mixed_list = [False, 1.0, "some_string", 3, True, [], False]
boolNum =0
intNum = 0
floatNum = 0
for i in mixed_list:
    if isinstance(i,int):
        intNum += 1
    elif isinstance(i,float):
        floatNum += 1
    elif isinstance(i,bool):
        boolNum += 1
    else:
        pass
print('布尔类型的个数为{}\n整数类型的个数为{}\n浮点数字个数{}'.format(boolNum,intNum,floatNum))

#exp2
someBool = True
print('*'*someBool)
print('-------------')
someBool = False
print('*'*someBool)

print(True == 1 == 1.0 and False == 0 == 0.0)
```

### 相同的值计算出来的哈希值一定相同，哈希值相同原始值不一定相同

```
another_dict = {}
another_dict[True] = "JavaScript"
another_dict[1] = "Ruby"
another_dict[1.0] = "Python"
print(another_dict)
```

### 易犯错误

```
some_list = [1, 2, 3]
some_dict = {
  "key_1": 1,
  "key_2": 2,
  "key_3": 3
}
some_list = some_list.append(4)
some_dict = some_dict.update({"key_4": 4})
print(some_list)
print(some_dict)
'''
大多数修改序列/映射对象的方法, 比如 list.append, dict.update, list.sort 等等. 都是原地修改对象并返回 None. 这样做的理由是, 如果操作可以原地完成, 就可以避免创建对象的副本来提高性能.
'''
```

烧脑的一个

```
a, b = a[b] = {}, 5
print(a)   # 打印个啥
```


##类属性继承的变量问题
class A:
    x = 1
class B(A):
    pass
class C(A):
    pass

B.x = 100
print(A.x,B.x,C.x)
print(id(A.x),id(B.x),id(C.x))

A.x = 1000
print(A.x,B.x,C.x)
print(id(A.x),id(B.x),id(C.x))

output:
1 100 1
1775004688 1775007856 1775004688
1000 100 1000
2267942203088 1775007856 2267942203088


###执行时机的问题
list_2 = [1, 2, 3, 4]
print(list(enumerate(list_2)))
for idx, item in enumerate(list_2):
    list_2.remove(item)
    # print(list(enumerate(list_2)))
print(list_2)

#s输出为：
[2,4]

###不能在循环中删除序列的值
a = [11,22,33,44,55,66,77,88]
for i in a:
    print(i)
    if i == 33 or i == 44:
        a.remove(i)
print('----------')
print(a)

#结果输出为：
11
22
33
55
66
77
88
----------
[11, 22, 44, 55, 66, 77, 88]

##原因是：在删除掉元素后，整个列表变了，导致删除的两个元素挨着的话第二个元素不会被删除


