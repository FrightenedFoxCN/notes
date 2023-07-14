---
comments: true
---

# 单子论和 Beck 单子性定理

本节是在看 Abstract Stone Duality 的时候想到来补个课的，主要内容来自于李文威老师的《代数学方法》。

\definition
    幺半范畴（monoidal category）意指一组资料 $(\mathcal V, \otimes, a, 1, \iota)$，其中 $\mathcal V$ 为一个范畴，$\otimes$ 为双函子，$a(X, Y, Z): (X \otimes Y) \otimes Z \stackrel{\sim}{\to} X \otimes (Y \otimes Z)$ 被称为结合约束，$1 \in \mathcal V$ 为幺元，$\iota: 1 \otimes 1 \stackrel{\sim}{\to} 1$ 是对应的约束。我们要求，结合约束满足以下所谓 MacLane 五角形公理：

    \tikzcd
         & ((X \otimes Y) \otimes Z) \otimes W \arrow{ddl}[swap]{a(X, Y, Z) \otimes \mathrm{id}_W} \arrow{ddr}{a(X \otimes Y, Z, W)} & \\\\
         (X \otimes (Y \otimes Z)) \otimes W \arrow{dd}[swap]{a(X, Y \otimes Z, W)} & & (X \otimes Y) \otimes (Z \otimes W) \arrow{dd}{a(X, Y, Z \otimes W)}\\\\
         X \otimes ((Y \otimes Z) \otimes W) \arrow{rr}{\mathrm{id}_X \otimes a(Y, Z, W)} & & X \otimes (Y \otimes (Z \otimes W))

注意，这里所谓的 MacLane 五角形公理不过是为了使得结合约束可以反复套用的相容性条件。结合约束和幺元的约束事实上表明了“同构”与“相等”在范畴论的意义上是有显著差异的。

一个典型的例子是自函子范畴 $\mathcal C^{\mathcal C}$，其中的双函子（“乘法”）是函子的合成运算，幺元是恒等函子。而为了定义单子，我们需要将代数的概念推广到幺半范畴上：

\definition
    幺半范畴 $\mathcal V$ 上的代数指资料 $(A, \mu, \eta)$，其中 $A \in \mathcal V$，$\mu = \mu_A: A \otimes A \to A$，$\eta = \eta_A: 1 \to A$，使得下列图表交换：

    \tikzcd
        1 \otimes A \arrow{r}{\eta \otimes \mathrm{id}} \arrow{rd}[swap]{\sim} & A \otimes A \arrow{d}{\mu} & A \otimes 1 \arrow{l}[swap]{\mathrm{id}\otimes \eta} \arrow{ld}{\sim} & (A \otimes A) \otimes A \arrow{rr}{a(A, A, A)}[swap]{\sim} \arrow{d}{\mu \otimes \mathrm{id}} & & A \otimes (A \otimes A) \arrow{d}{\mathrm{id} \otimes \mu} \\
        & A & & A \otimes A \arrow{r}[swap]{\mu} & A & A \otimes A \arrow{l}{\mu}

    其中的 $\mu$ 可视作乘法运算，$\eta$ 可视作幺元。因为它要求乘法结合律和幺元，有的地方也将其称为幺半群。

\definition
    范畴 $\mathcal C$ 上的单子（monad）无非是幺半范畴 $\mathcal C^{\mathcal C}$ 上的代数；对偶地，$\mathcal C^{\mathrm{op}}$ 上的单子称为 $\mathcal C$ 上的余单子（comonad）。

注意到函子范畴 $\mathcal C^{\mathcal C}$ 是一个严格的幺半范畴，因为结合律是严格的，所以不再需要结合约束，我们可以简单地将其翻译成以下定义：

