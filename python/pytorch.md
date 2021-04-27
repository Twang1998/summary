### 加载模型和参数 [ref](https://blog.csdn.net/lscelory/article/details/81482586)

pytorch有两种模型保存方式：

一、保存整个神经网络的的结构信息和模型参数信息，save的对象是网络net

二、只保存神经网络的训练模型参数，save的对象是net.state_dict()

1. 直接加载模型和参数
加载别人训练好的模型：

```
保存和加载整个模型
torch.save(model_object, 'resnet.pth')
model = torch.load('resnet.pth')
```
2. 分别加载网络的结构和参数
```
# 将my_resnet模型储存为my_resnet.pth
torch.save(my_resnet.state_dict(), "my_resnet.pth")
# 加载resnet，模型存放在my_resnet.pth
my_resnet.load_state_dict(torch.load("my_resnet.pth"))
其中my_resnet是my_resnet.pth对应的网络结构。
```
3. pytorch预训练模型
1）加载预训练模型和参数
```
resnet18 = models.resnet18(pretrained=True)
这里是直接调用pytorch中的常用模型
```
```
# PyTorch中的torchvision里有很多常用的模型，可以直接调用：
import torchvision.models as models

resnet101 = models.resnet18()
alexnet = models.alexnet()
squeezenet = models.squeezenet1_0()
densenet = models.densenet_161()
```
 2）只加载模型，不加载预训练参数
```
# 导入模型结构
resnet18 = models.resnet18(pretrained=False)
# 加载预先下载好的预训练参数到resnet18
resnet18.load_state_dict(torch.load('resnet18-5c106cde.pth'))
```
3）加载部分预训练模型
```
resnet152 = models.resnet152(pretrained=True)
pretrained_dict = resnet152.state_dict()
"""加载torchvision中的预训练模型和参数后通过state_dict()方法提取参数
   也可以直接从官方model_zoo下载：
   pretrained_dict = model_zoo.load_url(model_urls['resnet152'])"""
model_dict = model.state_dict()
# 将pretrained_dict里不属于model_dict的键剔除掉
pretrained_dict = {k: v for k, v in pretrained_dict.items() if k in model_dict}
# 更新现有的model_dict
model_dict.update(pretrained_dict)
# 加载我们真正需要的state_dict
model.load_state_dict(model_dict)
```

### 换源

~~~
pip install XXX -i https://pypi.tuna.tsinghua.edu.cn/simple  清华源
pip install XXX -i http://mirrors.aliyun.com/pypi/simple --trusted-host mirrors.aliyun.com  阿里源
~~~

CUDA_VISIBLE_DEVICES=1