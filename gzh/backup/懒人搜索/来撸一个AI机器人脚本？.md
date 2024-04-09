# 来撸一个AI机器人脚本？

[**返回列表页**](/gzh/懒人搜索)

小懒自动备份，仅供查阅学习

懒人搜索继续分享优质资源软件

最近Chatgpt开放了3.5的游客免登录使用，不过网络问题估计还是劝退很多Bro

![](https://mmbiz.qpic.cn/sz_mmbiz_jpg/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4VyM4WDiaNiczLAjE2N6a0IibpZBpqU0FQDHalc3iatzQUspdjcpNhdsUWg/640?wx_fmt=jpeg&from;=appmsg)

小懒AI绘画

随着国内大模型的迭代，现在国产AI智能程度也是到了够用的程度了

比如[之前分享的Kimi](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247489550&idx=1&sn=3bd47498843645d958ed318b88b35363&chksm=c0ed63aef79aeab870e0c95aa980ca21b2b567f59bb725809f2a63a5db921e718f28c0045fab&token=408107735&lang=zh_CN&scene=21#wechat_redirect)，早上还有群友反馈高效了他的工作

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4dlsxkJQcAZTBeol5x0nuHq4wTVyPeqqrOymvrG0hSibv3hvxUInDWLw/640?wx_fmt=png&from;=appmsg)

今天来又要来分享一个国产大模型，不过要教给大家的是利用其Token二次开发成自己的专属AI

不会代码的小懒也会给出软件，耐心往下看！

## 背景

小懒以前给大家做过[公众号导读系列](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzkwNjE5NDYzOQ==&action=getalbum&album_id=3199610982143131652#wechat_redirect)，因为黑粉举报怒而停更

而后又在懒人找资源-
手册里，[每天用脚本自动更新和备份一些公众号推文](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247489600&idx=1&sn=2ee52c65231cf2f376acf9f5a9486f86&chksm=c0ed63e0f79aeaf6f13c97e876d0f0119212be3c5d646510009efbfdd439b17fa7cda0eb7181&token=408107735&lang=zh_CN&scene=21#wechat_redirect)

![](https://mmbiz.qpic.cn/sz_mmbiz_jpg/BXJXNRRKQNJzm6ZgMMBuEMnkIFicASnlfiaoynVicXmUJWWp1wX5ICibdVMncVH9EzLFWMp4XdE2RGcGqga0X7dIpw/640?wxfrom=12&tp;=wxpic&wx;_fmt=jpeg)

之前的导读用群友分享的接口进行文章解读，前两天测试了这个Deekseek接口对文章自动解读，效果还可以

加上国内的大模型一般都经过审查了，后续打算用它继续更新导读系列

今天先分享用法~

![](https://mmbiz.qpic.cn/sz_mmbiz_jpg/RDnsI9KkLHWrutAk79HkHrq404T3lX4urQiaF9yxCwhU9DNbOJadlHaJNefjLiatHvGAiaxGGGWlKNtCElpS2q5ibg/640?wxfrom=12&tp;=wxpic&wx;_fmt=jpeg)小懒AI绘画

## Deekseek 大模型

网址：https://www.deepseek.com/

这个Deekseek支持通用对话，还支持开放平台

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4V438lWGOJYBGpMDuicI6YiaXOzYfXxagU7s3FodhGibgzoFG09h6kYWpA/640?wx_fmt=png&from;=appmsg)

后者可以利用其免费提供的token进行二次开发

用手机号注册登录接口（如有全局T，也可以邮箱登录，括号内看不懂的直接略过）

注册即送100W token，除非你和小懒一样打算用来解读大量文章（每天也最多消耗1万token），正常使用根本用不完

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4MylbHGoYOUC5rfCUGKF4wKushK2MB0c69QAxTb3geK93eyicu2JDnfA/640?wx_fmt=png&from;=appmsg)

在接口文档里有教程，不过咱们还是简单过一下入门教程，做一个命令行端的机器人

首先安装python环境（网上教程很多，很简单）

然后安装openai库：

`pip install openai`

里面有现成的python代码，我们来稍微改一下

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4lcufyCeINxTXD6M6ss1YpdSnIVUnaxlb0MLbHicqUj6C5El0kQjLWfA/640?wx_fmt=png&from;=appmsg)

改成这样：

    
    
    from openai import OpenAI  
      
    def ai_res(system_roll,user_content):  
        client = OpenAI(api_key="这里输入你自己申请的key", base_url="https://api.deepseek.com/v1")  
      
        response = client.chat.completions.create(  
            model="deepseek-chat",  
            messages=[  
                {"role": "system", "content": system_roll},  
                {"role": "user", "content": user_content},  
            ]  
        )  
      
        print(response.choices[0].message.content)  
    if __name__ == '__main__':  
        system_roll = input("这里输入你要设定的角色：")  
        while 1:  
            user_content = input("请输入对话内容：")  
            ai_res(system_roll,user_content)  
    

上面的key自己申请后填入

运行上面的脚本，就可以在窗口里设定角色，然后直接对话了

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4UUgbe54zmOM2oA4iawM0eicmyOWQIpBsEzwEov0GYexmeo0IL3ChE5MA/640?wx_fmt=png&from;=appmsg)

速度有点慢，但是运行成功啦

代码的编写就简单介绍到这里，更多内容可以自行查看文档~

不想自己写代码也不想用它的网页端，也可以利用开源软件实现自行搭建！

点击这个集成应用

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4ZxM7aBuu6CNic4icaEDkZeSmQGYRbfj6WpIPnQ9DiaPzp8Oq4IaurLS6Q/640?wx_fmt=png&from;=appmsg)

