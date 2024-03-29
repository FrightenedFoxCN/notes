---
comments: True
---

# Francis Bouceux: Some flavours of topos theory

> 本文译自 Francis Bouceux 2022 年在 Louvain-la-Neuve 的短期课程。根据笔者此时的心情，我们在本系列中将 topos 翻译成拓扑斯，其它术语在用到时另外注明，基本采纳标准翻译。

拓扑空间上的层（sheaf）的说法大约出现在二战期间，它在诸如微分几何等领域中提供了一种处理局部问题的有力手段。从拓扑空间到宇象（locale）[^1]，即类似于拓扑空间中的开集的格的推广是相当直接的。但是若是推广到位形（site）[^2]，即带有 Grothendieck 拓扑的小范畴（small category）上的层，事情就会变得有趣起来了。在对概型的研究中，位形上的层发挥着关键性的作用。在 60 年代末，F. W. Lawvere 引入了初等拓扑斯（elementary topos）的概念。它满足两条公理，而集合上的层构成的范畴正是它的一个典型。每个拓扑斯都给出了直觉逻辑（intuitionistic logic）的一个模型（model）。

[^1]: 这个词没有标准翻译，采此翻译的原因见笔者前面的[一篇日常笔记](../../dnotes/0716locale_frame/)。

[^2]: 同样没有找到标准翻译，考虑到 scheme 标译为概型，做此翻译，注意与分析力学中位形空间（configuration space）是完全不同的东西。

这些笔记的目标是速览拓扑斯理论的一些方面，不去深入探究证明细节（但会给出参考资料），也不去考察其在其他领域（如几何等）中的应用。在此，我们假定读者熟悉范畴论的语言。

第一节课的核心是层拓扑斯：拓扑空间上的层、宇象上的层和位形上的层。我们表明，这些层拓扑斯满足两条基本的性质，它们将作为初等拓扑斯的定义再次出现。所有这些拓扑斯都是所谓的 Grothendieck 拓扑斯。

第二节课的主题是初等拓扑斯：那些存在子对象分类子（subobject classifier）的笛卡尔闭范畴。我们将重点探讨它们的强正合性（strong exactness），这是两条公理的直接推论。我们还要引入所谓的无穷公理（axiom of infinity），它使我们能够在初等拓扑斯中探讨算数、分析、几何等等理论。

第三节课将引入初等拓扑斯中的内拓扑（internal topology）和内层（internal sheaf），它们在各个方面可以视作层论的推广。同时，我们还可以谈谈布尔拓扑斯（Boolean topos）和排中律（Law of Excluded Middle）的问题。

第四节课相当关键，但非常技术性：拓扑斯的内逻辑（internal logic）的讨论在此敞开大门。这是一种形式的直觉逻辑，让我们能够在拓扑斯中像在集合中一样“逐元素地”证明定理。

第五节课以拓扑斯的几何态射（geometric morphism）开篇。它的一个特例是在两个对应的层拓扑斯之间连续函数的作用。几何态射被用来探讨某个理论的“分类拓扑斯”（classifying topos）：一个包含理论的一个一般模型的 Grothendieck 拓扑斯，它能够通过几何态射的象重建出这个理论的所有模型对应的所有 Grothendieck 拓扑斯。

感谢 Marino Gram 邀请我来讲授这些课程，让我得以重温教书育人的乐趣。