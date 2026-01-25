---
title: NeoForge 模组开发教程
type: docs
---


# 欢迎来到我的开发笔记

- 本教程基于 Minecraft 26.1
- 使用 NeoForge 加载器

---
## 绪论

### FML和NeoForge的由来

在很久很久以前（一个可以追溯到Minecraft刚刚发布的年代），人们就开始为Minecraft制作和使用Mod了。那个时候，由于Mod的制作方式是直接通过底层对Minecraft修改，所以将两个Minecraft Mod进行整合几乎是一件不可能的事情。

随后，Minecraft MCP（Minecraft Mod Coder Pack）的诞生，让Mod的制作和整合变得容易。这是因为Minecraft被进行了混淆化，这件事使得原本好看好记的诸如Item这样的类名、方法名、变量名等，通通被混淆化成了alq这样难以阅读和辨认的符号。Minecraft MCP的意义，就是对其进行反混淆，把alq这样的类名用一个诸如Item的名称代替。这使得人们可以通过更改MCP提供的源代码来进行Mod制作。但是，若是想合并两个Mod，必须要把两个Mod的源代码一行一行地进行整合。

直到2010年年底，一个叫作ModLoader的Mod横空出世，这使得Mod的开发方式产生了跨时代性的变化。ModLoader提供了一个框架和一套API，玩家通过这个框架可以很方便地管理Mod，开发者通过这一套API可以完成很多任务，如添加新方块、添加新物品，等等。

从2010年圣诞节前夕，Minecraft Beta版本发布开始，直到2011年年底Minecraft正式版发布，这一段时间被称为Minecraft Mod的“黄金时期”。很多著名的Mod如RailCraft，IndustrialCraft，BuildCraft等，都是这一时期开始开发的。但是，这段时期的Mod开发仍然问题重重。比如BuildCraft和IndistrialCraft就不能共存。他们更改了太多底层的东西。

这些Mod的开发者们看到Mod的整合仍旧困难，他们便发起了一项新的计划，这个计划就是Minecraft Forge。随着Minecraft正式版的发布和“黄金时期”的终结，很多Minecraft Forge的开发者，渐渐不再参与Minecraft Forge的开发。然而随着Mod数量的爆炸式增加，以LexManos和Cpw等为首的开发人员仍然坚持着Minecraft Forge的开发，并加入了很多崭新的特性。他们甚至将ModLoader这个框架整合进了Minecraft Forge，也就是Forge Mod Loader，简称FML。直到今天，Minecraft Forge和通过Minecraft Forge开发的难以计数的Mods，仍在发展壮大。

---

### 阅读本教程需要什么

#### Java等程序设计基础知识

本教程不针对Java初学者，本教程假定读者已经对Java的基础知识有了一定深入的了解。换言之，本教程假设读者已经对下面这些Java概念进行了深入地了解：

- 对象
- 类、属性和方法
- 变量、运算符和表达式
- 条件和循环
- 包、继承、多态和接口
- 泛型
- 容器
- 异常

下面这些Java概念虽然对Mod开发比较重要，但是读者在阅读之前不需要掌握或者只有阅读本教程更深入的部分才需要掌握，如果教程的某一部分认为读者不需要掌握，教程会在用到的时候会加以简要的介绍，如果需要，教程会提醒读者阅读相关的资料：

- 注解
- 数字和字符串的操作
- 输入输出流
- 多线程和同步
- 反射
- 中立字节码

下面这些Java概念和本Mod开发教程无关，虽然这些概念在其他Java应用中比较重要，但在本教程中不会用到。当然，了解这些知识对Mod开发是有一定帮助的：

- 正则表达式
- 图形界面
- 网络
- 数据库
- ... 

#### 不会Java怎么办
> 考虑到一部分读者可能没有基础就像学习mod制作，这里也为大家的语言学习提供一些资源和建议

对于喜欢阅读书籍的朋友，这里推荐一本书[《Head First Java, 2nd Edition》](https://zh.zbeijing.ru/book/5472353/01c04e/head-first-java%E4%B8%AD%E6%96%87%E7%89%88%E7%AC%AC%E4%BA%8C%E7%89%88%E6%B6%B5%E7%9B%96java-50.html)，这本书的中文版适用于没有任何编程基础的读者。如果看完了这本书的前十一章，对于阅读本教程的Java基础知识就已经足够了。如果想深入学习的话，推荐[《Effective Java (3nd Edition)》](https://zh.zbeijing.ru/book/17121294/16a84e/effective-java%E4%B8%AD%E6%96%87%E7%89%88%E5%8E%9F%E4%B9%A6%E7%AC%AC3%E7%89%88.html)和[《The Java Language Specification (3rd Edition)》](https://zh.zbeijing.ru/book/44926553/27af7d/java%E8%AF%AD%E8%A8%80%E8%A7%84%E8%8C%83-%E5%9F%BA%E4%BA%8Ejava-se-8the-java-language-specification-javase-8-edition.html)两本书。

对于喜欢阅读博客的朋友，这里也推荐个人为教程编制的Java教程:
- [中文版]()
- [英文版]()    

除了Java知识之外，了解一些游戏开发的知识，如OpenGL等等，对阅读本教程有一些帮助，但对于阅读本教程没有专门学习的必要，除非作者在某些地方特定指出了对该知识的需要。



---

#### 对Minecraft游戏的基本了解

本教程假设读者在阅读本教程前，已经对Minecraft这款游戏有了一些了解，包括Minecraft中一些现象的运作机制，一些小技巧等有了一些了解。作者也相信对本教程感兴趣的读者已经做到了这一点。



---

#### Java开发环境


---

#### 一定程度的不借助JavaDoc的源代码分析能力
---
#### 对Mod开发的热情、缜密的思维、以及一个足够大而又能正常运作的脑洞
> 这条十分重要！！！说实话，作者不止一次因为Colaborator没有对开发的敬畏之心做了很多本可以避免的繁琐工作。

## 本教程为读者提供什么

---
### 针对 Minecraft 26.1 版本并基于NeoForge的Mod开发教程

---
### 源代码

---
### 简单的实际项目作为Workshop

---
### 手把手的工作环境配置体验


## 参考文献
1. [fmltutor(一个很古老但作者认为写得很好的系列文章)](https://github.com/ustc-zzzz/fmltutor/tree/master)
2. [Harbinger](https://harbinger.covertdragon.team/)
3. [Bosom](https://boson.v2mcdev.com/introducation/intro.html)
4. [JBAcademyJavaCourse](https://hyperskill.org/study-plan)