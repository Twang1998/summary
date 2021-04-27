### Python读图

 https://www.jianshu.com/p/af854c53ae20 

 https://blog.csdn.net/renelian1572/article/details/78761278 

### 1.opencv

涉及函数： cv2.imread

参考网站：<a href=' https://docs.scipy.org/doc/scipy-0.18.1/reference/generated/scipy.misc.imread.html#scipy.misc.imread '> 1 </a>

### 2.PIL

涉及函数：PIL.Image.open

参考网站：<a href='  https://pillow.readthedocs.io/en/latest/reference/Image.html#PIL.Image.open  '> 1 </a>

 https://blog.csdn.net/sunmingyang1987/article/details/100418432 

 这是一个懒惰的操作；此函数标识文件，但文件保持打开状态，直到尝试处理数据（或调用load（）方法），才会从文件中读取实际图像数据。 

1. PIL image转换成array

```
     img = np.asarray(image)
```

需要注意的是，如果出现read-only错误，并不是转换的错误，一般是你读取的图片的时候，默认选择的是"r","rb"模式有关。

修正的办法:　手动修改图片的读取状态

```
  img.flags.writeable = True  # 将数组改为读写模式
```

2. p = img.load()  *# img = Image.open('x.png')* *# 可以用p[x,y]的方式取像素* 

   arr = np.array(img) *# np = numpy* 

3. array转换成image

`Image.fromarray(np.uint8(img))` 




### 3.scipy

涉及函数： `scipy.misc.imread`(*name***,** *flatten=False***,** *mode=None*)

 Read an image from a file as an array .

参考网站：<a href=' https://docs.scipy.org/doc/scipy-0.18.1/reference/generated/scipy.misc.imread.html#scipy.misc.imread '> 1 </a>

Parameters:

**name** : str or file objectThe file name or file object to be read.

**flatten** : bool, optionalIf True, flattens the color layers into a single gray-scale layer.

**mode** : str, optionalMode to convert image to, e.g. `'RGB'`. See the Notes for more details. |

Returns: 

**imread** : ndarrayThe array obtained by reading the image. |

**note:  [`imread`]uses the Python Imaging Library (PIL) to read an image.  **

 `imread` is deprecated in SciPy 1.0.0, and will be removed in 1.2.0. Use [`imageio.imread`](http://imageio.github.io/) instead. 