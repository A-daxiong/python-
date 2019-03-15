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
