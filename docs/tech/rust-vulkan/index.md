---
comments: true
---

# 使用 Rust 语言的 Vulkan 教程

在这里，我们将使用 Rust 作为主要的编程语言开始对 Vulkan API ([Home | Vulkan | Cross platform 3D Graphics](https://www.vulkan.org/)) 的介绍。当然，许多其他语言都是可用的，例如更古老的 C++ + OpenGL/Vulkan 等等， Python + ModernGL 也是一个非常常见且易学的组合。这里之所以使用 Rust 是因为我喜欢，而且它的许多语言特性使得我们可以更少被语言本身的表达方式所限制，同时减少出错的可能。关于 Rust 最具参考价值的是 [The Rust Programming Language - The Rust Programming Language (rust-lang.org)](https://doc.rust-lang.org/book/title-page.html) 以及 [CS 110L: Safety in Systems Programming (stanford.edu)](https://web.stanford.edu/class/cs110l/) 等。在前几篇文章中，我们将首先使用 Vulkano 库 ([About Vulkano](https://vulkano.rs)) 来引入对基本流程的介绍，并且完成两个小例子作为开胃小菜。然后，我们将从 Vulkano 库深挖下去，一方面分析它的原始代码，另一方面尝试引入更多图形学的概念来实现更加复杂的任务。前者更加偏向于底层架构，而后者更加偏向于上层的代码实现。

接下来，我们将假定读者已经对 Rust 的基础语法有所了解，并且已经完成了对 Vulkan SDK 的安装。我们使用的 rustc 版本为 1.92.2，Vulkano 版本为 0.34.3，Vulkan SDK 版本为 1.4.335，均为笔者写作时的最新版本。

下面是我们的主要流程，源于 [Understanding Vulkan® Objects - GPUOpen](https://gpuopen.com/learn/understanding-vulkan-objects/)。

<p align="center"><img src="overview_full.png" width="300" /></p>
