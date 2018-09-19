# wechat_analysis_itchat
WeChat analysis by itchat

我的博客地址：https://blog.csdn.net/m511655654/article/details/82758059

通过调用第三方库itchat，基于python3.6实现微信朋友圈性别、地区、个性签名、头像四个维度的分析。

1、准备工作
1.1 环境要求
WIN10
python3.6
pycharm编译器

1.2 第三方库要求
itchat：itchat是一个开源的微信个人号接口
jieba：结巴分词的 Python 版本，对文本信息进行分词处理。 
matplotlib： Python 中图表绘制模块，在本文中用以绘制柱形图和饼图 
snownlp：一个 Python 中的中文分词模块，在本文中用以对文本信息进行情感判断。 
PIL： Python 中的图像处理模块，在本文中用以对图片进行处理。 
numpy： Python中 的数值计算模块，在本文中配合 wordcloud 模块使用。 
wordcloud： Python 中的词云模块，在本文中用以绘制词云图片。 
TencentYoutuyun：腾讯优图提供的 Python 版本 SDK ，在本文中用以识别人脸及提取图片标签信息。 
安装问题①：

上述几个第三方库均可通过pip install方式安装，除了TencentYoutuyun

通过普通的pip方法无法实现安装，会报错

pip install TencentYoutuyun
解决方法①：

先去github下载官方sdk的zip压缩包至某目录下，如E:\Project\test\Python_sdk-master.zip

https://github.com/Tencent-YouTu/Python_sdk

打开命令行，定位到下载目录下，再进行pip安装，至安装成功

e:
cd Project\test
pip install Python_sdk-master.zip
安装问题②：

PIL目前只支持python2.x版本，不支持python3.x。

解决方法②：

Pillow是PIL的一个派生分支，但如今已经发展成为比PIL本身更具活力的图像处理库。

Pillow的Github主页：https://github.com/python-pillow/Pillow
Pillow的文档(对应版本v3.0.0)：https://pillow.readthedocs.org/en/latest/handbook/index.html
Pillow的文档中文翻译(对应版本v2.4.0)：http://pillow-cn.readthedocs.org/en/latest/

Python 3.x 安装Pillow

给Python安装Pillow非常简单，使用pip或easy_install只要一行代码即可。

在命令行使用pip安装：

pip install Pillow
或在命令行使用easy_install安装： 

easy_install Pillow
安装完成后，使用from PIL import Image就引用使用库了。比如：
 

from PIL import Image
im = Image.open("bride.jpg")
im.rotate(45).show()

2、好友性别
获取好友性别信息，统计男、女、未知的数量，计算比例并制作饼图可视化。

3、好友地区
获取好友的地区信息，保存至本地'location.csv'，再统计各地区的好友数量存至'location_analysis.xls’。

使用BDP报表工具https://me.bdp.cn/home.html分析地区信息

4、好友头像
调用腾讯优图的人脸识别接口DetectFace和图片标签识别分类接口imagetag，再生成使用人脸头像的饼图和头像标签的词云。

5、好友个性签名
先获取好友签名信息，再对文本做预处理，调用SnowNLP接口对文本做情感分析。

