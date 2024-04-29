---
layout: post
title: Multidisciplinary Bootstrap
---

(originally posted on Wechat Official Account: 理思文辩)

# Bootstrap? 跨界出圈的“拔靴带”

*（本文共2043字，预计阅读需要5分钟）*

> \- bootstrap采样翻译成“自助法”是个啥意思？
>
> \- 火遍前端开发者的bootstrap框架又为啥叫这个名字？
>
> \- “拔靴带”？词典上的解释好像看不太懂啊...
>
> 别慌，这就让我们一起来了解看看bootstrap从文学到科技的跨界出圈历程！

**Bootstrap**，所谓“拔靴带”，英文词典上的解释是“a looped strap sewed at the side or the rear top of a boot to help in pulling it on"，即靴子两侧或后边缝制的带状配件，用途是使穿靴更容易，当然现在也可能有设计美感上的考量。

![bootstrap for boots]({{ '/assets/images/bootstrap_for_boots.jpg' | relative_url }})

而在鞋靴设计之外的领域，bootstrap却有着相比于其本意更深远更重要的影响。这一出跨界出圈日记，似乎应该从“吹牛大王”说起...

## 1. 吹牛大王历险记

Baron Munchausen (German: Münchhausen)，中文翻译为闵希豪森男爵或**孟豪森男爵**，是1785年德国作家Rudolf Erich Raspe笔下虚构的一个爱吹牛的德国贵族。他总是爱跟周围人搞笑夸张地讲述他的奇妙探险经历，包括骑过炮弹、被地中海的大鱼吞噬过、前往过月球等等。

Münchhausen的名字取自真实历史上与作家Raspe同时期的一个德国贵族，他参加过1735年-1739年的第四次俄土战争，1760年退伍后，他常常在德国贵族圈的酒席上讲述来源于自己军旅生涯的奇妙故事，并因此小有名气。

据说作家Raspe当时可能受邀参加宴席并听到了Münchhausen讲的内容，于是受到启发、用德语编写了一系列讽刺荒诞的故事，并于1785年以英文出书发表，题为Baron Munchausen's Narrative of his Marvellous Travels and Campaigns in Russia (巴伦·孟豪斯自述：我的俄国奇妙探险)。后来这本书被翻译成多种语言并在19世纪得到了广泛传播，其中比较有名的一版是诗人Gottfried August Bürger扩写翻译的德语版本。“吹牛大王”的故事书至今仍然广受喜爱，尤其是德国和俄罗斯等欧洲国家。

![Munchausen profiles]({{ '/assets/images/bootstrap_munchausen.jpg' | relative_url }})

各种文艺作品中塑造的孟豪森男爵的典型虚拟形象是一个有着鹰钩鼻、翘胡子的老头，在1988年Terry Gilliam编剧导演的好莱坞电影The Adventures of Baron Munchausen (中文翻译：终极天将)中也完美地表现了这一形象，在2011年播出的《风车故事汇：吹牛大王历险记》中也有蔡明老师的精彩cos演绎。再加上网上能找到中文少儿绘本和朗诵录音，“吹牛大王”的故事真的是不可谓是不流行。

## 2. pull oneself up by one's bootstraps

吹牛大王历险记中的一个有名的桥段是，孟豪森男爵骑马陷入沼泽或水中时，拎着辫子把自己和马解救了出来，在上面提到的好莱坞电影中也有通过特效去表达这个故事。然而，这是一个违反牛顿力学原理的吹牛，在现实中是不可能发生的事情。

![Munchausen boostrap]({{ '/assets/images/bootstrap_pull_oneself_up.jpg' | relative_url }})

据说由吹牛大王的故事引申而来，在19世纪开始出现了**pull oneself up by one's bootstraps**的说法，“拎着拔靴带把自己举起来”，如最早在1834年Workingman's Advocate中的句子：
> “It is conjectured that Mr. Murphee will now be enabled to hand himself over the Cumberland river or a barn yard fence by the straps of his boots.”

指的是不依靠外力的帮助、自力更生和自我发展。

## 3. Bootstrap跨界起飞

基于起源于吹牛、但不再包含吹牛的引申含义，bootstrap这个词开始在科学技术和社会商业等诸多领域被应用，这大概是由于“自力更生”、“从0到1”带来的良好联想。

* 从1953年开始，bootstrapping就被用来描述计算机的启动过程（常简写成**booting**），即每一个启动环节都通过载入一个较小较简单的引导程序、启动下一环节所需的更大更复杂的程序。
* bootstrapping还指代构建self-hosting compiler的技术，这里的self-hosting compiler指的是以某一编程语言L编写的用来构建L语言程序的编译器；这个用L语言编写的编译器程序需要由可以编译L语言的编译器进行构建，然而这个编译器本身似乎还未被构建出来；对于这样一个鸡生蛋还是蛋生鸡的问题（**the chicken and egg problem**），一种解决方法是编译器的最初核心版本由其他语言（如汇编语言）构建，然后再逐步扩展成使用L语言最小集构建的编译器版本。
* 在网页前端开发者中，bootstrap是由twitter公司开源的一个非常有名的开源http/css/js框架，支持开发者快速开发原型，特别是具有响应式布局、移动端友好的前端应用。
* 在统计学中，bootstrap自助法是一种常用的重采样技术（**resampling**），是指利用从总体抽样得到的样本数据进行多次有放回的抽样，建立起足以代表总体样本分布的新样本，通常在总体样本量不大或从总体多次抽样困难的限制条件下使用。
* 在人工智能/机器学习领域，一种常用的集成学习方法叫作**bagging**，是bootstrapping aggregation的简称，通过在训练数据上使用bootstrapping有放回采样、训练多个“好而不同”的基础模型，再通过投票等方法汇总得到一个效果更优的最终模型。
* 在商业领域，bootstrapping是指在创业早期不依赖投资人投资、完全靠自己的能力来支应开销、白手起家的创业模式，如利用存款、信用卡、拖延应付账款等方法，这种创业模式能使创业早期的决策更灵活，能更早地接受市场考验，创造了价值后其中后期融资会更容易。

## 4. 总结

Bootstrap这个词，从19世纪的文学作品启程，如今已经在计算机科学、统计科学、人工智能、创业领域纷纷开花，大多表达了受外界帮助有限、依靠自身的力量发展这层意思。

也许你已经在上述的一些跨界应用里接触过bootstrap了，但了解了吹牛大王的故事渊源，是否有对你更生动地理解“自助”这一概念更有帮助呢？

## 参考资料
1. Bootstrapping, Wikipedia
2. Baron Munchausen, Wikipedia
3. The Adventures of Baron Munchausen (1989) Review, Cinemology 101, Youtube
4. 【这个蔡明好像有点不一样】《风车故事汇：吹牛大王历险记》20111205-20111209, 喵星人徒爪煎鱼, bilibili
5. 【小概念】Bootstrap(自助法), silencedream, bilibili
6. 机器学习, 周志华, 清华大学出版社
7. Bootstrapping创业模式：不求人的低成本创业, 刘老师新营销, 微信公众号

*文字由理思文辨原创，图片来源于网络*
