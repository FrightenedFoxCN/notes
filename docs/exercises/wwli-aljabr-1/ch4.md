---
comments: true
---

1. 设 $S$ 为半群. 证明元素 $1 \in S$ 是幺元当且仅当 (i)  $1 \cdot 1 = 1$, (ii) $1$ 满足左, 右消去律. 读者不妨对照定义 3.1.1.

??? Solution
    若 $1$ 为幺元，则 $\forall x \in S, x \cdot 1 = 1 \cdot x = x$，因此 $1 \cdot 1 = 1$；映射 $x \mapsto 1\cdot x$ 和 $x \mapsto x \cdot 1$ 都是恒等映射，因此也都是单射，所以 $1$ 满足左右消去律。

    反之由第一条性质，$1 \cdot 1 = 1 \Rightarrow 1 \cdot 1 \cdot x = 1\cdot x$，再由左消去律得到 $1 \cdot x = x$；右侧同理可证。

2. 以泛性质解释命题 4.2.4 (见 $\text\S$2.4 的讨论), 并说明它在何种意义下唯一地刻画了商幺半群 $M/\sim$.

??? Solution
    给定幺半群 $M$ 与其上的等价关系 $\sim$，所有满足 $(x \sim y) \Rightarrow \varphi(x) = \varphi(y)$ 的幺半群同态 $M \stackrel \varphi \rightarrow N$ 构成一个范畴，其上的态射 $\mathrm{Hom}(M \stackrel \varphi \rightarrow N, M \stackrel {\varphi^\prime} \rightarrow N^\prime)$ 定义为使得下图交换的所有幺半群同态 $\psi$：

    <script type="text/tikz" data-tikz-libraries="cd" data-show-console="true">
        \begin{tikzcd}
            & {\text{id}_{S}}
            \arrow[mapsto]{r} \arrow[phantom, d, sloped, "\in" description]
            & {u_{S}}
            \arrow[phantom, d, sloped, "\in" description] \\
            {\text{id}_{S}}
            \arrow[mapsto]{d} \arrow[phantom, r, sloped, "\in" description]
            & {\text{Hom}_{\mathcal{C}}(S,S)}
            \arrow[d,"{f^{*}}"'] \arrow[r,"{\phi_{S}}"]
            & {A(S)}
            \arrow[d,"A(f)"] \arrow[phantom, r, sloped, "\ni" description]
            & {u_{S}}
            \arrow[mapsto]{d} \\
            {f}
            \arrow[phantom, r, sloped, "\in" description]
            & {\text{Hom}_{\mathcal{C}}(T,S)}
            \arrow[r,"\phi_T"']
            & {A(T)}
            \arrow[phantom, r, sloped, "\ni" description]
            & {\phi_{T}(f)} \\
            & {f_{S}}
            \arrow[phantom, u, sloped, "\in" description] \arrow[mapsto]{r}
            & {\phi_{T}(f)}
            \arrow[phantom, u, sloped, "\in" description]
        \end{tikzcd}
    </script>