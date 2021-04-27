### 1.删除

[ref](https://blog.csdn.net/jhr112/article/details/115631246)

> 本文介绍的方法中，均有`inplace`参数，其默认值都为`False`,表示返回新数据框；设置为`True`表示替换原数据框，返回None

~~~
# 删除单行
df.drop('a')
# 删除多行
df.drop(['a', 'c'])
# 删除指定位置行
df.drop(df.index[[1,3]])
~~~

~~~
df = pd.read_csv('UGCTrain_dmos.csv.bkup')
a = np.where(df['file_ref'] == df['file_dis'])  ##tuple
df = df.drop(df.index[a[0]])
# or df = df.drop(df.index[a])
~~~

根据`列名`删除目标列，同时需要设置`axis=1`或者`columns`。

~~~
# 删除一列
df.drop('x',axis=1)
# 删除多列
df.drop(['x','z'],axis=1)
# 删除指定位置列
df.drop(df.columns[[0,1]],axis=1)
~~~

删除列也可以用关键字`del`实现，每次只能删除一列，且删除列后，原数据发生改变。

```python
del df['x']
df
```

同时删除行和列，需要为行使用`index`参数，为列使用`columns`参数。

```python
df.drop(index=['a','b'],columns='y')
```

### 2. save

~~~
data.to_csv('data.csv',index=False, header=False)
~~~

