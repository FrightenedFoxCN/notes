# 使用 Rust 语言的 Vulkan 教程

在这里，我们将使用 Rust 作为主要的编程语言开始对 Vulkan API ([Home | Vulkan | Cross platform 3D Graphics](https://www.vulkan.org/)) 的介绍。当然，许多其他语言都是可用的，例如更古老的 C++ + OpenGL/Vulkan 等等， Python + ModernGL 也是一个非常常见且易学的组合。这里之所以使用 Rust 是因为我喜欢，而且它的许多语言特性使得我们可以更少被语言本身的表达方式所限制，同时减少出错的可能。关于 Rust 的资料不多，可供参考的有 [The Rust Programming Language - The Rust Programming Language (rust-lang.org)](https://doc.rust-lang.org/book/title-page.html) 以及 [CS 110L: Safety in Systems Programming (stanford.edu)](https://web.stanford.edu/class/cs110l/) 等。在前几篇文章中，我们将首先使用 Vulkano 库 ([vulkano - Rust (docs.rs)](https://docs.rs/vulkano/0.32.3/vulkano/index.html)) 来引入对基本流程的介绍，并且完成两个小例子作为开胃小菜。然后，我们将从 Vulkano 库深挖下去，一方面分析它的原始代码，另一方面尝试引入更多图形学的概念来实现更加复杂的任务。前者更加偏向于底层架构，而后者更加偏向于上层的代码实现。

接下来，我们将假定读者已经对 Rust 的基础语法有所了解，并且已经完成了对 Vulkan SDK 的安装。我们使用的 rustc 版本为 1.66.2，Vulkano 版本为 0.32.3，Vulkan SDK 版本为 1.3.236，均为笔者写作时的最新版本。

???+ warning 
    作者也是初学者，所以出现错误在所难免，希望大家在看的过程中多参考其他资料，如果发现错误，敬请指正！另外，本文中涉及的专有名词很多事实上没有官方的翻译，看个乐就行，重要的地方应该都已经注上英文了。

下面是我们的主要流程，源于 [Understanding Vulkan® Objects - GPUOpen](https://gpuopen.com/learn/understanding-vulkan-objects/)。

<p align="center"><img src="overview_full.png" width="300" /></p>