可以看到有不少应用和插件可以直接调用它的Key

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4rz78I5vYxRd27x6Mw3mzAEuFZatJvTX6v5CRuuxJUtmd5iclJjxByog/640?wx_fmt=png&from;=appmsg)

从软件到浏览器插件，VScode插件，都涵盖了

小懒怀疑那些所谓给你GPT4的国产假AI，都是这样套壳的~

咱们这里就举例之前安利过的沉浸式翻译插件。其他的自行尝试

插件插件设置，自定义Key，输入key，输入自定义模型名称：deepseek-chat

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o45WelOW6qramqSaJWnB2avOUBmdvKY5MEyIV1kQZIFPRBdx4kZ9DWibg/640?wx_fmt=png&from;=appmsg)

API接口输入：https://api.deepseek.com/v1/chat/completions

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4hjQ4ic8icoK6r5yXfhK78aiaBtMBFh2XpiaxbFGfic8XNjjUFLEtDHOupKg/640?wx_fmt=png&from;=appmsg)

这样插件翻译的来源就是你的接口啦~

我们打开BBC一篇新闻看看效果

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4IUPLG38bYGic4BOwib5zXqxscUiav1RH2DUQf4L8qVdfibhBULKQicZ6C6w/640?wx_fmt=png&from;=appmsg)

（沉浸式翻译这种原文对照的翻译方式真是太酷拉）  

效果还是很不错的~

## 总结

如果你现在还没用过AI工具，那么建议你试试小懒推荐的Kimi：

[又一AI神器，免费无限制！](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247489550&idx=1&sn=3bd47498843645d958ed318b88b35363&chksm=c0ed63aef79aeab870e0c95aa980ca21b2b567f59bb725809f2a63a5db921e718f28c0045fab&token=408107735&lang=zh_CN&scene=21#wechat_redirect)

今天分享的AI大模型，更多的是带大家尝试着学习使用AI的key

随着越来越多的工具集成AI，后面很多软件也会预留出AI接口出来

到时候大家就知道这是怎么一回事了

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4gIDZHMrT1hzPE2IiauL0Eu4z9Iv94hiamqaqzP8plqL7b9HD3H1f5vFQ/640?wx_fmt=png&from;=appmsg)

今天的deepseek提供的和OpenAI兼容的格式，这类后来居上的大模型后续肯定也都是以OpenAI为准的，大家学一下后面也会用得到

自定义接口的回答没有Kimi的快速，不过小懒是打算用来给大家导读公众号文章内容的，挂在后台自动化所以对速度要求不大

这是测试下来的效果，挺不错：

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4Ej1q3ic7jNdt0iaPkAwUHsE2Fu7vzv25Kf5SZa3ZQsohurwzib0WAfoyA/640?wx_fmt=png&from;=appmsg)

## 资源领取

今天分享的资源无需后台回复领取，直接文章里复制网址到浏览器访问即可~

粉丝防走丢麻烦添加小懒备用号VX，每天朋友圈分享早报等内容，不会发广告

更不会私信打扰大家（小懒才懒得发私信）

