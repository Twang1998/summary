### 1.python 切片 索引 越界问题

```
>>> a ='asfaf'
>>> a[4:4]
''
>>> a[5:5]
''
>>> a[5:6]
''
>>> a[6]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
>>> a[:10000]
'asfaf'
```

1. 若切片后结果与原来相同，则新字符串所指向的物理地址就是原字符串的物理地址`(a1、a2、a3)`。
2. 若切片后结果与原来不同，则新字符串指向新的物理地址`(a5)`。
3. 若当前切片索引范围内不存在合法数值，则返回相应类型的空值`(a4)`。
1. 数组切片操作必定指向新的物理地址。
2. 若当前切片索引范围内不存在合法数值，则返回相应类型的空值`(b4)`。

### 2. 字符串

```
>>> 'aff'*3
'affaffaff'
>>> ['aff']*3
['aff', 'aff', 'aff']
>>> [1,2,3]*3
[1, 2, 3, 1, 2, 3, 1, 2, 3]
>>> [[1,2,3]]*3
[[1, 2, 3], [1, 2, 3], [1, 2, 3]]
>>> 
```

**Python join() 方法用于将序列中的元素以指定的字符连接生成一个新的字符串。**

**str.join(元组、列表、字典、字符串)** 之后生成的只能是字符串。

所以很多地方很多时候生成了元组、列表、字典后，可以用 **join()** 来转化为字符串。

```
list=['1','2','3','4','5']
print(''.join(list))
```

结果：**12345**

```
seq = {'hello':'nihao','good':2,'boy':3,'doiido':4}
print('-'.join(seq))        #字典只对键进行连接
```

结果：**hello-good-boy-doiido**

```
>>> print(''.join([1,2,3,4]))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: sequence item 0: expected str instance, int found
```

此时会报错，而当列表元素为字符串时，正常运行：

```
>>> print(','.join(['1','2','3','4']))
1,2,3,4
```



**Python strip()** 方法用于移除字符串头尾指定的字符（默认为空格）或字符序列。[参考](https://www.runoob.com/python3/python3-string-strip.html)

**注意：**该方法只能删除开头或是结尾的字符，不能删除中间部分的字符。



**.isdigit()**

**ord(ls[i]) - ord('0')**