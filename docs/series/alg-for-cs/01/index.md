---
comments: true
---

# 群、环、域及其他

!!! info "本章介绍"
    在这一节中，我们将简要介绍一些结构及其基本性质。在本章中所讨论的性质往往是初等的，而且通常具备组合学的一些性质，因此，一些基本的计数原理是必须的。而且，因为组合学本身的缘故，受笔者水平所限，很多地方会显得相当繁琐，还请大家谅解。

    另外，本章的主要目的是让读者熟悉基本的构造，从而为后面讨论更多抽象概念做铺垫。因此，我们也会涉及一些较为抽象的东西，例如自由构造，例如 Grothendieck 群，这些东西都是可以用比较初等的方式描画，但是有更多的推广的东西，在后面的章节中还会被反复提及。

    在本章及以后的大部分章节中，我们默认的集合论体系是 ZFC 的，除非特殊声明，不讨论集与真类的区别。而且在大部分情况下，没有人会真正意义上用 ZFC 的体系思考，朴素集合论的内容对于我们来说是足够的。映射的定义也默认的，包括关于映射的分类的一些术语（单射、满射、一一对应、像、原像），在文中也不会去一一解释。关系和等价关系的基本思想同样希望读者已经明白，等价关系和等价类的相互作用会称为我们的研究中一个重要的主题。

这一章的起始点是一个集合 $S$。我们不讨论集合论，所以一个光秃秃的集合对我们来说是毫无用处的。而要讨论上面的结构，这一章中用到的方法是在上面构建一个二元映射 $- \cdot -: S \times S \to S$。它被称为 $S$ 上的一个二元运算，一般记作加或者乘，在不引起混淆的情况下可以省去。这个东西事实上没有任何性质，是吗？它可以是平凡的，把所有二元组映到同一个元素，也可以让像铺满整个 $S$，因此还需要在上面施加约束。不管怎么说，这就是本章研究的主要对象，布尔巴基学派为这种混沌未开的结构起名岩浆（le magma）[^1]，所以接下来我们要做的是让它逐级“冷却”。

[^1]: 李文威《代数学方法 第一卷：基本架构》，98