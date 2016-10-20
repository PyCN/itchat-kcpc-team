# itchat 项目组

itchat是微信Python API的项目，旨在提供优雅易用的微信接口。

目前有个人微信号接口[itchat][itchat]，公众号（企业号）接口[itchatmp][itchatmp]（在建）与筹备中的itchatui。

如果你希望参与这一项目，欢迎加入[kcpc的队伍][kcpc]。

项目进展与参与方式我会实时在本项目更新，不过依旧建议你加入相应的QQ群并与我联系以免出现不必要的重复工作。

## 加入方式：

你可以在这三个群里找到我。

kcpc交流群号： 477542380

itchat交流群号： 549762872

itchatmp交流群： 438747166

## 项目进展

目前项目组的主要精力在完成itchatmp，如果你对其他两个项目有兴趣，你可以与我私信交流。

如果你对tornado有足够的了解并有一定的项目经验，欢迎你来和我交流一下目前itchatmp的组织架构、交互方式与具体实现。

如果你对微信公众平台与企业号的运营有丰富的经验，欢迎你来就目前提供的接口设计与简化给出自己的意见。

如果你想要通过该项目学习http请求的各种实现，欢迎你来就研究目前接口的实现（如果追求项目页的代码量，也可以同时书写文档）。

如果你还没有确定怎么加入这个项目，但是想要加入我们一同进行开源项目的共同开发，你可以带上你的技术水平和我来做个交流，我一定会尽量提供给你一个适合的位置。

## 项目展示：

如下是一个利用该itchat接口实现的微信个人号机器人：

![robot-qr][robot-qr]

对于itchat，调用接口是一个这样的过程：

```python
import itchat

@itchat.msg_register(itchat.content.TEXT)
def text_reply(msg):
    itchat.send(msg['Text'], msg['FromUserName'])

itchat.auto_login(hotReload=True)
itchat.run()
```

类似的，企业号和公众号使用itchatmp同样简单易懂：

```python
import itchatmp

itchatmp.update_config(itchatmp.WechatConfig(
    token='yourToken',
    appId = 'yourAppId',
    appSecret = 'yourAppSecret'))

@itchatmp.msg_register(itchatmp.content.TEXT)
def text_reply(msg):
    return msg['content']

itchatmp.run(isWsgi=False)
```

[itchat]: https://github.com/littlecodersh/ItChat
[itchatmp]: https://github.com/littlecodersh/itchatmp
[kcpc]: https://github.com/orgs/Chinese-Python/teams/team-1
[robot-qr]: http://7xrip4.com1.z0.glb.clouddn.com/ItChat%2FQRCode2.jpg?imageView/2/w/400/
