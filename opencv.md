### OpenCV

#### 1.视频

```python
import numpy as np
import cv2 as cv
cap = cv.VideoCapture(0)
if not cap.isOpened():
    print("Cannot open camera")
    exit()
while True:
    # Capture frame-by-frame
    ret, frame = cap.read()
    # if frame is read correctly ret is True
    if not ret:
        print("Can't receive frame (stream end?). Exiting ...")
        break
    # Our operations on the frame come here
    gray = cv.cvtColor(frame, cv.COLOR_BGR2GRAY)
    # Display the resulting frame
    cv.imshow('frame', gray)
    if cv.waitKey(1) == ord('q'):
        break
# When everything done, release the capture
cap.release()
cv.destroyAllWindows()
```

 https://docs.opencv.org/3.4/dd/d43/tutorial_py_video_display.html (**video capture介绍**)

 You can also access some of the features of this video using **cap.get(propId)** method where propId is a number from 0 to 18. Each number denotes a property of the video (if it is applicable to that video). Full details can be seen here: [cv::VideoCapture::get()](https://docs.opencv.org/3.4/d8/dfe/classcv_1_1VideoCapture.html#aa6480e6972ef4c00d74814ec841a2939). Some of these values can be modified using **cap.set(propId, value)**. Value is the new value you want. 

 https://docs.opencv.org/3.4/d4/d15/group__videoio__flags__base.html#gaeb8dd9c89c10a5c63c139bf7c4f5704d (**get、set 参数详情**)

| get()                                                   |                                                              |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| CAP_PROP_POS_FRAMES<br />Python: cv.CAP_PROP_POS_FRAMES | 0-based index of the frame to be decoded/captured next.**1** |
| CAP_PROP_FRAME_WIDTH Python: cv.CAP_PROP_FRAME_WIDTH    | Width of the frames in the video stream.**3**                |
| CAP_PROP_FRAME_HEIGHT Python: cv.CAP_PROP_FRAME_HEIGHT  | Height of the frames in the video stream.**4**               |
| CAP_PROP_FPS Python: cv.CAP_PROP_FPS                    | Frame rate.**5**                                             |



#### 2. opencv imread

```python
cv2.imread('path').shape[0]  #height
cv2.imread('path').shape[1]  #width
```

#### 3.opencv resize

函数原型

```
`cv2.resize(src, dsize[, dst[, fx[, fy[, interpolation]]]])`
```

参数：

**src**：要resize的原图，应该是一个矩阵

**size：**希望得到图像的shape，**是一个tuple类型的数据，注意，这里是宽\*高，而我们平常img.shpae得到都是高\*宽**

**fx**，**fy** 一般不会用到

**interpolation：** 插值方法

其中插值方式有很多种：

**INTER_NEAREST**    	最近邻插值
**INTER_LINEAR**   	 双线性插值（默认设置）
**INTER_AREA ** 	 使用像素区域关系进行重采样。 它可能是图像抽取的首选方法，因为它会产生无云纹理的结果。 但是当图像缩放时，它类似于INTER_NEAREST方法。
**INTER_CUBIC**	 4x4像素邻域的双三次插值
**INTER_LANCZOS4**	8x8像素邻域的Lanczos插值

通常的，缩小使用cv.INTER_AREA，放缩使用cv.INTER_CUBIC(较慢)和cv.INTER_LINEAR(较快效果也不错)。默认情况下，所有的放缩都使用cv.INTER_LINEAR。

另外，一个小tips ，opencv 的imread 读图读出来应该是 BGR 模式 如果需要保存应该转成 RGB，下面这句代码就可以了

```python
img = img [:,:,::-1]  #所有行，所有列，所有竖（步长为-1）
```

还有 注意 opencv 的resize 后矩阵的数据类型仍然应该是uint8，但是 在skimage.transform.resize() 里 返回的是 [0,1] 的矩阵，数据类型变为了 float 。

跑模型时，经常会遇到自己数据的size和原模型的size不一致，这时候可能需要自己resize，但尤其要注意：

原来imread读出来的矩阵的数据类型是uint8，而resize后的数据类型是float，这是(0，1)范围内的数，所以如果以后要转回uint8的话肯定会丢失精度，所以我的做法是：

```python
image = (resize(image, (128, 64)) * 255).astype(np.uint8)  #resize为skimage的
```


强转为uint8