\definition
    范畴 $\mathcal C$ 上的的单子是资料 $(T, \mu, \eta)$，其中 $T: \mathcal C \to \mathcal C$ 是函子，$\mu: T^2 \to T$ 和 $\eta: \mathrm{id}_\mathcal{C} \to T$ 是态射，使得下图交换：

    \tikzcd
        T \arrow{r}{\eta T} \arrow{rd}[swap]{\mathrm{id}} & T^2 \arrow{d}{\mu} & T \arrow{l}[swap]{T\eta} \arrow{ld}{\mathrm{id}} & T^3 \arrow{r}{\mu T} \arrow{d}[swap]{T\mu} & T^2 \arrow{d}{\mu} \\
        & T & & T^2 \arrow{r}[swap]{\mu} & T 

    余单子 $(L, \delta, \varepsilon)$ 的定义是对偶的。

注意到，伴随对和单子之间有如下关系：

\proposition
    考虑一对伴随函子：

    $$
    F: \mathcal C \rightleftarrows \mathcal D : G
    $$

    相应的单位 $\eta: \mathrm{id}_{\mathcal C} \to GF$ 和余单位 $\varepsilon: FG \to \mathrm{id}_{\mathcal D}$。则可定义 $\mathcal C$ 上的单子：

    $$
    (GF, [GFGF \stackrel{G\varepsilon F}{\rightarrow} GF], \eta)
    $$

    和 $\mathcal D$ 上的余单子：

    $$
    (FG, [FG \stackrel{F\eta G}{\rightarrow} FGFG], \varepsilon)
    $$

\proof
    简单验证即可。验证需要用到代数学方法卷一的引理 2.2.7。

回顾一下到此为止我们的定义。单子是自函子范畴上的代数，这就意味着单子事实上就是一个自函子，这个自函子作用在原来的范畴 $\mathcal C$ 上。所以，下面的思路，是要探讨在范畴 $\mathcal C$ 中在单子 $T$ 作用下的模。

\definition
    设 $(T, \mu, \eta)$ 为范畴 $\mathcal C$ 上的单子。则所谓 $T$-模指资料 $(M, a)$，其中 $M \in \mathcal C$，$a \in \mathrm{Hom}_{\mathcal C}(T(M), M)$ 使得下图交换：

    \tikzcd
        T^2(M) \arrow{r}{Ta} \arrow{d}[swap]{\mu_M} & T(M) \arrow{d}{a} & M \arrow{r}{\eta_M} \arrow{rd}[swap]{\mathrm{id}_M} & T(M) \arrow{d}{a}\\
        T(M) \arrow{r}{a} & M & & M

与一般的模类似地，它也能构成一个范畴。其中的态射定义不妨类比表示同态的定义方式：

\definition
    所有 $T$-模可以构成范畴 $\mathcal C^T$，其中的态射为 $\mathcal C$ 中使得下图交换的态射 $f: M \to M'$：

    \tikzcd
        T(M) \arrow{r}{a} \arrow{d}{Tf} & M \arrow{d}[swap]{f}\\
        T(M') \arrow{r}{a'} & M'

同理可以定义 $L$-余模，对应的 $L$-余模范畴记作 $\mathcal C^L$。当然，类似一般的模，也可以做自由函子和忘却函子。忘却函子 $U^T: \mathcal C^T \to \mathcal C$ 将对象 $(M, a)$ 映到 $M$，而自由函子的定义稍微复杂一点：

