---

layout: post
title: 如何学习机器学习
category: 技术
tags: MachineLearning
keywords: 深度学习

---


## 前言

机器通过分析大量数据来进行学习。比如说，不需要通过编程来识别猫或人脸，它们可以通过使用图片来进行训练，从而归纳和识别特定的目标。

![](/public/upload/machine/machine_learning_xmind.png)

## 学习路线与材料

现在学习 AI，特别是上手深度学习，已经清楚的出现了两条路子。

1. 以理论为中心，扎扎实实从数学基础开始，把数据科学、机器学习大基础夯实，然后顺势向上学习Deep Learning，再往前既可以做研究，也可以做应用创新。
2. 以工具为中心，直接从Tensorflow、Caffe、MXNET、PyTorch 这些主流的工具着手，以用促练，以练促学。

一般来说，第一条路子适合于还在学校里、离毕业还有两年以上光景的青年学生，而第二条路子适合于已经工作，具有一定开发经验的人，也适合时间有限的转型开发者，这条路见效快，能很快出成果，受到更多人的青睐。但是它也同样需要一个健康的框架，如果自己瞎撞，表面上看很快也能重复别人已经做出来的成果，但是外强中干，并不具备解决新问题的能力，而且一般来说在知识和技能体系里会存在重大的缺陷。

