### numpy学习 import numpy as np

#### 1.一维向量的append

```python
a=np.array([4,5,6,4])
a = np.append(a,7)
# a = np.append(a,[7]) 也行(实际上这种情况下[]几层都行)
print(a)

[4 5 6 4 7]
```



#### 2.二维矩阵的append(维度很关键)

```python
a = np.array([[1,2,3],[7,8,9],[4,5,6]])
b=np.array([4,5,6])
a = np.append(a,[b],axis=0)
print(a)

[[1 2 3]
 [7 8 9]
 [4 5 6]
 [4 5 6]]
```

```python
a = np.array([[1,2,3],[7,8,9],[4,5,6]])
b=np.array([4,5,6])
a = np.append(a,b,axis=0)
print(a)

ValueError: all the input arrays must have same number of dimensions
```

```python
a = np.array([b'M_112.jpg', b'M_113.jpg' ,b'M_114.jpg'])
a = np.append(a,[np.string_('M_113.jpg')],0)
print (a)
print (np.string_(a))
#np.string_() 字符串转为二进制序列

[b'M_112.jpg' b'M_113.jpg' b'M_114.jpg' b'M_113.jpg']
b'M_112.jpgM_113.jpgM_114.jpgM_113.jpg'
```

```python
a = np.array([b'M_112.jpg', b'M_113.jpg' ,b'M_114.jpg'])
a = np.append(a,['M_113.jpg'],0)
print (a)
print (np.string_(a))

['M_112.jpg' 'M_113.jpg' 'M_114.jpg' 'M_113.jpg']
b'M\x00\x00\x00_\x00\x00\x001\x00\x00\x001\x00\x00\x002\x00\x00\x00.\x00\x00\x00j\x00\x00\x00p\x00\x00\x00g\x00\x00\x00M\x00\x00\x00_\x00\x00\x001\x00\x00\x001\x00\x00\x003\x00\x00\x00.\x00\x00\x00j\x00\x00\x00p\x00\x00\x00g\x00\x00\x00M\x00\x00\x00_\x00\x00\x001\x00\x00\x001\x00\x00\x004\x00\x00\x00.\x00\x00\x00j\x00\x00\x00p\x00\x00\x00g\x00\x00\x00M\x00\x00\x00_\x00\x00\x001\x00\x00\x001\x00\x00\x003\x00\x00\x00.\x00\x00\x00j\x00\x00\x00p\x00\x00\x00g'
```

```python
a = np.array([b'M_112.jpg', b'M_113.jpg' ,b'M_114.jpg'])
a = np.append(a,b'M_113.jpg',0) // a = np.append(a,'M_113.jpg',0)
print (a)

ValueError: all the input arrays must have same number of dimensions
```



**字符串前u,r,b是什么意思？**

**u例**：u"我是含有中文字符组成的字符串。"

作用：后面字符串以 Unicode 格式 进行编码，一般用在中文字符串前面，防止因为源码储存格式问题，导致再次使用时出现乱码。

**r例**：r"\n\n\n\n”　　# 表示一个普通生字符串 \n\n\n\n，而不表示换行了。

作用：去掉反斜杠的转义机制。（特殊字符：即那些，反斜杠加上对应字母，表示对应的特殊含义的，比如最常见的”\n”表示换行，”\t”表示Tab等。 ）

应用：常用于正则表达式，对应着re模块。

**b例**: response = b'<h1>Hello World!</h1>'   # b' ' 表示这是一个 bytes 对象

作用：b" "前缀表示：后面字符串是bytes 类型。

用处：网络编程中，服务器和浏览器只认bytes 类型数据。如：*send 函数的参数和 recv 函数的返回值都是 bytes 类型*

**附：**

在 Python3 中，bytes 和 str 的互相转换方式是
str.encode('utf-8')
bytes.decode('utf-8')



**h5py**

 http://docs.h5py.org/en/stable/high/file.html 

#### 3.判断元素是否存在

```python
a = np.array([b'M_112.jpg', b'M_113.jpg' ,b'M_114.jpg'])
b = a == [b'M_113.jpg']
print(b)
print(b.any())  ###any()所有布尔值进行或操作，all()所有布尔值进行与操作

[False  True False]
True
```

#### 4.返回某一元素索引

np.where() 返回位置索引向量

```python
b=np.array([4,5,6,4])
a = np.where(b == 4)
print(a)

(array([0, 3], dtype=int64),)
```

```python
a = np.array([b'M_112.jpg', b'M_113.jpg' ,b'M_114.jpg'])
b = np.where(a == [b'M_113.jpg'] )
print(b)
print(a[b])

(array([1], dtype=int64),)
[b'M_113.jpg']
```

```python
a=np.array([4,5,6,4])
b = np.where(a == 7)
print(b)
print(a[b])

(array([], dtype=int64),)
[]
```

#### 5.删除二维矩阵某一行元素

```python
a = np.array([[1,2,3],[7,8,9],[4,5,6]])
a = np.delete(a,[0,1],0)
a = np.delete(a,[1],0)
a = np.delete(a,1,0)
[0,1] 表示哪几行，0表示删除行，1表示删除列，axis=0/1
```



#### 6.numpy中形状的改变

**resize与reshape**

 两个函数都是改变数组的形状，但是resize是在本身上进行操作，reshape返回的是修改之后的参数 

- reshape：有返回值，所谓有返回值，即不对原始多维数组进行修改；
- resize：无返回值，所谓无返回值，即会对原始多维数组进行修改；

 **ravel与flatten**

 flatten不会影响原始矩阵，返回的是一个副本，但是ravel是会修改数组 

```python
>>> x = np.array([[1, 2], [3, 4]])
>>> a = x.flatten()
>>> a[1] = 100
>>>> a
array([  1, 100,   3,   4])
>>> x
array([[1, 2],
       [3, 4]]) 
## flatten函数返回的是拷贝,修改返回的a之后原始的x并未改变。
## 1. .reshape可以实现维度的提升
```

```python
>>> x = np.array([[1, 2], [3, 4]])
>>> a = x.ravel()
>>> a
array([1, 2, 3, 4])
>>> a[1] = 100
>>> a
array([  1, 100,   3,   4])
>>> x
array([[  1, 100],
       [  3,   4]])  
### a是由x降维得到的，对a修改会影响到x
### ravel返回的是视图(参考数据库中的视图进行理解)，修改a之后x的内容会发生改变。不过注意a已经变为一维的了，x还是二维的，a只是将x的数据以不同的方式进行呈现。
```



~~~
np.transpose
np.newaxis   unsqueeze
hstack[:,:,::-1]
~~~

