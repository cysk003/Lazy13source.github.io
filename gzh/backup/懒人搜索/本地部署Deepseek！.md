# 本地部署Deepseek！

[**返回列表页**](/gzh/懒人搜索)

公众号【懒人搜索】备份，仅供查阅学习

懒人搜索继续分享优质资源软件

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDezKw8ZkejQKTvQJQRaOPvbBqGbwtgEBP5nxrqeFDibblbhSRoO53RWA/640?wx_fmt=png&from;=appmsg)

今天看到一句话：

> 吴军之前谈工业革命时的一个观点。
>
> 他说工业革命的受益者分成三类人：第一类是掌握核心技术的人；第二类是投资核心技术的人；第三类是率先使用核心技术的人
>
> 对应到 AI 时代，我理解，第一类人是指参与大模型研发的那批人。第二类是做 AI 相关生意的人。第三类是愿意积极使用 AI
> 技术的人。至少，我们应该让自己成为第三类人。

整个春节期间最爆火的科技资讯，莫过于Deepseek

虽然放假前小懒就安利过：

[这AI竟然能“深度思考”了？](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247494882&idx=1&sn=603993b0bceb9d3e6b74c1ca43155de8&token=1112031742&lang=zh_CN&scene=21#wechat_redirect)

不过随着爆火，官网总是会出现服务器繁忙字样

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDtd2woT8TcjwgOtcGrXzbFvLYgic4saWiaXU216tm6iaskGic7W1uuu5dlQ/640?wx_fmt=png&from;=appmsg)

今天主要分享本地部署，方便电脑配置比较好的Bro直接在自己电脑上玩Deepseek

本地版的好处在于不受限网络和官方服务器，私有部署不希望信息泄露风险的Bro

不过要体验满血版的，目前只能通过官网哈，其他平台就算是调用API的也都蒸馏版，没那么智能

文末还有其他资源补充，记得往下看~

## 本地Deepseek

小懒之前分享过搭建本地AI的教程：

[爽，三分钟接入本地大模型！](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247494252&idx=1&sn=e98edaf5ab70a21f01e99d1705691d0a&token=1112031742&lang=zh_CN&scene=21#wechat_redirect)

Ollama和AnythingLLM这两个工具的下载安装见上面文章，见上面文章！有详细教程

同样，Deepseek也在Ollama的Library里，所以可以直接拉取安装

Ollama library:

https://ollama.com/library/deepseek-r1

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDLvEqCQicRbRw44LcOxvwlxcC3OdGo7JOMrJwRXkMIhopxFSVGFO1IgA/640?wx_fmt=png&from;=appmsg)

这个B越多，代表模型越大，约吃配置和空间

小懒是4070 12G显卡，依据GPT建议安装了7B的模型：

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDgVose9RZkibHzRBUUrz6VXKR041BR8yNiaa3WciajibJofyibJ1tePA12hg/640?wx_fmt=png&from;=appmsg)

只要在CMD里执行：

`ollama pull deepseek-r1:7b`

差不多5G内容，等待即可

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDzOrV3lAh0kZJ6zGZHfGahkwAf11h17TkYxYtmpCx4iaAHLibDQZjTZ8A/640?wx_fmt=png&from;=appmsg)

安装后，我们打开AnythingLLM，方便我们可视化使用

新建工作区后，聊天设置里设置成Deepseek

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDPsqmLjOOUrickZT9HogwoRmUxrSQshl7rZ1oGresVwRM77NBtqlpLDw/640?wx_fmt=png&from;=appmsg)

记得点击下面的Update以更新

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TD6iaZta0wEicuA4oRZ9iamDicTxRFUuRU2G6Q9Ft4ibeFhVoeeVJRFXSmoQg/640?wx_fmt=png&from;=appmsg)

代理也设置一下

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDGKjSyBAkeKW57uiccHgDINAmagIbibmNQskPEaMmSbFsyNkrDvibqRafQ/640?wx_fmt=png&from;=appmsg)

记得修改后下面也有Update按钮

然后就可以愉快地玩耍啦

R1版本也是带深度思考

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDI6C5ksibcN9FfxHYGM38qAcDbluWarClb2AYrK5TkhINTHxLHWBPkag/640?wx_fmt=png&from;=appmsg)

体验上，小懒也感觉不如网页版满血爽，不过作为本地一个小平替吧

进阶玩法还能进行本地知识库搭建，关于知识库搭建，目前使用比较好的还是腾讯的IMA，这块小懒也写过文章分享了：

[这个神级软件，值得尝试！](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247494689&idx=1&sn=beec3ae024f2bb631979d8cfab0a0d64&token=1875674197&lang=zh_CN&scene=21#wechat_redirect)

就分享到这里吧，AI目前已经可以有成为生产力的能力了，再不济陪大家聊聊天啊，解决一些日常的情感问题啊，人机问题啊，或者单纯解闷，也是够用的~

最后小懒还给大家搬来一份Deepseek实战技巧，给大家放后台~

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDib3SnB9ADHuHhHbCbesibwF7zIpkVo8tSBwoBjht3ia9m0UFVhaoTLzjw/640?wx_fmt=png&from;=appmsg)

包含一些使用技巧和现成的Prompt，方便大家直接上手~

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TD4fRBapsX9muuYk4q0XgJoSiawLNoia3bE8N5zKm3hkddmgV6Zdj5KTxw/640?wx_fmt=png&from;=appmsg)

下方领取~

## 资源领取

本公众号后台回复 250206 领取资源地址

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNLUDREWLEiaz4atNIu5GsH65E1SdqC8k1gMylFg91guwoqWCY4QcABnbsh9RIz8Un8iaGSr9OPfQhXA/640?wx_fmt=png&wxfrom;=5&wx;_lazy=1&wx;_co=1)

