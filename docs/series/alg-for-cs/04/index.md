---
comments: true
---

# 范畴论：一些抽象废话

!!! info "本章介绍"
    在前几章的铺垫之后，有心的读者可能已经发现了以下事实：

    1. 各种结构具备大量相同的构造，例如“自由”的构造、局部化的构造。
    2. 泛性质的描述是普遍的，例如商映射等等。
    3. 不同的结构具备相同的、普遍成立的性质，例如 Jordan-Hölder 定理和 Krull-Schmidt 定理等。
    4. 结构之间存在联系，例如 Galois 理论向我们呈现的域扩张与群的关系。
    5. 代数和拓扑之间存在广泛的联系，比如，拓扑空间具备基本群。

    本章将展现一套范畴论语言用以描述这些现象，与此同时，将前面几章的内容进行普遍的重述以应用这种语言。这一章的内容主要包括：

    1. 范畴论的基本概念介绍。
    2. 应用范畴论描述各种上述事实，并给出更广泛的解释。
    3. 讨论范畴、类型、逻辑的关联。
    4. 介绍范畴论的一些“定理”，并讨论一些编程中会用到的性质和范式。
    5. 讨论一些特定范畴的结构，例如 Abel 范畴，三角范畴等。

标题中的“抽象废话”事实上是范畴论的发明人之一（大概是 Steenrod？）的自嘲。当我们剥离结构本身的内容而注重结构与结构之间的联系时，自然而然地就得到了范畴的框架，这也就是前面一直在使用的交换图的框架。但是，这套语言的真正成形是为了书写所谓的自然性（naturality）。事实上，与平时所谓的范畴、函子、自然变换的顺序不同，自然变换构成了范畴论历史意义上的动机。当然，时至今日再去重写这套体系，已经少有人会提“抽象废话”这样的批评。所以不妨让我们在动机不足的情况下直接出发，暂且视其为一个独立学科对其进行探讨，在探讨的过程中再去展现其与已有构造的联系。毕竟，比起发明者的视角，这样的视角可能更为自然。

另一位发明人（大约是 MacLane）说，范畴论是没有什么属于自己的大定理的。到了现在，这种论断已经不是那么有效了。它已经脱离了元语言的范畴而形成了自己的方法和视角，从几乎必备的 Yoneda 引理到 Beck 单子性定理、Isbell 对偶、密度定理和臭名昭著的 Freyd-Mitchell 嵌入定理，这些结果使得它本身足以成为一个单独研究分支。因此，本章也会探讨这些更加“自足”的内容并且给出更广泛的解读。

另外，在前言中已经提及了 Haskell 对范畴论语言的偏爱。因此，我们也会对范畴论和编程语言的关系进行解读。这需要引入一些类型论的说法以及范畴语义，它最终会导向对单子性（主要是特殊的一些单子）的偏爱以及一些特殊的编程范式。

范畴论到如今不过百年，尚且出于发展阶段，故而笔者也只能盲人摸象，展现其某些特定的方面，以希求读者窥一斑以见全豹，不尽之处与错误之处亦在所难免，希望有识之士指出和补充。这里，只得引用 P. Johnstone 的一段话聊以自慰：

> 在 1993 年初，我发现我面临着选择：要么放弃这个项目，要么找人合作，或者独自背下书写这整本书的重担。第一种选择并不吸引人，因为这意味着放弃已经完成的大量材料；第二种选择则因为我难以找到合适的合作者而告吹。因此，我决定采用第三种方式，尽管这可能是一次长达数年的长征。（Peter T. Johnstone, *Sketches of an Elephant: A Topos Theory Compendium*, Preface, "One blind man", page xi）