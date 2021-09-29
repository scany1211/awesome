---

layout: post
title: 编程语言的动态性
category: 技术
tags: Basic
keywords: dynamic

---

## 简介

* TOC
{:toc}

## 类型系统层面上的动态性

根据类型检查是在编译期还是在运行期进行的，我们可以把计算机语言分为两类：

1. 静态类型语言（全部或者几乎全部的类型检查是在编译期进行的）。因为编译期做了类型检查，运行期不用再检查类型，性能更高。像 C、Java 和 Go 语言，在编译时就对类型做很多处理，包括检查类型是否匹配，以及进行缺省的类型转换
2. 动态类型语言（类型的检查是在运行期进行的）。


## 泛型编程

来自陈皓《左耳听风》笔记

编程语言的本质是帮助程序猿屏蔽底层机器代码，使得我们可以更为关注业务逻辑代码。

programming paradigm，范即模范之意，是一类典型的编程风格，不同的风格解决的都是同一个问题：如何写出更为通用、更具可重用性的代码或模块。

作者提供了一个视角，从“程序=算法 + 数据结构”出发，从语言对泛型的支持来看待语言的演化：泛型编程的支持。**逻辑重用 ==> 算法复用性高 ==> 数据结构标准化 ==> 类型泛型。简单说就是让数据结构 迁就算法。**

1. 对于程序=算法 + 数据结构，C语言有以下问题：一个通用的算法，需要对所处理的数据的数据类型进行适配。
2. C语言的伟大之处在于 程序猿可以在高级语言的特性之上还能简单的做任何底层上的微观控制。但在编程这个世界中，更多的编程工作是解决业务上的问题，而不是计算机的问题。
3. C++的作者有一本书《C++语言的设计和演化》这本书系统介绍了C++诞生的背景和初衷： 早先很多是对C的强化和净化 ==> 用引用解决指针问题；用class来解决对象的创建、赋值、销毁等问题（C指针干这些都要手动）。泛型编程是C++的重点
4. 理想情况下，算法应是和数据结构以及类型无关的，各种特殊的数据类型理应做好自己分内的工作。算法只关心一个标准的实现。而对于泛型的抽象，我们需要回答的问题是：如果我们的数据类型符合通用算法，那么对数据类型的最小需求是什么？

	* **减少自定义数据类型 与 内建数据类型的差异**。比如漏出构建、析构、克隆等函数 的hook交由语言自动执行，类似int自动帮你初始化为0.
	* 减少自定义数据类型之间的差异。List、Set 抽象为Iterator，而调用Iterator.next 可以按照实际的数据类型反应。**从泛型的角度理解Iterator 的价值**

5. 使用动态类型语言写sum(x,y)貌似没有泛型的问题，但在你要明确类型时又很难受，比如将一个不知道什么类型的x转为一个数字。

一个良好的泛型编程需要解决 几个问题

1. 算法的泛型，将sum 和max、min等都抽象为 reduce（把数组聚合为一个值），也就是将for 循环之内的 逻辑/算法 作为参数传入。
2. 类型的泛型，比如sum int 改为sum T。
3. 数据结构的泛型，比如找到一种公共的方式来描述List、Set、Map 等 ==> Iterator

![](/public/upload/architecture/type_system.png)

泛型编程于1985年在论文 generic programming 中被这样定义：Generic programming centers around the idea of abstracting from concrete, efficient algorithms to obtain generic algorithms that can be combined with different data representations to produce a wide variety of useful software. 屏蔽掉数据和操作数据的细节，让算法更为通用，让编程者更多的关注算法的结构，而不是在算法那中处理不同的数据类型。

## 编程语言层面上的动态性

[动态语言之三：语言的动态性](http://ooaer.iteye.com/blog/1704766) 要点如下

1. 不同的语言具有不同程度的动态特性，现代大多数语言都是介于二者之间的折中。下面是两个极端：

	1. Fortran语言不支持堆栈，所有的变量和子程序都是在编译时分配好内存的，不能进行动态内存分配，因而不能进行函数递归调用。
	2. Perl、Python和Ruby语言可以在运行时修改类的结构或定义，变量的类型可以按需改变，Lisp语言甚至可以在运行时动态地改变自身的代码
	
1. 动态语言有多种定义，本文采用：动态语言是指能够在运行时改变程序结构和变量类型的语言
2. **程序中定义的操作一般需要特定类型的参数作为操作的输入，操作只有在接收到类型正确的参数时才能正确无误的执行（包括操作内存）。所以无论哪种语言，都逃避不了一个特定的类型系统**
3. 动态类型语言在每个数据对象中保存一个类型标签表明该数据对象的类型，在运行时进行动态类型检查。比如在表达式C=A+B中，A和B的类型在程序运行时确定，也可以在运行时改变，所以**每次执行 + 操作时都要根据类型标签对A和B的类型进行检查**
4. 动态类型检查的主要优点在于程序设计的灵活性，不需要声明语句，一个变量名绑定的数据对象的类型可以在程序执行时按需改变，使程序员从数据类型摆脱出来。运行时进行的类型检查也存在几点重大不足：

	1. 程序难以调试。只在程序运行到某一条操作时才对其进行类型检查，软件测试时是不能遍历程序中所有的执行路径，这样没有被执行的路径仍有可能存在bugs
	2. 保存大量的类型信息。运行时需要相当大的额外存储空间
	3. 执行效率低，动态类型检查要靠软件模拟实现，主要是在运行时完成的