\definition
    设 $(T, \mu, \eta)$ 为 $\mathcal C$ 上的单子，定义函子 $\mathrm{Free}^T: \mathcal C \to \mathcal C^T$：

    $$
    \mathrm{Free}^T(M) = (T(M), [T^2(M) \to T(M)]), \quad \mathrm{Free}^T([M \to M']) = T(f): T(M) \to T(M')
    $$

验证它与 $U^T$ 伴随是容易的。注意到这个伴随对在 $\mathcal C$ 上确定的单子正好就是 $(T, \mu, \eta)$。对偶地，$\mathcal D$ 上的余单子也可以类似的给出伴随对。

考虑一个伴随对，应用函子的过程可以理解为一个“丢失信息”的过程。下面我们要考虑将函子拆成一个忘却函子和另一个函子：

\lemma
    考虑伴随对 $(F, G)$ 给出的单子 $T$ 和余单子 $L$。设 $N \in \mathcal D$，则可以定义资料
    
    $$
    (G(N), G\varepsilon_N: GFG(N) \to G(N)) \in \mathcal C^T
    $$

    于是给出函子 $\mathbb{K}: \mathcal D \to \mathcal C^T$ 满足 $G = U^T\mathbb K$。对偶地，$F$ 也可以被对偶地分解为 $U^L\mathbb K$

\proof
    简单验证交换性和函子性即可。

这样的分解的目标就在于，可以注意到结构是否只被忘却函子丢失。如果是如此的话，那么就可以通过单子或者余单子来重构过程中丢失的信息。于是下面的定义就显得理所应当了：

\definition
    考虑一对伴随函子 $F: \mathcal C \rightleftarrows \mathcal D: G$，以此定义 $\mathcal C$ 上的单子 $T$ 和 $\mathcal D$ 上的余单子 $L$。如果上面的引理构造的函子 $\mathbb{K}: \mathcal D \to \mathcal C^T$ 是一个范畴等价，那么称 $(F, G)$ 是单子的；如果对偶版本 $\mathbb{K}: \mathcal C \to \mathcal D^L$ 是范畴等价，那么称这个伴随对是余单子的。

接下来的 Beck 单子性定理（又称 Barr-Beck 定理）刻画了单子性。为了描述它，我们还要给出一点定义：

\definition
    称函子 $F$ 是保守的（conservative），如果态射 $f$ 为同构当且仅当态射 $Ff$ 为同构。

显然，保守函子是保余极限的。

\definition
    考虑下列图表使得实线部分交换：

    \tikzcd
        A \arrow[r, shift left, "u"] \arrow[r, shift right, swap, "v"] & B \arrow[l, dashed, bend left, "t"] \arrow[r, "h"] & Z \arrow[l, dashed, bend left, "s"]

    而且 $h$ 和 $v$ 各自有虚线所示的右逆 $s$ 和 $t$ 满足 $sh=ut \in \mathrm{End}(B)$。称词实线部分图为分裂叉（split fork）。

注意到这样的图表与余等化子的类似性。事实上，这样的分裂叉就已经给出了 $u$ 和 $v$ 在 $\mathcal C$ 中的余等化子。

\proposition
    如上图，$Z$ 就是 $f$ 和 $g$ 的余等化子。

\proof
    我们验证余等化子的泛性质。考虑如下图表：

    \tikzcd
        & & W \\
        A \arrow[r, shift left, "u"] \arrow[r, shift right, swap, "v"] & B \arrow[r, "h"] \arrow[ru, "k"] & Z \arrow[u, dashed, swap, "\varphi"] 

    如果存在 $\varphi$ 使得 $\varphi h = k$，则 $\varphi = \varphi hs = ks$。反过来，置 $\varphi = ks$，则 $\varphi h = ksh = kut = kvt = k$。

另外，分裂叉在任意函子下的像仍然是分裂叉，这是非常容易验证的。

\definition
    考虑函子 $G: \mathcal D \to \mathcal C$ 和 $\mathcal D$ 的一对态射 $f, g: X \rightrightarrows Y$，如果存在 $h: G(Y) \to Z$ 使得：

    \tikzcd
        G(X) \arrow[r, shift left, "Gf"] \arrow[r, shift right, swap, "Gg"] & G(Y) \arrow[r, "h"] & Z
    
    是 $\mathcal C$ 中的分裂叉，则称 $(f, g)$ 为 $\mathcal D$ 中的 $G$-分裂对。

一个分裂对使得 $(Gf, Gg)$ 有余等化子。那么，我们的问题是，能否将其提升为 $(f, g)$ 的余等化子，以及此种提升是否唯一。注意到，忘却函子 $U^T$ 是保守的。因此，下面这个引理很符合我们的直觉：

\lemma
    考虑 $\mathcal C$ 上的单子 $(T, \mu, \eta)$，则函子 $U^T$ 能够给出 $U^T$-分裂对的余等化子。

\proof
    考虑 $\mathcal C^T$ 中的一对态射 $u, v: (M, a) \rightrightarrows (M', a')$ 和 $\mathcal C$ 中的分裂叉：

    \tikzcd
        M \arrow[r, shift left, "u"] \arrow[r, shift right, swap, "v"] & M' \arrow[l, dashed, bend left, "t"] \arrow[r, "h"] & M'' \arrow[l, dashed, bend left, "s"]

    下面我们的问题只剩下了表明 $M''$ 可以唯一扩充为 $(M'', a'') \in \mathcal C^T$ 并且说明这给出了 $u$ 和 $v$ 在 $\mathcal C^T$ 中的余等化子。注意函子 $T$ 不影响分裂叉，$T$ 作用之后的结果 $T(M'')$ 仍然是余等化子，因此泛性质可以给出唯一的 $a''$。接下来，验证 $(M'', a'')$ 是 $T$-模，以及在 $\mathcal C^T$ 中验证余等化子的泛性质即可。

终于，我们可以描述 Beck 单子化定理：

\theorem
    设函子 $G: \mathcal D \to \mathcal C$ 有左伴随 $F$，以下陈述等价：

    1. 伴随对 $(F, G)$ 是单子的；
    2. $G$ 对所有 $G$-分裂对都给出相应的余等化子；
    3. $G$ 是保守的，而且所有 $G$-分裂对在 $\mathcal D$ 中都有余等化子。

    此时，$\mathbb K: \mathcal D \to \mathcal C^T$ 的一个拟逆函子 $\mathbb L$ 可以被描述为以下余等化子图表：

    \tikzcd
        FGF(M) \arrow[r, shift left, "Fa"] \arrow[r, shift right, swap, "\varepsilon_{FM}"] & F(M) \arrow[r] & \mathbb L(M, a)

    其中 $(M, a)$ 为一个 $\mathcal C$ 上的 $T$-模。

    对于余单子而言，判断完全是对偶的。

\proof
    由于 $G = U^T\mathbb K$，关于忘却函子的引理直接表明了 1 $\implies$ 2。由于 $U^T$ 保守，所以 $G$ 显然保守，2 $\implies$ 3 成立。3 $\implies$ 2 由保守函子保余极限的性质成立。2 $\implies$ 1 只需证明如上构造的拟逆成立即可。

下面这个引理给出了一个余等化子的构造：

\lemma
    设函子 $G: \mathcal D \to \mathcal C$ 有左伴随 $F$，并且 $G$ 对于所有 $G$-分裂对都能给出相应的余等化子，则下图给出余等化子：

    \tikzcd
        FGFG(N) \arrow[r, shift left, "FG\varepsilon_N"] \arrow[r, shift right, swap, "\varepsilon_{FG(N)}"] & FG(N) \arrow[r, "\varepsilon_N"] & N

    其中 $N \in \mathcal D$。

\proof
    对图表取 $G$，则我们得到一个取单子为 $\mathbb{K}(N)$ 的情形的分裂叉：

    \tikzcd
        GFGFG(N) \arrow[r, shift left, "GFG\varepsilon_N"]\arrow[-, double line with arrow={-,-}]{d} \arrow[r, shift right, swap, "G\varepsilon_{FG(N)}"] & GFG(N)\arrow[-, double line with arrow={-,-}]{d} \arrow[r, "G\varepsilon_N"] & G(N)\arrow[-, double line with arrow={-,-}]{d} \\
        GFGF(\mathbb K(N)) \arrow[r, shift left, "GF(G\varepsilon_N)"] \arrow[r, shift right, swap, "G\varepsilon_{FG(N)}"] & GF(\mathbb K(N)) \arrow[r, "G\varepsilon_N"] & \mathbb K(N) \arrow[-, double line with arrow={-,-}]{r} & (G(N), G\varepsilon_N)

    利用它给出余等化子即可。

应用这个引理和 Beck 单子性定理，得到推论：

\proposition
    若 $(F, G)$ 是单子的，那么图表：

    \tikzcd
        FGFG(N) \arrow[r, shift left, "FG\varepsilon_N"] \arrow[r, shift right, swap, "\varepsilon_{FG(N)}"] & FG(N) \arrow[r, "\varepsilon_N"] & N

    对所有 $N \in \mathcal D$ 都是余等化子。