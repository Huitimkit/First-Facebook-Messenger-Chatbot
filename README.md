# First-Facebook-Messenger-Chatbot

![](https://github.com/Huitimkit/First-Facebook-Messenger-Chatbot/blob/master/img/log.jpg?raw=true)

Messenger是Facebook推出的即时通讯工具，用户只需打开Messenger就可以与各种各样的chatbot交互，而无需下载和安装相应的app。这么一说，是不是觉得和微信的小程序很相似。
但是两者存在的形式大不相同，chatbot，顾名思义，就是通过聊天的形式进行引导交互，而不是通过传统的用户自主浏览等操作。本文主要简单介绍如何快速的搭建一个傻瓜聊天机器人（呵呵，实际只会重复你发送的消息）


## 搭建步骤

### 1.注册Facebook开发者
登录自己的Facebook账号，转到Facebook开发者平台（[https://developers.facebook.com/](https://developers.facebook.com/))，点击右上角的**开始**按钮，按照提示操作，就可以注册成为Facebook的开发者了。

![](https://github.com/Huitimkit/First-Facebook-Messenger-Chatbot/blob/master/img/register.jpg?raw=true)

### 2.创建新的粉丝页
如果你当前没有粉丝页，你可以通过以下链接（[https://www.facebook.com/pages/create/?ref_type=logout_gear](https://www.facebook.com/pages/create/?ref_type=logout_gear)）前往创建自己的一个粉丝页。根据类别创建相应的粉丝页。

![](https://github.com/Huitimkit/First-Facebook-Messenger-Chatbot/blob/master/img/build.jpg?raw=true)


### 3.添加新的应用
返回到Facebook开发者平台，鼠标移动到右上角的**我的应用**，选择下拉菜单的**添加新的应用**，在弹出框中填入相应的应用名称，点击提交后，页面会跳转到应用的管理页面。

![](https://github.com/Huitimkit/First-Facebook-Messenger-Chatbot/blob/master/img/app.jpg?raw=true)


### 4.获取访问口令

在上一步最后跳转到的管理页面当中，点击messenger的设置，跳转至messenger设置页，在生成口令一栏，选择你自己第二步创建的粉丝页，系统就会自动生成一串访问口令，复制这段口令，需要在验证Webhook时用到。

![](https://github.com/Huitimkit/First-Facebook-Messenger-Chatbot/blob/master/img/set.jpg?raw=true)


### 5.设置和启动Webhook Server
我们可以通过Facebook官方提供的代码，在glitch平台快速搭建一个Webhook Server。

点击[https://glitch.com/edit/#!/messenger-bot](https://glitch.com/edit/#!/messenger-bot)进行编辑，

在.env文件中，把上一步的获得访问口令填到**PAGE_ACCESS_TOKEN**中，**VERIFY_TOKEN**随便填，记住等一下用。

![](https://github.com/Huitimkit/First-Facebook-Messenger-Chatbot/blob/master/img/glitch.jpg?raw=true)

点击顶部的**Show Live**启动服务器，浏览器会打开一个新窗口，显示如下，复制当前链接	

![](https://github.com/Huitimkit/First-Facebook-Messenger-Chatbot/blob/master/img/glitch02.jpg?raw=true)



### 6.验证Webhook
返回到第四步的应用管理页，在webhook一栏中，点击**设置Webhooks**

![](https://github.com/Huitimkit/First-Facebook-Messenger-Chatbot/blob/master/img/webhook.jpg?raw=true)

在回调网址中，填入第五步的最后复制的链接并加上**/webhook**，例如：https://example.com/webhook。

在验证口令一栏中输入.env中的VERIFY_TOKEN的值，并且勾选**message**和**messaging——postbacks**，点击**验证并保存**，验证填写信息是否有误。无误则自动关闭窗口并在Webhook一栏的右边显示完成，同时操作订阅刚刚创建的粉丝页。

### 7.测试聊天机器人

如果以上都没有问题，就可以回到粉丝页和机器人开始聊天了，当然现在他非常傻，就会回传你发给他的信息。












