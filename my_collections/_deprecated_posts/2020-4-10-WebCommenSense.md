---
title: 网络常识小科普
tags: Tech\技术
key: GFWWoLaiLa
layout: article
license: true
toc: true
pageview: true
aside:
    toc: true
sitemap: false
# mathjax: true
---

<meta itemprop="name" property="og:title" content="网络常识小科普">
<meta name="description" itemprop="description" property="og:description" content="以上，便是小编为大家整理的关于如何上不存在网站的方法……">
<meta itemprop="image" property="og:image" content="https://raw.githubusercontent.com/ZaoHan415/ZaoHan415.github.io/master/assets/images/BeHit.jpg">


共3185字，预计阅读时间6分钟。
{:.info}

这篇文章将会把读者当作什么都不懂的小白，讨论以下几个问题：

- 什么是互联网
- 互联网是怎么工作的
- 假如动森、AO3等等东西被:no_entry:了，是怎么:no_entry:的
- 动森真的被:no_entry:了，我们怎么接着和歪果老哥老姐联机

<!--more-->
另外：

- 虽然:baby:的博客不怕被:no_entry:，但是为了节目效果，我使用:no_entry:这个表情来代替。
- :baby:水平有限，希望各位看官批评指正。
- :baby:就是蹭一波热度，没别的意思。

## 什么是互联网

用电线把大家连起来，电线里可以传递电信号，就叫“网”。

当对象儿给你发句“在吗”，消息被转化成电信号，沿着电线送到你家，你的手机再把电信号转化成“在吗”，于是你就乐啦。

这么多电线，电线怎么知道把你对象儿的消息送到哪儿呢？

## 互联网是怎么工作的

QQ的工作机理比较复杂，假设你对象是度娘，就比较好说清。在浏览器地址框里敲入www.baidu.com，按回车，就找到了度娘。度娘住哪儿呢？度娘活在服务器里，**服务器**，就是一个大电脑；全世界每个连上网的电脑都有一套通用门牌号，四个数，叫**IP地址**，度娘生在大户人家，有好多门牌号能找到她，比方说你在地址框敲39.156.69.79试试。你家接入网线后也有网络门牌号，只不过你家电脑里没得度娘，所以在地址框里敲进你家的IP地址就啥也看不到。

当你要问度娘一个问题，就好比给度娘写了封信；现在有了信，有了门牌号，谁来送信呢？那在咱们国家就是中国电信、中国移动，在外国就是别的公司。你给电信交了网费，他们就从自己的**路由服务器**上引根电线出来给你。顾名思义，路由服务器也是个大电脑，但是这个电脑他不养度娘，他“路由”，也就是找路+送信。

![IP_router](/assets/images/IP_router.png){:.shadow}

你把要问度娘的话和度娘门牌号一起发给路由器，路由器知道上哪儿去找所有人的家——假设度娘居住的服务器离你家挺近，有线直接连到这个路由器身上，那直接送过去就成啦；若是度娘住在地球对面的资本主义强国（**以下简称姿娘**），那得把你的信和地址原样送给资本主义的服务器，再让姓资的服务器去找姓资的度娘。

问题来了，四个数字毫无规律，你怎么知道度娘的门牌号呢？大伙儿想了个办法，给度娘起了baidu.com这个好听好记的**域名**，搞了个**DNS服务器**，你要找度娘，先问DNS服务器baidu.com门牌号是啥，DNS把号发给你，你拿着号接着找度娘。有时候DNS出了问题，你这边就会显示：

![DNS_error](/assets/images/dns-server-cannot-be-reached.png){:.shadow}

## 网站是如何被ban的

中国电信、中国移动，顾名思义是两个:baby:，要听家里大人的话。有国内的网站不听话，咱:older_man:可以依法治理。但是，如果别人家的:baby:不听咱:older_man:的话，咱:older_man:还想管教人家，咋办呢？咱:older_man:于是叫人搞了一个叫GFW的东西。这个名字不是我瞎编的，是咱:older_man:自己起的名字，不信可以看百度百科：