![](https://mmbiz.qpic.cn/mmbiz_jpg/Rmd3GnW8BRuMqPkiaJgW6znyhJmJ7era1mEShL3iaiabxRJpHIMZscNYAffvpDrJiablAzdNej51nfSQshHeJI669Q/640?wxfrom=12&tp;=wxpic&wx;_fmt=jpeg)

## 懒人专属群

[懒人专属群](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247486907&idx=1&sn=23a2e5c2d932caad06b5d6190e9415c9&scene=21#wechat_redirect)持续纳新，本月纳新介绍点击查看：

[【懒人专属群】四月纳新，欢迎加入~](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247490055&idx=1&sn=fe1119fde2a73e7e20ba5f1fc0871fa6&chksm=c0ed61a7f79ae8b168def35fca58403d1bdbcc220535dd1c675f2e6641f5d38e8cb52dee5621&token=1498998905&lang=zh_CN&scene=21#wechat_redirect)

左拉标签公众号懒人搜索，懒人专属群介绍[](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247486907&idx=1&sn=23a2e5c2d932caad06b5d6190e9415c9&scene=21#wechat_redirect)

 ***公众号懒人搜索 | 手机端访问查看完整样式 | 标签可以向左拖拽，来回拖动**

有需要进群的Bro欢迎添加主号（本号好友已满，所以仅供群友啦）

![](https://mmbiz.qpic.cn/sz_mmbiz_png/BXJXNRRKQNL2TXGXG4RpnR4Oa6BBiaMafcicNzVIMy2BZagKPXf95Tj9OCNzdtlyxqluSfibjAlOCejsg2rXxJ18A/640?wx_fmt=png&from;=appmsg&wxfrom;=5&wx;_lazy=1&wx;_co=1)

## 粉丝反馈

因为新公众号没有留言功能，需要反馈或者留言，麻烦识别下图访问：

![](https://mmbiz.qpic.cn/sz_mmbiz_png/RDnsI9KkLHXUp35ZZUH6anzI01OzYCVHYOslcNaYdqXU31j38icickWjaHliaO82mELSfv1sRKYgmloTkzxRLT3CQ/640?wx_fmt=png&from;=appmsg)长按识别

## 今日一言

> 有思想，也有忧伤和理想，这才是生活。
>
> ——陀思妥耶夫斯基

![](https://mmbiz.qpic.cn/sz_mmbiz_jpg/BXJXNRRKQNKVJ6NMVnqduDoByTbicy6o4k1yLgOtrOAUiafDoVRwgQtiamXiadicCLh3wcwmGR8bWh7ymRTYib9XBI0g/640?wx_fmt=jpeg&from;=appmsg)

## 推荐阅读

[吾爱大佬神作，2.0版本](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247490091&idx=1&sn=94878b2caaa335f33151e0ebc388ba5c&chksm=c0ed618bf79ae89dbeeed07239e36479a9445d14bfceae0545445fe2781e65ddf1d3d7cc57d3&token=1498998905&lang=zh_CN&scene=21#wechat_redirect)

[【懒人专属群】四月纳新，欢迎加入~](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247490055&idx=1&sn=fe1119fde2a73e7e20ba5f1fc0871fa6&chksm=c0ed61a7f79ae8b168def35fca58403d1bdbcc220535dd1c675f2e6641f5d38e8cb52dee5621&token=434182421&lang=zh_CN&scene=21#wechat_redirect)

[又一NB插件，高效办公！](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247490032&idx=1&sn=85a474191db1372cf8a50d5a101b9642&chksm=c0ed6250f79aeb46afd32f274cfde342bd45306c225cb8ec3566c927984b74474093c3ed108f&token=434182421&lang=zh_CN&scene=21#wechat_redirect)

[有生之年](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247490011&idx=1&sn=1128a83e937d4c1de83cb7059609dbb8&chksm=c0ed627bf79aeb6db20ca07a7922f49f859cd4672a9fb10496131a68cb314baa87babc9c60f7&token=434182421&lang=zh_CN&scene=21#wechat_redirect)

[神级电子书格式，配套编辑器！](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247489986&idx=1&sn=9e647fe8a0663d4b8589bbc79dd9212b&chksm=c0ed6262f79aeb74208e368741b26ff4d37521e07dc718f152e377bf6effc8c73d2a1f99f47f&token=434182421&lang=zh_CN&scene=21#wechat_redirect)

[隐私泄露？请勿用于非法用途！](https://mp.weixin.qq.com/s?__biz=MzkwNjE5NDYzOQ==&mid=2247489905&idx=1&sn=2a55d406b85bda32717c6c89a1e2c523&chksm=c0ed62d1f79aebc718a9e99051ddd4f98122233e1194785a7bde3393efd2a2c43e7c93e9f544&token=434182421&lang=zh_CN&scene=21#wechat_redirect)

[](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzkwNjE5NDYzOQ==&action=getalbum&album_id=3095199290177650691#wechat_redirect)[](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzkwNjE5NDYzOQ==&action=getalbum&album_id=3184635951063531523#wechat_redirect)[](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzkwNjE5NDYzOQ==&action=getalbum&album_id=3189384915092537344#wechat_redirect)[](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzkwNjE5NDYzOQ==&action=getalbum&album_id=3095199290177650691#wechat_redirect)如页面未加载，请刷新重试

 ***公众号懒人搜索 | 点击跳转专题 | 欢迎订阅**

* * *

> 如果你喜欢小懒的推文，希望可以把公众号文章分享出去
>
> 你的支持很重要~

![](https://mmbiz.qpic.cn/sz_mmbiz_gif/BXJXNRRKQNJ6YdLcSex3A3fRP26rl1cS3HO7V1sQUXcdiakzhwpgs1FicmG6XVSr6w6VRhSpuiagjCk1UcMxSbSdg/640?wx_fmt=gif&from;=appmsg)

