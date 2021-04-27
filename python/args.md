#### 0.args

```python
ap = argparse.ArgumentParser()
ap.add_argument("-database", required = True,
	help = "Path to database which contains images to be indexed")
ap.add_argument("-index", required = True,
	help = "Name of index file")
args = ap.parse_args() or args = vars(ap.parse_args())  !!!!!
args['database']   or  args.database
```

```python
print(type(args))  
print(args)

<class 'argparse.Namespace'>
Namespace(database='scene', index='fea.h5')

<class 'dict'>
{'database': 'scene', 'index': 'fea.h5'}
```

 **vars()** 函数返回对象object的属性和属性值的字典对象。 