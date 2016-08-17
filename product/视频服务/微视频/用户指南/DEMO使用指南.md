## 1	微视频DemoAPP简介及下载
### 1.1 微视频DemoAPP简介
微视频DemoAPP，是腾讯云提供给开发者的一个测试APP，包括图片（万象优图）和视频（微视频）两个体验模块。图片体验模块包括图片的上传、暂停、删除、查询和复制等功能；视频体验模块包括视频的上传、暂停、查询和删除等功能。开发者可以使用DemoAPP体验腾讯云微视频服务，也可以在DemoAPP上注册自己的APP来验证其微视频服务是否正常开通。 

### 1.2 微视频DemoAPP下载
**Android系统**
手机扫描下面的二维码，安装图片/微视频服务安卓版的体验APP。Android SDK中自带的demo即为这个体验APP。
http://v.qcloud.com/src/css/images/android.png
**iOS系统(暂时仅支持代码包下载）**
[iOS体验APP](http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/doc/QCloudDemo-ios-v1.1.0.zip) 
将SDK中Demo重新编译或在模拟器中运行图片/微视频服务iOS版的体验APP。


## 2	微视频DemoAPP使用说明
### 2.1	注册APP
DemoAPP本身自带了官网内置的APP应用信息，可以直接使用上传、暂停、删除、查询、复制等操作来体验微视频服务。如果开发者希望验证自己的微视频服务是否开通，可以在DemoAPP上注册自己的APP，如下图所示，其中
(1). APPID为开发者在[移动服务控制台——应用管理](http://app.qcloud.com/)创建应用时获取的AppID；
(2). USERID是开发者自己业务体系中的userid，用户可以自己设置也可以使用DemoAPP自带的123456；
(3). SIGN为签名。签名是开发者客户端向其业务服务器请求得到的，验证自己的移动是否开通时，开发者可以参考[服务器端SDK](http://www.qcloud.com/doc/product/314/SDK%E4%B8%8B%E8%BD%BD)，选择熟悉的语言SDK，根据其提供的接口生成签名。

![](http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/demo-1.jpg)

填写注册信息：
![](http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/demo-2.jpg)

### 2.2	使用上传、暂停、删除、查询、复制等操作
图片服务页面如下：

![](http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/demo-3.jpg)

视频服务页面如下：

![](http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/demo-4.jpg)

### 2.3	IOS返回码说明
![](http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/demo-5.jpg)

![](http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/demo-6.jpg)

![](http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/demo-7.jpg)

### 2.4	Android返回码说明
![](http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/demo-8.jpg)

![](http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/demo-9.jpg)