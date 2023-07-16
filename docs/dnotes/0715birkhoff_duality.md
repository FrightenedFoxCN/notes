---
comments: true
---

# 格论和 Birkhoff 对偶

这几天的内容大概是整理一些对偶性相关的东西。今天的目标是回顾一下格论的基本定义，搞定 Birkhoff 对偶。本来打算再用 Birkhoff 对偶的方式引出 Heyting 代数，但是因为余代数的方法足以再水一篇就放弃了（逃）。主要参考资料是 [John Harding 的课件](https://wordpress.nmsu.edu/hardingj/files/2019/10/ESSLLI3.pdf)、[Gavin C. Wraith 的论文](http://archive.numdam.org/item/CTGDC_1993__34_4_259_0.pdf) 和 R. Stanley 的 *Enumerative Combinatorics Vol. 1*。

首先，不妨回顾一下格论的基本概念。这个部分我们将一笔带过。

\definition
    一个偏序集（partially ordered set, poset）是一个带有二元关系 $\leqslant$ 的集合 $P$，且这个二元关系居有自反性、反对称性和传递性。

\definition
    对于 $A \subseteq P$：

    - $x$ 在 $A$ 中是极大的（maximal），如果 $x \in A$，且不存在 $y \in A$ 满足 $x < y$；
    - $x$ 在 $A$ 中是最大元（maximum），如果 $x \in A$，且 $\forall y \in A, y \leqslant A$；
    - 极小、最小可以被对偶地定义；
    - $A$ 的上界（upper bound）$U(A) = \{u: \forall x \in A, x \leqslant u\}$；
    - $A$ 的下界（lower bound）$U(A) = \{v: \forall x \in A, v \leqslant x\}$；
    - 最小上界（least upper bound） $\vee A$ 为 $U(A)$ 的最小元，最大下界（greatest lower bound） $\wedge A$ 为 $L(A)$ 的最大元。
    - 称一个偏序集有界（bounded），如果 $P$ 有最大、最小元，分别记作 $\top$ 和 $\perp$。

\definition
    如果偏序集 $L$ 的任何一个双元素子集 $\{a, b\}$ 都有一个最小上界（记作 $a \vee b$，称为 $a$ 和 $b$ 的并，join）和一个最大下界（记作 $a \wedge b$，称为 $a$ 和 $b$ 的交，meet），则称这个偏序集是一个格（lattice）。

我们这里避开泛代数的概念，但是不妨注意到这个结构 $(L, \wedge, \vee)$ 确实是一个代数，满足以下性质：

\proposition
    对于任意格，以下性质成立：
    
    1. 幂等性：$x \wedge x = x \vee x = x$；
    2. 交换律：$x \wedge y = y \wedge x$，$x \vee y = y \vee x$；
    3. 结合律：$(x \wedge y ) \wedge z = x \wedge (y \wedge z)$，$(x \vee y) \vee z = x \vee (y \vee z)$；
    4. 吸收律：$x \wedge (x \vee y) = x = x \vee (x \wedge y)$

当然，也可以证明满足这四条性质的代数结构上一定能定义偏序，只需倒过来验证即可。用代数的语言当然可以定义格同态和子格的概念，在此不做详述。我们称一个格同态是有界的（bounded），如果它保极大、极小元。

\definition
    如果一个格 $L$ 满足以下性质，那么就称其为一个分配格（distributive lattice）：

    $$
    \forall x, y, z \in L, x \vee (y \wedge z) = (x \vee y) \wedge (x \vee z), x \wedge (y \vee z) = (x \wedge y) \vee (x \wedge z)
    $$

注意，如果将等号改成不等号，那么在任意格中，这两个等式各在一个方向上成立。因此定义中的等号约束事实上也只需要一半就能完成。

注意到，可以由一个偏序集去构造分配格。我们首先考虑偏序集的理想：

\definition
    一个偏序集的 $P$ 序理想（order ideal）[^1]是集合 $I \subseteq P$ 满足：

    $$
    \forall t \in I, s \leqslant t \implies s \in I
    $$

[^1]: 格论的术语往往非常麻烦，序理想又称 semi-ideal / down-set / decreasing subset，这里取了一个比较明白的翻译。

下面这个命题是极好验证的：

\proposition
    一个偏序集 $P$ 的全体序理想构成分配格 $D(P)$。其中的 $\vee$ 和 $\wedge$ 分别对应集合的并与交，偏序关系就是属于关系。

\proof
    验证序理想的交和并仍为序理想即可。

类似的采一个子集构成分配格的方式非常常见。类比环论中的理想，我们也可以定义出主序理想：

\definition
    称 $\downarrow t = \{s \in P: s \leqslant t\}$ 为由 $t$ 生成的主序理想。

这个定义并不想它看起来那么随意。序理想的含义在 Hasse 图中可以看的更清晰，它就是“取一族元素下面所有能构建偏序关系的元素构成集合”，这些元素可被视作生成元（事实上，它们就是 $I$ 上的极大元）。而当极大元唯一时，就产生了主序理想，这与环论中的定义是完全一致的。

对 Birkhoff 对偶性[^2]的描述事实上非常简单：

[^2]: 或者叫 Birkhoff 表示定理、有限分配格基本定理。

\theorem
    设 $L$ 为一有限分配格，则存在一个在同构意义下唯一的偏序集 $P$ 满足 $L \cong D(P)$。

为了证明这个结果，我们需要做的就是构造这样一个 $P$。为此，我们考虑并不可约元（join-irreducible）：

\definition
    称格 $L$ 中的元素 $s$ 并不可约，如果 $s \neq \perp$ 且 $s = t \vee u \implies t = s \ \mathrm{or}\ u = s$。记 $L$ 中所有并不可约元的集合为 $J(L)$。[^3]

[^3]: 这里不能为最小元是出于技术性的需要，见下面的直觉描述。

很显然，一个元素是交不可约元就意味着正好有一个元素在它下面紧挨着它。从 Hasse 图上看，就是它往下只能连出一根表示偏序关系的线。这样的元素当然能够构成偏序集，只要继承原来的偏序关系即可。循着这种直觉，我们很容易发现：

\proposition
    $D(P)$ 中的并不可约元就是主序理想。

而主序理想与偏序集的元素一一对应，也就是说：

\lemma
    $$
    J(D(P)) \cong P
    $$

    这个同构是保序关系的。

利用这样的一一对应，当然也可以有：：

\lemma
    $$
    D(J(L)) \cong L
    $$

    这是一个格同构。

\proof
    定义同构 $L \to D(J(L)): x \mapsto \{s \in J(L): s \leqslant x\}$ 即可。

这两个结果事实上相当漂亮。为了看出其对偶性的核心，我们不妨用范畴的语言表述一下。记有限偏序集和保序映射构成的范畴为 $\mathsf{FPos}$，有限分配格和有界格同态构成的范畴为 $\mathsf{FDistLat}$，则 $J: \mathsf{FDistLat} \to \mathsf{FPos}$ 和 $D: \mathsf{FPos} \to \mathsf{FDistLat}$ 的函子性是显见的。上面的两个结果分别构建了 $D \circ J$ 和 $J \circ D$ 到 $\mathrm{id}$ 的自然变换，也就是说，我们表明这两个函子是双侧互伴的。