![gfw_baike](/assets/images/GFW_baike.png){:.shadow}

这个GFW就好比矗立在我国国境线上忠诚守卫的战士，只不过当战士很光荣，GFW却有些行事隐秘见不得人。GFW具体是怎么办事儿的，咱们外人不清楚，但我们仍然可以捕风捉影地略知一二——

具体来说，GFW也是好多个超级大的电脑，守着所有通向咱:older_man:管不住的蛮夷之地的网线，没日没夜地进行以下工作：

- 每一封出境入境的信他都要复制一份来仔细研究，要是发现里面写了不适合小孩子看的内容，就做一封假信发给通信的双方，信上写着类似于“我去洗澡了，咱们不聊了”的假话。咱们的电脑基本上都是傻子，一收到这封信就真的会停止聊天。
- GFW发现某些门牌号总发不合适的东西，就安排移动联通等等:baby:把去往这些地址的信故意送错，使其石沉大海，渺无回音。
- 要是有姓资的大户人家坐拥好多门牌号，:no_entry:不动，咋搞呢？那就勒令自家的DNS服务器：“要是有人问某某家在哪儿，你就说不知道”。这种方法见效快，但是缺点也多，假如我拿个小本本抄一堆门牌号，直接拿着去找，就找见了；或者我不问自己家的DNS，而问邻居家的DNS，也能找见。早年间大家把前一种方法叫**修改host文件**，后一种方法叫**修改DNS地址**；当然，随着GFW越来越先进，这俩方法都不太好使了。
- 以上只是最明显的几点，传闻中GFW还发展出很多反制翻:no_entry:软件的技术，可谓魔高一尺，道高一丈，感兴趣的同学可以自行探索。

