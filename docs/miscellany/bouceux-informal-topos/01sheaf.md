---
comments: True
---

# 第一讲 层拓扑斯

## 1.1 拓扑空间上的层

在微积分课上，我们的研究对象就是 $\mathcal{C}(\R, \R)$，实数域上的连续函数，比如 $x$，$x^2$，$\sin x$，$e^x$ 等等。当然，那些并非在整个 $\R$ 上有定义的函数也不会被直接无视，比方说 $\log x$ 和 $\sqrt x$，分别在 $]0, \infty[$ 和 $[0, \infty[$ 有定义。当然咯，如果我们把它看成，比方说对于 $\sqrt x$，在拓扑空间 $[0, \infty[$ 上定义的函数，那么连续函数的拓扑定义不会带来任何问题……但是，如果考虑其为一个 $\R$ 上的偏函数（partial function），则在 $0$ 点处的连续与其它地方就大不相同了，因为它在任意一个 $0$ 的邻域内都有地方未定义。

层论方法的则稍有不同：在给定点处，层专注于那些在其邻域中成立的性质。比方说被视作 $\R$ 上的偏函数的 $\log x$ 和 $\sqrt x$，它们在所有 $x > 0$ 的邻域内处都有定义，而且连续，但在 $0$ 的邻域内则未必。当然，不失一般性地，我们只需要考虑开邻域。由此，我们的实值连续函数层 $\mathcal C(-, \R)$ 的定义需要说明，对于 $\R$ 的任意开子集 $U$，$\mathcal C(U, \R)$ 这个集合长什么样。当然，当 $V \subseteq U$ 是一个更小的开子集时，任意函数 $f \in \mathcal C(U, \R)$ 都可以被限制下来得到到 $f\vert_V \in \mathcal C(V, \R)$。将 $\R$ 的开子集构成的格记作 $\mathcal O(\R)$，则我们有一个反变函子（contravariant functor）将其打到集合范畴上：

$$
\mathcal C(-, \R): \mathcal O(\R) \to \mathsf{Set}, U \mapsto \mathcal C(U, \R)
$$

接下来，给定两个开子集 $U, V$ 和连续函数 $f: U \to \R, g: V \to \R$，它们在 $U \cap V$ 上取值完全相等，那么我们就能把它们“胶合”起来得到一个 $U \cup V$ 上的连续函数。当然，取定一族连续函数 $f_i: U_i \to \R$ 也有类似的结果，不一定只能是两个。因此，我们的连续函数层满足以下性质：

> 给定开子集 $U = \bigcup_{i \in I} U_i$ 和连续函数 $f_i \in \mathcal C(U_i, \R)$，如果对于任意指标 $i, j$ 都有 $f_i \vert_{U_i \cap U_j} = f_j \vert_{U_i \cap U_j}$，则存在一个唯一的 $f \in \mathcal C(U, \R)$ 使得 $\forall i, f \vert_{U_i} = f_i$。

!!! info "定义 1.1"
    选定拓扑空间 $X$，记其开子集构成的格为 $\mathcal O(X)$。$X$ 上的一个预层（presheaf） $F$ 是一个反变函子 $F: \mathcal O(X) \to \mathsf{Set}$。$\mathcal O(X)$ 中的态射 $V \subseteq U$ 在函子的作用下被映为：

    $$
    F(U) \to F(V), a \mapsto a \vert_V
    $$

    $X$ 上的一个层（sheaf）是满足以下公理的预层：

    给定 $\mathcal O(X)$ 中的集合 $U = \bigcup_{i \in I} U_i$ 和 $a_i \in F(U_i)$，如果对于任意指标 $i, j$ 都有 $a_i \vert_{U_i \cap U_j} = a_j \vert_{U_i \cap U_j}$，则存在一个唯一的 $a \in F(U)$ 使得 $\forall i, a \vert_{U_i} = a_i$。

    预层或者层之间的态射无非就是函子间的自然变换，拓扑空间上的层范畴被称为空性拓扑斯（spatial topos）。

!!! info "例 1.2"
    以下均为层的例子：

    1. 给定自然数 $k$，函子

    $$
    \mathcal O(\R) \to \mathsf{Set}, U \mapsto \mathcal C^k(U, \R)
    $$

    将开子集 $U$ 映到 $k$-阶连续函数集。

    2. 给定拓扑空间 $X$ 和 $Y$，函子

    $$
    \mathcal O(X) \to \mathsf{Set}, U \mapsto \mathcal C(U, Y)
    $$

    将开子集 $U$ 映到 $X$ 到 $Y$ 的连续映射的集合。

    3. 给定连续映射 $p: Y \to X$，函子

    $$
    \mathcal O(X) \to \mathsf{Set}, U \mapsto \mathsf S(U, Y) = \{s \mid s \in \mathcal C(U, Y, p \circ s = \mathsf{id}_U)\}
    $$

    将开集 $U$ 映到 $p$ 在 $U$ 上的连续截影（section）的集合。

!!! info "拓展阅读"
    例 1.2.3 看起来似乎有点普遍，参见 [4] 的 2.4, 2.5 和 2.6 节。更准确地说，给定拓扑空间 $X$ 上的一个层 $F$，对于任意 $x \in X$ 考虑所谓的 $F$ 在 $x$ 处的茎（stalk）：

    $$
    F_x = \mathop{\mathrm{colim}}\limits_{U \ni x} F(U), U \in \mathcal O(X)
    $$

    这是一个滤过极限（filtered colimit）。将 $Y$ 定义为这些茎的无交并，然后在 $Y$ 上对所有映射 $\sigma_a^U$ 置最终的拓扑：

    $$
    \sigma_a^U: U \to Y; x \mapsto [a] \in F_x
    $$

    $U$ 取遍 $\mathcal O(X)$，$a$ 取遍 $F(U)$。此时平凡的投影 $p: Y \to X$ 就是一个平展映射（étale mapping），即一个连续函数，满足对于任意点 $y \in Y$，存在 $y$ 和 $p(y)$ 的邻域，使得 $p$ 限制在上面是一个同胚。这时，我们一开始定义的层就同构于 $p$ 的连续截影层。进一步地，这也就给出了一个 $X$ 上的层到 $X$ 上的平展映射的对应关系。

## 1.2 宇象上的层

定义 1.1 表明，拓扑空间上的层只依赖于对应的子对象的格。那么，可以很自然地想到把这个定义推广到一个任意的完备格（complete lattice）上去：我们要求完备是因为拓扑空间上的层的定义要求有覆盖 $U = \bigcup_{i \in I} U_i$。但是完备性并不足够，因为层论同时也要用上往子集 $V \subseteq U$ 上的限制。在拓扑空间中，给定覆盖 $U = \bigcup_{i \in I} U_i$ 和开子集 $V \subseteq U$，我们得到：

$$
V \cap U = V \cap \bigcup_{i \in I} U_i = \bigcup_{i \in I}(V \cap U_i)
$$

所以，$U$ 的覆盖可以被限制成为 $V \cap U = V$ 的覆盖。这种美好的性质在层论的发展中至关重要。

因此，我们写下以下定义：

!!! info "定义 1.3"
    一个宇象（locale）是一个完备格，且其中有限交对任意并分配。

定义中的条件写出来就是，对于宇象中的任意元素

$$
u \wedge \bigvee\limits_{i \in I} v_i = \bigvee\limits_{i \in I}(u \wedge v_i)
$$

注意，宇象有顶元素（top element）$1$（所有元素的并）和底元素（bottom element）$0$（空子集中的元素的并）。它也有包含任意元素的交（所有下界的并），但这没啥意思，因为宇象中的极小值（infimum）没什么相关的性质。在拓扑空间的情形中，这样的极小值是交集的内部。

当然我们定义：

!!! info "定义 1.4"
    选定宇象 $L$。$L$ 上的一个预层（presheaf） $F$ 是一个反变函子 $F: L \to \mathsf{Set}$。$L$ 中的态射 $v \leqslant$ 在函子的作用下被映为：

    $$
    F(u) \to F(v), a \mapsto a \vert_V
    $$

    $L$ 上的一个层（sheaf）是满足以下公理的预层：

    给定 $L$ 中的元素 $u = \bigvee_{i \in I} u_i$ 和 $a_i \in F(u_i)$，如果对于任意指标 $i, j$ 都有 $a_i \vert_{u_i \wedge u_j} = a_j \vert_{u_i \wedge u_j}$，则存在一个唯一的 $a \in F(u)$ 使得 $\forall i, a \vert_{U_i} = a_i$。

    预层或者层之间的态射无非就是函子间的自然变换，宇象上的层范畴被称为宇性拓扑斯（localic topos）。

定义 1.4 中取的元素族被称为覆盖 $u = \bigvee_{i \in I} u_i$ 上的相容元素族；$a \in F(u)$ 被称为这个族的胶合（gluing）。因此，宇象上的层无非是拓扑空间上的层的推广。

我们需要强调以下性质：

!!! success "定理 1.5"
    任一宇象都是笛卡尔闭范畴（Cartesian closed category）[^1]。

[^1]: 一个范畴被称为笛卡尔闭的，如果它有有限积，且任意函子 $- \times B$ 都有右伴随。——原注

\proof
    考虑宇象 $L$ 中的三个元素 $u, v, w$。置：

    $$
    (v \implies w) = \bigvee\{x \in L \mid x \wedge v \leqslant w\}
    $$

    随即可知

    $$
    (u \wedge v) \leqslant w \mathop{\mathsf{iff}} u \leqslant (v \implies w) 
    $$

    而 $u \wedge v$ 是范畴 $L$ 中 $u$ 和 $v$ 的积。因此我们发现函子 $(- \wedge v)$ 的右伴随不外乎 $(v \implies -)$。

至于为什么要用 $v \implies w$ 这样的记号，考虑带离散拓扑的集合 $A$，给定其开子集构成的宇象 $\wp(A)$ 中的元素 $V, W$，我们有：

\begin{aligned}
(V \implies W) &= \{a \in A \mid \{a\} \subseteq (V \implies W)\}\\
&= \{a \in A \mid \{a\} \cap V \subseteq W\}\\
&= \{a \in A \mid a \in V \mathop\mathsf{implies} a \in W\}
\end{aligned}

所以这样的记号是非常正当的。

!!! success "推论 1.6"
    给定宇象 $L$ 中的元素 $u$，元素 $\lnot u = (u \implies 0)$ 是其中最大的与 $u$ 的交为 $0$ 的元素。它被成为 $u$ 的伪补（pseudo-complement）。

!!! info "例 1.7"
    任意完备布尔代数都是一个宇象。

\proof
    一个布尔代数是一个分配格。给定布尔代数 $B$ 中的三个元素 $u, v, w$，都有

    $$
    (u \wedge v) \leqslant w \mathop\mathsf{iff} u \leqslant (\complement v \vee w)
    $$

    这表明函子 $- \wedge v: B \to B$ 有右伴随 $\complement v \vee -$，因此也保虽有的并。

因此，在一个完备的布尔代数中，$(v \implies w) = \complement v \vee w$，而且 $\lnot u = \complement u$。

!!! info "拓展阅读"
    在拓扑空间中，如果一个开子集是其闭包的内部，我们就称它是正则的（regular）。正则的开子集组成了一个完备布尔代数，其中一族元素的并就是对应集族的并的闭包的内部，有限交就是集合的交。拓扑空间的正则开子集构成的宇象通常并不同构于开子集构成的宇象，在 [3] 的 1.8.10.d 中可以看见，$\R$ 就已经是一个反例了。因此，宇性拓扑斯比空性拓扑斯更普遍。

## 1.3 拓扑斯的两个基本性质

