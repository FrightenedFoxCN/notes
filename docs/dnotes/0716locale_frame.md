# 用格论研究拓扑空间：Locale and Frame

今天我们接着往 Stone 对偶进发，这里要引入的是宇象（locale）和宙象（frame）[^1]的概念，顺便回顾一下拓扑空间的各种东西。当然，这些翻译都是笔者编的，如果有标准翻译还请告知。主要的参考资料来自于 Johnstone 的 *Stone Spaces* 、 [Picado 的 *Frames and Locales*](https://link.springer.com/book/10.1007/978-3-0348-0154-6) 和 [P. Taylor 的论文](http://www.paultaylor.eu/ASD/sobsc/sobsc.pdf)。

[^1]: 为什么这么翻译？因为 locale 事实上抽象了 space 的概念，自然地就带有空间性，frame 与之对偶，这个概念本意也带点时间因素。另外，出于与一些奇怪的翻译统一的心态（anima 心象，topos 意象），就有了这样一个奇怪的翻译。

第一个问题是：什么是拓扑空间？一个点集，以及它的一个满足一些性质的开集族，这是一般的定义。但是，这个点集真的是必须的吗？我们当然会发现，似乎开性才是最根本的东西，我们在上面定义连续性、层等等东西。因此，我们产生了研究无点拓扑（pointless topology）的动机，而宇象和宙象的概念就是在这样的研究中产生的。

首先，考虑拓扑空间的定义。开集族的要求包含任意并和有限交，它当然是一个分配格，其上的偏序关系就是集合的属于关系，我们将其记作 $\Omega(X)$。它是完备的，且具备无限项的分配律。因此，我们首先写出宙象的定义：

\definition
    宙象（frame）范畴（$\mathsf{Frm}$）的对象是满足无限项的分配律的完备格，其上的态射为保有限交和任意并的函数。

宇象的定义与之对偶：

\definition
    宇象（locale）范畴 $\mathsf{Loc} = \mathsf{Frm}^\mathrm{op}$。

为什么需要用对偶的方式定义？注意连续性的定义中，我们用一个映射的**逆映射**将开集映到开集。因此，这里的定义也就变得直观了。

上面的 $\Omega: \mathsf{Top} \to \mathsf{Loc}$ 的函子性是显见的。

当然，我们的宇象定义的范围似乎要比拓扑空间广，它上面只考虑了开集的问题而没有考虑点的问题。下面我们要想，怎么从这样的定义中把点恢复出来。

不妨先反思一下，一个点到底是个什么东西？我们会先想象一个很小片的区域，然后变小、再变小。于是，这就给出了一个比较直观的定义：

\definition
    一个宙象（宇象）$L$ 中的点就是其中的一个完备素滤子。将它们的集合记作 $\mathrm{pt}(L)$。

好吧，这直观吗？不一定。为了理解这个定义，我们需要先把几个概念理一下，然后引入一点跟拓扑空间相关的观察。

\definition
    一个格 $L$ 中的滤子（filter）$F$ 就是它的序理想的对偶，也就是说，它是一个满足以下条件的非空子集：

    1. 如果 $A \leqslant B, A \in F$ 则 $B \in F$；
    2. 如果 $A \in F, B \in F$ 则存在 $C \in F$ 满足 $C \leqslant A, C \leqslant B$。

    一个滤子 $F$ 是素的（prime），如果 $\perp \not \in F$ 且 $x \vee y \in F \implies x \in F \ \mathrm{or}\ y \in F$。

    它是完备素的（completely prime）如果上面定义里的并被改写成任意并：任意指标集 $I$，$\vee_{i \in I} x_i \in F \implies \exists k \in I, x_k \in F$。

以下观察是自然的：

\proposition
    一个点 $x$ 的所有开邻域构成的集合 $\mathcal U(x) = \{U: x \in U\}$ 是一个完备素滤子。

下面我们来处理一点跟拓扑空间相关的观察。鉴于上面提到的动机，我们希望由 $\Omega(X)$ 能够唯一确定其中的点。对此，我们先给出 Grothendieck 应用闭集写就的定义：

\definition
    一个拓扑空间被称为素净的（sober），如果对于其中的任意并不可约的闭子集 $A$，都存在唯一 $x \in X$ 使得 $A = \overline{\{x\}}$。

下面的命题将证实我们前面对点的定义：

\proposition
    一个拓扑空间 $X$ 是素净的，当且仅当所有的完备素滤子都是形如 $\mathcal U(x)$ 的集合。

\proof
    我们首先要对素净性（sobriety）的定义做一点改写，取其对偶命题：任意交不可约的开子集 $U$，都存在唯一 $x \in X$ 使得 $U = X \setminus \overline{\{x\}}$。

    先证 $\Rightarrow$ 方向。设 $X$ 是素净的，$\mathcal F$ 为 $\Omega(X)$ 中的完备素滤子，那么 $W = \cup\{U \in \Omega(X): U \not \in \mathcal F\}$ 是交不可约的。为了看出这点，我们只要注意到 $W$ 的补恰为 $\mathcal F$ 的交在 $\mathcal F$ 中，而$\mathcal F$ 是完备素的即可。这样，我们就能由素净性得到 $W = X \setminus \overline{\{x\}}$。因此，我们就得到 $U \not \in F \iff U \subseteq W \iff x \not \in U$。因此 $\mathcal F = \mathcal U(x)$。

    接下来证 $\Leftarrow$ 方向。如果 $X$ 不是素净的，那么存在一个 $W$ 为交不可约的开集，不能表为形如 $X \setminus \overline{\{x\}}$ 的形式。设 $\mathcal F = \{U \in \Omega(X): U \not\subseteq W\}$。这是一个完备素滤子但是 $\mathcal F$ 并不是形如 $\mathcal U(x)$ 的集族。

这个命题往往比对素净性原来的定义更好用，因此后面我们不妨将其作为对素净性的定义。再反思一下，这样一个性质事实上表明，我们之前对点的定义就等价于定义了以它为中心的一串开集族为宇象中的点，这就是那个“越来越小”的直觉的用武之地。

当然，既然对拓扑空间给出了素净性的限制，那么我们不妨稍微讨论一下这个限制有多强。下面两个命题在此不做证明，但它们能够给出关于其限制的一个直观理解：

\proposition
    任一素净的拓扑空间都是 $T_0$ 的。

\proposition
    任一 Hausdorff 空间都是素净的。[^2]

[^2]: 需要用到排中律。

当然，这样的限制自然引发了下面的结果：

\lemma
    任意宇象 $L$，$\mathrm{pt}(L)$ 都是素净的。

还可以注意到，$\mathrm{pt}$ 是具备函子性的，而且很舒服的是，它是 $\Omega$ 的右伴随。

本来打算再补点啥的，比如用单子性定义素净性，但是既然都这个点了，想想再展开讲什么东西都会变得很长，而且要用到不少范畴语义不补充又有悖本系列的精神，那就摸了，争取明天先写范畴语义好了（遁）。