GFW并不是我国特色，很多国家都有类似的设施，譬如<span class="heimu" title="一个黑幕">韩国人民就无法正常访问色情网站</span>[“北朝鲜唯二的Steam玩家”](https://www.wanplus.com/article/183077.html)。当然朝鲜和咱们的GFW又有所不同——除了特定必需人士外，朝鲜其余人均是物理上的与外网隔离（指压根就没有网线通出去），而咱们的GFW现阶段还采用的是“主动防御”的策略，这既体现了我国先进的技术实力，也使得翻:no_entry:成为可能。

客观地说，**GFW的确为咱们国家的经济发展社会民生、咱们孩子的健康成长做出了很大的贡献**，<span class="heimu" title="又一个黑幕">但既然你都看到这儿了，废话咱也就不多说了</span>。总之，如果你不乐意自己送给外国友人的信被人拿去端详（虽然信内容一般是加密的，也看不出个啥），请管住身边的程序员、工程师朋友，让他们将来莫去给GFW添砖加瓦。

## 怎么不被ban

知道了GFW的原理，那翻:no_entry:的方法就显而易见了——

- 首先，你需要一个没被:no_entry:的外国朋友。
- 假设你想问姿娘一个问题，你先把问题发给外国朋友，朋友替你问姿娘；姿娘的回复，朋友再原样转发给你。
- 这个外国朋友不能在朝鲜，当然也不能在韩国<span class="heimu" title="再一个黑幕">假定你确实想看不可描述的网站</span>。如果你还想回复快一点儿，自然也不能在网速慢的地区。

这个外国朋友——说白了是个重复劳动的工具人——能做的事情，程序猿们都帮大家弄好了，只要在你的手机/电脑与这台外国电脑（服务器）上装上合适的程序，并合理地设计他们之间的来往消息格式，学名叫做**VPN协议**，就可以无卡顿地流畅访问歪果网站惹。

自防火长城出世以来，VPN协议和GFW反制VPN的功力都在不断增长。协议方面的事情，并不需要我们一般用户操心，旧的、不安全的协议会被自然淘汰，而目前的主流协议有ShadowSocksR、v2Ray等，我们拿来用即可。

要真正翻过:no_entry:，下面两个要素必须要搞定：

要素一：你的设备上要有相应的程序。这一点非常好搞定，不用翻:no_entry:也可以下载到，如：

- v2Ray 安卓客户端[Kitsunebi](https://github.com/eycorsican/kitsunebi-android/releases)
- ShadowSocksR 安卓客户端[发布页](https://github.com/shadowsocksr-backup/shadowsocksr-android/releases)
- v2ray Windows、Linux、macOS跨平台客户端[Qv2ray](https://github.com/Qv2ray/Qv2ray)

要素二：需要给某台外国电脑上装上配套的程序。依然，程序好搞，但外国电脑不好搞，有下面几种方式搞到外国电脑：

- 找阿里、腾讯等互联网公司租一个，市场价格最低配置一年1000元左右，然后自己在上面装程序、配协议。门槛较高，但隐私性极强，并且还可以进行搭自己的网站等操作。缺点是如果你和服务器间的往来通信不幸被GFW发现，或是自己搭了一个不被允许的网站，你的服务器可能会被:no_entry:掉，从而失去翻:no_entry:功能。
- 找专业做翻:no_entry:、网络加速功能的公司买一个，自用市场价约400元每年，你掏钱，人家办事，不用自个儿操心。缺点是提供这种服务的公司一般都被:no_entry:了，所以你得先翻:no_entry:才能购买。通信协议虽然提供加密功能，但你的隐私依然可能会被这些收了你钱的公司获取（尤其是对于技术不敏感的同学），请擦亮眼睛，小心为上。偷偷放三个在被墙边缘试探的公司网站，请酌情点击（后两个:baby:也没用过，但我知道你点第一个:baby:可以白嫖几G流量【手动滑稽】）：
  - [BoomCloud](https://www.boomsse.com/aff.php?aff=1519)
  - [V2BOX](https://www.v2box.net/)
  - [心阶](https://www.xinjiecloud.vip/auth/register?code=fmLG)
- 的确有很多免费提供境外服务器的公司与组织，但请记住，**服务器的运行维护需要成本，没有人会白白做公益，羊毛永远出在羊身上**，比较遵守商业道德的情况下，他们只是多收点儿广告费了事；更邪恶一点儿的，比方法轮功组织，曾经在很长时间内向大陆地区免费提供翻:no_entry:软件“自由门”，打的什么算盘，就不宜公开讨论了（:baby: 人生中第一次掏钱买的VPN就是挂着自由门搜出来的:joy:）
- 只要敢想，办法还很多，比如飞去外国，买一台服务器，联网、开机，再飞回来……等等。

## 到底该怎么搞？？

说了这么多，歪果服务器怎么搞到底是怎么回事呢？下面，小编为大家整理了关于“如何搞到翻:no_entry:服务器”的一些回答，希望可以帮到大家：

1. 找一个对翻:no_entry:有硬性需求的行业人士，如码农，或是学术从业者，如化学学院搬砖的、学数学的，或是热爱“出征”外网的朋友，等等。
2. 询问TA是否会翻:no_entry:，如果是，前往第3条，如果否，则前往第4条。
3. 请TA好吃好喝，求他教你。或其它下三滥/少儿不宜的招数。
4. 嘲讽TA。例句：“你连翻:no_entry:都不会，自称程序猿/媛真的大丈夫:horse:”。如果嘲讽成功，TA学会了，则前往第3条；如果他还是不会，你可以去找祖安人学习对线技术，重新开始本条……或是前往第1条，从头再来。
5. 如果以上4条陷入死循环，还请自行钻研，只要愿意下功夫搞，百度上的信息便足够了。

以上，便是小编为大家整理的关于如何上不存在网站的方法。大家可能会很惊讶不存在的网站怎么会这么上呢？但事实就是这样，小编也感到非常惊讶。

<img class="image image--md" alt="被打.jpg" src="/assets/images/BeHit.jpg"/>

这就是关于歪果服务器怎么搞的事情了，大家有什么想法呢，欢迎在评论区告诉小编一起讨论哦！

![再见](/assets/images/goodbye.jpg)