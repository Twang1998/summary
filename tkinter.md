tkinter 大事记

tkinter用法及在Python2.X和Python3.X中的不同

**一.导入方式：**
　　Python2.x:

　　　　from Tkinter import *

　　Python3.x:

　　　　from tkinter import *

**二.打开文件框：**
　　Python2.X：

　　　　import tkFileDialog

　　　　filename = tkFileDialog.askopenfilename(filetypes=[("bmp格式".decode('gbk'),"bmp")])

　　　　#注意：Python2.X会有中文乱码问题，需要在"中文"后加.decode('gbk') 。Python3.X则不需要

　　　　这里可以加入属性： initialdir 设置默认初始路径。即：

　　　　FileName = tkFileDialog.askopenfilename(filetypes=[("bmp格式".decode('gbk'),"bmp")], initialdir = 'E:')

　　Python3.X：

　　　　import tkinter.filedialog

　　　　filename=tkinter.filedialog.askopenfilename(filetypes=[("bmp格式","bmp")])

**三.对话框：**
　　Python2.X：

　　　　import tkFileDialog

　　　　tkinter.MessageBox.showinfo(title='中文标题'.decode('gbk'), message='XXX') #注意:中文要加.decode('gbk')

　　Python3.X：

　　　　import tkinter.messagebox

　　　　tkinter.messagebox.showinfo(title='XXX',message='XXX')

**四.下拉列表：**
　　Python2.X：

　　　　import ttk

　　　　#注意：如果写from ttk import * 会影响Label的属性，这里可能Label会自动调用ttk里的Label？猜测而已

　　Python3.X：

　　　　from tkinter import ttk

　　　　用法一样：

　　　　　　myComboList = ['AAA','BBB',]

　　　　　　myCombox = ttk.Combobox(root, values=myComboList )

　　　　　　myCombox .pack()



mac 下 python3 应用tkinter 有点问题

通过python2解决

通过brew管理Python环境

brew install python2

brew install python3

pip 对应 python2 pip3 对应python3



Linux 下，

sudo apt-get install python3-tk

即可python3+tkinter正常使用



csv -> unicodecsv(没有newline属性)



filename重排序