## 题外话

小懒目前的助理AI工具依旧是Chatgpt，目前也可以免费使用推理和联网功能

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDGE7PP51bBSgDCJCI05ic998rMp9ticbq46WZaAJfibg57dwxnbAVVKFlQ/640?wx_fmt=png&from;=appmsg)

不过碍于网络和账号问题，大部分国人难以直接使用

Deepseek这段时期的爆火，也算是成功出圈——让更多人知道AI，尝试AI

甚至小红书上有父母用AI给出的回答来鼓励小孩——恕我直言，AI比大部分父母都会教学——它不会打压，它懂分寸

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDSaPvK7GDU8LDNZ1spo02s0lS8M9y1WBXMOsURkBtsHvT2bqxJlzBdg/640?wx_fmt=png&from;=appmsg)

小懒在春节挺喜欢用Deepseek的（可惜后面爆火之后，服务器一直繁忙），特别是写作能力让我感叹杀疯了——我让它帮我写一些博尔赫斯风格的句子，给它一些意象，回答的内容让我都想抄一抄了

![](https://mmbiz.qpic.cn/sz_mmbiz_jpg/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDsWQSbVB4nDibicmM3WTNXzLvAGDt1KHuRDJrKhGvHx2PLK0sOqQkiacGA/640?wx_fmt=jpeg&from;=appmsg)

春节期间还发了一条朋友圈：

![](https://mmbiz.qpic.cn/sz_mmbiz_jpg/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDN40MRYmG6Sb6yLUAM7mu5wf9clFeGbo4W3ZKJGNlRzx2NOIn8MRuUg/640?wx_fmt=jpeg&from;=appmsg)

不过小懒写推文就不用AI了（用AI汇总啥的会特别标注出来）

毕竟咱们主要分享资源软件为主，小懒这普普通通的文风，大家看习惯的也不影响资源领取~

## 懒人专属群

过完春节就来到了2月了，本月[懒人专属群](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247493087&idx=1&sn=e147d983c4441e296ee9b0ae0cdf5716&scene=21#wechat_redirect)纳新依旧，专属的优质分享也继续

欢迎需要的bro加入，也感谢老群友们安利出去~

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNJsz63cfklUia8jpvia2WCF5CChSaJTbagddbfEOv4lUhaJJuZ1DwET6L8nyECznicEkBzQeT0fmgTEA/640?wx_fmt=other&from;=appmsg&tp;=webp&wxfrom;=5&wx;_lazy=1&wx;_co=1)左拉标签公众号懒人搜索，懒人专属群介绍[](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247493087&idx=1&sn=e147d983c4441e296ee9b0ae0cdf5716&scene=21#wechat_redirect)

***公众号懒人搜索 | 手机端访问查看完整样式 | 标签可以向左拖拽，来回拖动**

  

需要的Bro添加小懒VX：

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNL2TXGXG4RpnR4Oa6BBiaMafcicNzVIMy2BZagKPXf95Tj9OCNzdtlyxqluSfibjAlOCejsg2rXxJ18A/640?wx_fmt=png&from;=appmsg&wxfrom;=5&wx;_lazy=1&wx;_co=1)

## 今日一言

> 实在，生在这乏味的世间，应该做些喜爱之事，欢度岁月才是。
>
> ——紫式部《源式物语》

![](https://mmbiz.qpic.cn/sz_mmbiz_jpg/BXJXNRRKQNJ7QOygeaLhZkXSicesXq9TDHSLzibZh1RuGSo5iaV1qY1TFrsbfPCfSDpVGicNl6z6xTIbmbicJrQOL5Q/640?wx_fmt=jpeg&from;=appmsg)

## 推荐阅读

[这AI竟然能“深度思考”了？](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247494882&idx=1&sn=603993b0bceb9d3e6b74c1ca43155de8&token=1112031742&lang=zh_CN&scene=21#wechat_redirect)

[爽，直接搞定抖音和小红书！](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247494786&idx=1&sn=4d25c89707dd34ff9633399a9eb5ef56&token=1875674197&lang=zh_CN&scene=21#wechat_redirect)

[这个神级软件，值得尝试！](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247494689&idx=1&sn=beec3ae024f2bb631979d8cfab0a0d64&token=701648839&lang=zh_CN&scene=21#wechat_redirect)

[聚合工具，实用！](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247494637&idx=1&sn=9510f0e1fad51b13fbe54b167d90604f&token=701648839&lang=zh_CN&scene=21#wechat_redirect)

[小工具，有大用！](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247494588&idx=1&sn=7e69aff75eb8a249fb9ba01ad1ddf3bf&token=1323352775&lang=zh_CN&scene=21#wechat_redirect)

  
[](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzkwNjE5NDYzOQ==&action=getalbum&album_id=3095199290177650691#wechat_redirect)[](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzkwNjE5NDYzOQ==&action=getalbum&album_id=3184635951063531523#wechat_redirect)[](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzkwNjE5NDYzOQ==&action=getalbum&album_id=3189384915092537344#wechat_redirect)[](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzkwNjE5NDYzOQ==&action=getalbum&album_id=3095199290177650691#wechat_redirect)如页面未加载，请刷新重试

***公众号懒人搜索 | 点击跳转专题 | 欢迎订阅**

* * *

> 如果你喜欢小懒的推文，希望可以把公众号文章分享出去
>
> 你的支持很重要~

![](https://mmbiz.qpic.cn/sz_mmbiz_gif/BXJXNRRKQNJ6YdLcSex3A3fRP26rl1cS3HO7V1sQUXcdiakzhwpgs1FicmG6XVSr6w6VRhSpuiagjCk1UcMxSbSdg/640?wx_fmt=gif&from;=appmsg)

  