斯坦福大学今年上半年开了一门课程，叫做 CS20SI: Tensorflow for Deep Learning Research。可以说这门课程为上面所说的第二条路径规划了一个非常漂亮的框架。学习斯家的课程，你很容易找到一种文武双修、理论与实践生命大和谐的感觉。特别是斯家课程的课件之细致完备、练习之精到舒适，处处体现一种“生怕你学不会、学不懂”的关怀。[stanford-tensorflow-tutorials](https://github.com/chiphuyen/stanford-tensorflow-tutorials)

王天一：人工智能的价值在于落地，它的优势则是几乎所有领域都有用武之地。与其星辰大海，不如近水楼台。将自身专业的领域知识和人工智能的方法结合，以解决实际问题，才是搭上人工智能这趟快列的正确方法。 

三百多页ppt，就说比较好的学习材料[李宏毅一天搞懂深度學習](https://www.slideshare.net/tw_dsconf/ss-62245351?qid=108adce3-2c3d-4758-a830-95d0a57e46bc)

[Deep Learning](http://www.deeplearningbook.org/)

[吴恩达给你的人工智能第一课](https://mooc.study.163.com/smartSpec/detail/1001319001.htm) 这是笔者实际的入门课程

才云内部的课程资料：[适合传统软件工程师的 Machine Learning 学习路径](https://github.com/caicloud/mlsys-ladder?from=timeline)

[ 2017 斯坦福李飞飞视觉识别课程](https://github.com/caicloud/mlsys-ladder?from=timeline) 虽然说得是视觉识别，但一些机器学习的基本原理也值得一看。[CS231n课程笔记翻译：神经网络笔记1（上）](https://zhuanlan.zhihu.com/p/21462488?refer=intelligentunit) 未读

[李宏毅2020机器学习深度学习(完整版)国语](https://www.bilibili.com/video/BV1JE411g7XF?p=16) 也非常的不错。

## 机器学习的数学基础

[分层的概念——认知的基石](https://mp.weixin.qq.com/s?__biz=MzA4NTg1MjM0Mg==&mid=2657261549&idx=1&sn=350d445acf339ce19e7aab1ff19d92d0&chksm=84479e34b3301722aea0aaaa6f74656dd3e9509d70bf5719fb3992d744312bdd1484fc0c1852&mpshare=1&scene=23&srcid=1105hMUVZrVwuoX8KbtS0Vl0%23rd)

利用机器学习，我们至少能解决两个大类的问题：

1. 分类(Classification)
2. 回归(Regression)。

为了解决这些问题，机器学习就像一个工具箱，为我们提供了很多现成的的算法框架，比如：LR, 决策树，随机森林，Gradient boosting等等，还有近两年大热的深度学习的各种算法，但要想做到深入的话呢，只是会使用这些现成的算法库还不够，还需要在底层的数学原理上有所把握。比如

1. 研究优化理论，才能够有更好的思路去设计和优化目标函数；
2. 研究统计学，才能够理解机器学习本质的由来，理解为什么机器学习的方法能够使得模型一步步地逼近真实的数据分布；
3. 研究线性代数，才能够更灵活地使用矩阵这一数学工具，提高了性能且表达简洁，才能够更好地理解机器学习中涉及到的维数灾难及降维问题；
4. 研究信息论，才能够准确地度量不同概率分布之间的差异。

王天一：人工智能虽然复杂，但并不神秘。它建立在数学基础上，通过简单模型的组合实现复杂功能。在工程上，深度神经网络通常以其恒河沙数般的参数让人望而却步；可在理论上，各种机器学习方法的数学原理却具有更优的可解释性。从事高端研究工作固然需要非凡的头脑，但理解人工智能的基本原理绝非普通人的遥不可及的梦想。

## AI 的范畴

[周志华：“深”为什么重要，以及还有什么深的网络](https://mp.weixin.qq.com/s/U6DvnuLogfmfYzwe5ULmiQ)

1. 深度学习就等于深度神经网络吗？深度学习是机器学习中使用深度神经网络的的子领域。所以如果我们要谈深度学习的话，是绕不开深度神经网络的。
2. 神经网络需要可微的函数、需要能够计算梯度，这是最根本最重要的
3. 我们知道一个机器学习模型，它的复杂度实际上和它的容量有关，而容量又跟它的学习能力有关。所以就是说学习能力和复杂度是有关的。机器学习界早就知道，如果我们能够增强一个学习模型的复杂度，那么它的学习能力能够提升。那怎么样去提高复杂度，对神经网络这样的模型来说，有两条很明显的途径。一条是我们把模型变深，一条是把它变宽。如果从提升复杂度的角度，那么变深是会更有效的。当你变宽的时候，你只不过是增加了一些计算单元，增加了函数的个数，在变深的时候不仅增加了个数，其实还增加了它的嵌入的程度。既然你们早就知道要建立更深的模型了？那为什么现在才开始做？这就涉及到另外一个问题，我们把机器学习的学习能力变强了，这其实未必是一件好事。因为机器学习一直在斗争的一个问题，就是经常会碰到过拟合（overfit）。我希望学到的是一般规律，能够用来预测未来的事情。但是有时候我可能把这个样本数据本身的一些独特特性学出来了，而不是一般规律。错误地把它当成一般规律来用的时候，会犯巨大的错误。那现在我们为什么可以用很复杂的模型？其实我们设计了许多方法来对付过拟合，比如神经网络有 dropout、early-stop 等。但有一个因素非常简单、非常有效，那就是用很大的数据。
4. 为什么深度神经网络能成功？就是因为复杂度大。如果从复杂度这个角度去解释的话，我们就没法说清楚为什么扁平的（flat），或者宽的网络做不到深度神经网络的性能？实际上我们把网络变宽，虽然它的效率不是那么高，但是它同样也能起到增加复杂度的能力。但是这样的模型在应用里面怎么试，我们都发现它不如深度神经网络好。所以我们要问这么一个问题：深度神经网络里面最本质的东西到底是什么？今天我们的回答是，本质是表征学习的能力。以往我们用机器学习解决一个问题的时候，首先我们拿到一个数据，比如说这个数据对象是个图像，然后我们就用很多特征把它描述出来，比如说颜色、纹理等等。这些特征都是我们人类专家通过手工来设计的，表达出来之后我们再去进行学习。而今天我们有了深度学习之后，现在不再需要手工去设计特征了。你把数据从一端扔进去，结果从另外一端就出来了，中间所有的特征完全可以通过学习自己来解决。所以这就是我们所谓的特征学习，或者说表征学习。我们都认可这和以往的机器学习技术相比可以说是一个很大的进步，这一点非常重要。我们不再需要依赖人类专家去设计特征了。这个过程中的关键点是什么呢？是逐层计算，layer-by-layer processing。
5. 当我们有很大的训练数据的时候，这就要求我们必须要有很复杂的模型。否则假设我们用一个线性模型的话，给你 2000 万样本还是 2 亿的样本，其实对它没有太大区别。它已经学不进去了。而我们有了充分的复杂度，恰恰它又给我们使用深度模型加了一分。所以正是因为这几个原因，我们才觉得这是深度模型里面最关键的事情。
6. 这是我们现在的一个认识：第一，我们要有逐层的处理；第二，我们要有特征的内部变换；第三，我们要有足够的模型复杂度。这三件事情是我们认为深度神经网络为什么能够成功的比较关键的原因。或者说，这是我们给出的一个猜测。那如果满足这几个条件，我们其实马上就可以想到，那我不一定要用神经网络。凡是用过深度神经网络的人都会知道，你要花大量的精力来调它的参数，其实在图像上面调参数的经验，在语音问题上基本上不太有借鉴作用。所以当我们跨任务的时候，这些经验可能就很难共享。还有很多问题，比如说我们在用深度神经网络的时候，模型复杂度必须是事先指定的。因为我们在训练这个模型之前，我们这个神经网络是什么样就必须定了，然后我们才能用 BP 算法等等去训练它。其实这会带来很大的问题，因为我们在没有解决这个任务之前，我们怎么知道这个复杂度应该有多大呢？所以实际上大家做的通常都是设更大的复杂度。比如说 Kaggle 上面的很多竞赛有各种各样的真实问题，有买机票的，有订旅馆的，有做各种的商品推荐等等，我们就可以看到在很多任务上的胜利者并不是神经网络，它往往是像随机森林，像 xgboost 等等这样的模型。深度神经网络获胜的任务，往往就是在图像、视频、声音这几类典型任务上，都是连续的数值建模问题。而在别的凡是涉及到混合建模、离散建模、符号建模这样的任务上，其实深度神经网络的性能可能比其他模型还要差一些。这也就是我们说的「没有免费的午餐定理」，已经有数学证明，一个模型不可能在所有任务中都得到最好的表现。
7. 我们从学术的观点来总结一下，今天我们谈到的深度模型基本上都是深度神经网络。如果用术语来说的话，它是多层、可参数化的、可微分的非线性模块所组成的模型，而这个模型可以用 BP 算法来训练。那么这里面有两个问题。第一，我们现实世界遇到的各种各样的问题的性质，并不是绝对都是可微的，或者用可微的模型能够做最佳建模的。第二，过去几十年里面，我们的机器学习界做了很多模型出来，这些都可以作为我们构建一个系统的基石，而中间有相当一部分模块是不可微的。


[ 图解机器学习：人人都能懂的算法原理](https://mp.weixin.qq.com/s?__biz=MzI5ODQxMTk5MQ==&mid=2247487773&idx=2&sn=ae1eadb1bbe0b5f83bd97c1874dbf3d9&chksm=eca763a5dbd0eab38c343c5f85d38e5cce087bcce39dd60ec7e94caadd69e8d0b2f2468cc6ae&cur_album_id=1815350871241637891&scene=190#rd)深度学习都是神经网络吗？明显并不一定是，例如周志华老师的深度森林，它就是第一个基于不可微构件的深度学习模型。

![](/public/upload/machine/what_is_ai.png)

机器学习下面应该是表示学习（Representation Learning），即概括了所有使用机器学习挖掘表示本身的方法。相比传统 ML 需要手动设计数据特征，这类方法能自己学习好用的数据特征。整个深度学习也是一种表示学习，通过一层层模型从简单表示构建复杂表示。

## 实践

实践说的是：选择入门的编程语言（基本是python）以及编程语言在机器学习方面的库

[机器学习实践指南](https://zhuanlan.zhihu.com/p/29743418)

[CS231n课程笔记翻译：Python Numpy教程](https://zhuanlan.zhihu.com/p/20878530?refer=intelligentunit) 未读

基本原理搞懂之后，可以先找个实际问题+dataset 实操一下 [Kaggle入门，看这一篇就够了](https://zhuanlan.zhihu.com/p/25686876)Kaggle成立于2010年，是一个进行数据发掘和预测竞赛的在线平台。入门级的三个经典练习题目：

1. [逻辑回归应用之Kaggle泰坦尼克之灾](https://blog.csdn.net/han_xiaoyang/article/details/49797143)未做
2. [Kaggle竞赛 — 2017年房价预测](https://www.kaggle.com/neviadomski/how-to-get-to-top-25-with-simple-model-sklearn)未做
3. [大数据竞赛平台——Kaggle 入门](https://blog.csdn.net/u012162613/article/details/41929171)未做

[初学者如何从零开始征战Kaggle竞赛](https://mp.weixin.qq.com/s?__biz=MzI5ODQxMTk5MQ==&mid=2247489435&idx=1&sn=b9ebf571e145b25a33021f31a5f6270f&chksm=eca76523dbd0ec3543903843ee28af0f2dca11264b2b29d87b20c8575ea292d3ffb75f64d8a5&cur_album_id=1815350871241637891&scene=190#rd)
[从技术到科学，中国AI向何处去？](https://mp.weixin.qq.com/s/GV0UFUvDtIiBong0ZAe0LA)


## 工程

海量数据标注 + 大规模计算（训练和推理） + 工程化（python或c++）=AI系统

1. 数据侧：数据整理、数据标注系统
2. 训练侧：集群管理、分布式训练，更快、利用率高更高
2. 推理侧：对训练得到的模型剪枝、蒸馏、量化、压缩，更换算子等 [携程AI推理性能的自动化优化实践](https://mp.weixin.qq.com/s/jVnNMQNo_MsX3uSFRDmevA)

最终目标就是，缩短算法工程师训练一个模型的时间。

## 自动编码器

如何学习特征，用到了自编码器。参考文章

1. [Deep Learning模型之：AutoEncoder自编码器](http://blog.csdn.net/u010555688/article/details/24438311)
2. [系统学习深度学习（二） --自编码器，DA算法，SDA，稀疏自编码器
](http://www.voidcn.com/blog/app_12062011/article/p-6370385.html)

自动编码器基于这样一个事实：原始input（设为x）经过加权（W、b)、映射/传递函数（Sigmoid）之后得到y，再对y反向加权映射回来成为z。

通过反复迭代训练（W、b），使得误差函数最小，即尽可能保证z近似于x，即完美重构了x。

那么可以说（W、b）是成功的，很好的学习了input中的关键特征，不然也不会重构得如此完美。Vincent在2010年的论文中做了研究，发现只要训练W就可以了。

[深度学习系列（四）：什么是稀疏编码](http://blog.csdn.net/on2way/article/details/50389968)