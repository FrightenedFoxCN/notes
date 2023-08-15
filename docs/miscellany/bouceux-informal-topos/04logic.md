---
comments: True
---

# 4 拓扑斯的内逻辑

在本节课中我们谈及的拓扑斯都指初等拓扑斯，除非特别指明。

## 4.1 拓扑斯的语言

如果你想要研究实数域，你首先需要处理具体的数，例如 $5$，$\frac 2 3$，$\pi$，$\sqrt 2$ 等等。我们将它们称为类型 $\R$ 的常元（constants of type $\R$）：因此，这样的常量的个数与实数的个数相同。但是，你也需要处理类似这样的公式：

$$
a \times (b + c) = (a \times b) + (a \times c)
$$

其中 $a$，$b$，$c$ 表示任意的、未指明的实数。我们称 $a$，$b$，$c$ 为类型 $\R$ 的变元（variables of type $\R$）。因为你能写下的一个公式是一个符号组成的有限序列，你每次只需要有限个（当然，可能非常多个）这样的变量……因此，想要写下所有关于实数的可能公式，一个可列的变量集完全够用。因此，变量的个数与 $\R$ 中元素的个数毫无关系。注意，哪怕你只想讨论单元素集，你也有可能用到两个不同的变量，例如下面的式子表示单元素集只有一个元素：

$$
\forall x\ \forall y\ x = y
$$

一个拓扑斯的语言是你能使用的所有“良定的”（well-formed）符号串的集合：现在的问题就在于，抛却写下的东西的实际含义，怎么界定何为“良定”的符号串。例如，在英语中，你被允许使用字典中的所有单词，并用符合语法规则的方式将它们组合起来，因此 *The prolific fork mixes yellow mathematics.*[^1] 也是一个完全良定的英语句子。

[^1]: “多产的叉子搅拌黄色的数学。”一个典型的符合语法但是不知所云的句子。——译者注

\definition
    （4.1）考虑拓扑斯 $\mathcal E$，对每个元素 $A \in \mathcal E$ 它的语言给定：

    - 对每个箭头 $1 \to A$，一个符号，称为一个类型 $A$ 的常元。
    - 一个符号组成的可列集，称为类型 $A$ 的变元。

    以及各种由它们组成的形式表达式，叫做项（term）和公式（formula），见下面的定义 4.2 和 4.3。

从现在开始，我们可以直觉地将类型 $A$ 的常元和变元（更广泛的，所有类型 $A$ 的项，如 4.2 所述）视作 $A$ 的形式内元素。我们说这是形式的，是因为直到现在为止，它们只存在于我们的想象当中，它们（尚且）并不与拓扑斯中的任何对象或者箭头相对应。直觉地说，我们希望将拓扑斯的元素视作某种广义的集合。例如，在一个宇性拓扑斯中，层是某种带有“不同水平上”的元素的广义集合。准此原则，如果 $A$ 上面有，比方说，加法 $+: A \times A \to A$，我们当然希望谈论形式内元素 $a + b$，其中 $a$，$b$ 为类型 $A$ 的变元或者常元。如果 $f: A \to B$ 是一个态射，我们希望能够谈论类型 $B$ 的形式内元素 $f(a)$。以此类推。我们希望补充的这些额外的类型 $A$ 或者类型 $B$ 的形式元素被称为类型 $A$ 或者类型 $B$ 的项。定义 4.2 会递归地定义我们在一个拓扑斯中所能考虑的所有可能的项，也就是所有我们能想到的可行的直觉地表示形式内元素的形式表达式。

接下来，假定 $A$ 有一个内在的群结构，因此，加法是结合的，我们自然希望通过“对于所有类型 $A$ 的形式内元素 $a$，$b$，$c$，都有 $(a + b) + c = a + (b + c)$ 成立”来表达这种结合性。这样一个内部元素之间的形式表达式不再是一个形式元素了：它直觉地表达了包含 $a + b$，$b + c$ 等等的项的某种形式上的性质。但是一个公式，直到现在，在拓扑斯中还毫无意义。定义 4.3 会递归地定义我们希望在一个拓扑斯内使用的所有公式。

另外，在公式中，我们还希望使用诸如 $\wedge$，$\vee$，$\implies$，$\exists a$ 或者 $\forall a$ 等等的数学符号。类似于经典逻辑的说法，在 $\exists a$ 或者 $\forall a$ 这样的量词中出现的变元被称为受限变元（bound variable），不在量词中出现的变元被称为自由变元（free variable）。

在定义写下项和公式的定义之前，不妨再次回忆一下，在一个拓扑斯中，类型 $\Omega^A$ 的常元，即形如 $1 \to \Omega^A$ 的态射，与形如 $A \to \Omega$ 的态射之间是有一个双射的，因此，也与 $A$ 的子对象之间有一个双射。这样，$\Omega^A$ 在形式上应当被认为是“A 的子对象的对象”：一个类型 $\Omega^A$ 的常元代表了 $A$ 的一个实际的子对象，一个类型 $\Omega^A$ 的变元可以被认为代表了 $A$ 的一个形式内子对象。

为了避免下面这些定义的核心被一些不必要的关于自由变元的细节掩盖，我们在此省略了这些细节，读者可以参考文献 [4] 的定义 6.1.1，那里有更为精确的定义。

\definition
    （4.2）在拓扑斯 $\mathcal E$ 中，内语言的项被递归地定义如下：

    1. 类型 $A$ 的常元是类型 $A$ 的项；
    2. 类型 $A$ 的变元是类型 $A$ 的项；
    3. 如果 $\tau$ 是类型 $A$ 的项，$f: A \to B$ 是 $\mathcal E$ 中的一个态射，那么 $f(\tau)$ 是一个类型 $B$ 的项；
    4. 如果 $\tau_1, \cdots, \tau_n$ 分别为类型 $A_1, \cdots, A_n$ 的项，那么 $(\tau_1, \cdots, \tau_n)$ 是类型 $A_1 \times \cdots \times A_n$ 的项；
    5. 如果 $\tau$ 是一个类型 $A$ 的项，带有类型分别为 $A_1, \cdots, A_n$ 的自由变元 $a_1, \cdots, a_n$；$\sigma_1, \cdots, \sigma_n$ 是类型分别为 $A_1, \cdots, A_n$ 的不含 $\tau$ 中的受限变元的项，则 $\tau(\sigma_1, \cdots, \sigma_n)$ 仍然是类型 $A$ 的一个项；
    6. 如果 $\varphi$ 是一个带有自由变元 $a_1, \cdots, a_n, b_1, \cdots, b_m$ 的公式，类型分别为 $A_1, \cdots, A_n, B_1, \cdots, B_m$，则 $\{(a_1, \cdots, a_n) | \varphi(a_1, \cdots, a_n, b_1, \cdots, b_m)\}$ 是一个类型 $\Omega^{A_1 \times \cdots \times A_n}$ 的项。

\definition
    （4.3）在拓扑斯 $\mathcal E$ 中，内语言的公式被递归地定义如下：

    1. 符号 $\mathsf{true}$ 和 $\mathsf{false}$ 是公式；
    2. 如果 $\tau$ 和 $\sigma$ 都是类型 $A$ 的项，那么 $\tau = \sigma$ 是一个公式；
    3. 如果 $\tau$ 是一个类型 $A$ 的项，$\Sigma$ 是一个类型 $\Omega^A$ 的项，那么 $\tau \in Sigma$ 是一个公式；
    4. 如果 $\varphi$ 是一个公式，那么 $\lnot \varphi$ 也是一个公式；
    5. 如果 $\varphi$ 和 $\psi$ 都是公式，那么 $\varphi \wedge \psi$，$\varphi \vee \psi$ 和 $\varphi \implies \psi$ 都是公式；
    6. 如果 $\varphi$ 是一个带有自由变元 $a, b_1, \cdots, b_n$ 的公式，它们类型分别是 $A, B_1, \cdots, B_n$，则 $\exists a \varphi(a, b_1, \cdots, b_n)$ 和 $\forall a \varphi(a, b_1, \cdots, b_n)$ 都是带有自由变元 $b_1, \cdots b_n$ 的公式。
    7. 如果 $\varphi$ 是一个带有自由变元 $a_1, \cdots, a_n$ 的公式，类型分别为 $A_1, \cdots, A_n$，$\sigma_1, \cdots, \sigma_n$ 是类型分别为 $A_1, \cdots, A_n$ 的项，带有同为 $b_1, \cdots, b_m$，类型分别为 $B_1, \cdots, B_m$ 的自由变元，则 $\varphi(\sigma_1(b_1, \cdots, b_m), \cdots, \sigma_n(b_1, \cdots, b_m))$ 是一个带有自由变元 $b_1, \cdots, b_m$ 的公式。

注意，上面对于两个公式或者项具备相同自由变量的假设并不是什么真正意义上的限制，因为把某个给定变量当成一个公式或者项的自由变量并不会造成什么问题……哪怕它没有在那个公式或者项中显式出现。

当然，一如既往地，$\exists !x\ \varphi(x)$ 是下面的表达式的缩写：

$$
(\exists x \ \varphi(x)) \wedge ((\varphi(y) \wedge \varphi(z)) \implies (y = z))
$$

换句话说，这一小节旨在表明，拓扑斯的语言事实上正是模仿了集合论的通常语言。但是直到现在为止，这只是一种填字游戏，你通过将一些形式符号并置在一起来构造句子（公式或者项）。但是只有那些在定义 4.2 和 4.3 中所述的“字典”和“语法”中的句子才是良定的，因此，诸如：

$$
\exists a \ \forall b \ (\lnot(a = a)) \wedge (a = b)
$$

是我们语言中的一个完美（但愚蠢）的良定的句子……

## 4.2 项和公式的实现（realization）

让我们回到实数的例子上来。给定有理数 $a$ 和自然数 $b$，我们可以构造一个实数 $b^{a\pi}$。用 4.1 节的话说，$b^{a\pi}$ 就是一个类型 $\R$ 的项，带有类型 $\mathbb Q$ 的变元 $a$ 和类型 $\N$ 的变元 $b$。这样的一个项诱导了映射：

$$
\mathbb Q \times \N \to \R, (a, b) \mapsto b^{a\pi}
$$

这个映射就是我们所谓的项 $b^{a\pi}$ 的实现。通过这个过程，我们将 $\mathsf{Set}$ 中类型 $\R$ 的一个形式的项和集合拓扑斯中的一个良定的态射联系了起来。

准此思路，对于一个拓扑斯中的每个形式的项，我们都可以分派一个实际的同态。对于每个类型 $A$ 的项 $\tau$，其自由变元为类型分别是 $A_1, \cdots, A_n$ 的 $a_1, \cdots, a_n$，我们为其指派一个“实现”态射[^2]：

$$
\lceil \tau \rceil: A_1 \times \cdots \times A_n \to A
$$

[^2]: 看起来作者在原文中用的是 `tipa` 包中的 `\textopencorner` 而不是这里用的 `\lceil`，译者用 `\lceil` 代替是因为 KaTeX 没有这玩意。——译者注

同样的，定义依然是递归的。为了简短起见，我们直接继承定义 4.2 中的符号和计数：

\definition
    （4.4）在拓扑斯 $\mathcal E$ 中，继承定义 4.2 中的记号和标号，项 $\tau$ 的实现 $\lceil \tau \rceil$ 被递归地定义如下：

    1. 常元的实现是它自身；
    2. 类型 $A$ 的变元的实现是 $A$ 上的恒同态射；
    3. $\lceil f(\tau) \rceil = f \circ \lceil \tau \rceil$；
    4. $\lceil (\tau_1, \cdots, \tau_n) \rceil$ 的实现是 $(\lceil \tau_1 \rceil, \cdots, \lceil \tau_n \rceil)$；
    5. $\lceil \tau(\sigma_1, \cdots, \sigma_n) \rceil = \lceil \tau \rceil \circ (\lceil \sigma_1 \rceil, \cdots, \lceil \sigma_n \rceil)$；
    6. $\lceil \{(a_1, \cdots, a_n) | \varphi\} \lceil$ 是一个 $B_1 \times \cdots \times B_m \to \Omega^{A_1 \times \cdots \times A_n}$ 的态射，通过笛卡尔闭性（见定义 4.5）与 $\lceil \varphi \rceil$ 对应。

接下来，让我们再次回到 $\mathsf{Set}$ 中的实数上来，考虑，例如，公式 $a + b = c$，它有三个带有类型 $\R$ 的变元。这自然地给出了一个映射：

$$
\R \times \R \times \R \to \{\mathsf{false}, \mathsf{true}\}
$$

将一个具体的实数三元组 $(a, b, c)$ 映到 $a + b = c$ 的真值。这个映射是我们所谓的公式 $a + b = c$ 的真值表。如前所属，在集合拓扑斯中，$\{\mathsf{false}, \mathsf{true}\}$ 不过就是 $\Omega$，我们的子对象分类子。被这个真值表分类出来的对象也就是满足 $a + b = c$ 的三元组所构成的集合。

我们已经多次发现，在一个宇性拓扑斯中，对象 $\Omega$ 在某种程度上扮演了“真值的对象”的角色。例如，考虑定义 2.3 中的 $= : A \times A \to \Omega$，给定 $A(u)$ 中的 $a, b$，元素 $=_u(a, b)$ 是 $a = b$ 的真值，是满足 $a$ 和 $b$ 相等的条件下的最高层级。态射 $=$ 因此也就是公式 $a = b$ 的某种“真值表”。以此类推，现在，我们要给每个带有类型 $A_1, \cdots, A_n$ 的自由变元 $a_1, \cdots, a_n$ 的公式 $\varphi$ 一个“真值表”态射：

$$
\lceil \varphi \rceil: A_1 \times \cdots A_n \to \Omega 
$$

被这个真值表分类的子对象 $[\varphi] \rightarrowtail A_1 \times \cdots \times A_n$ 也可以被更明确地写成下面的形式：

$$
\{(a_1, \cdots, a_n) | \varphi(a_1, \cdots a_n)\} \rightarrowtail A_1 \times \cdots \times A_n
$$

当然，这和定义 4.2 是一致的。

我们的定义依然是递归地进行的，这次不仅仅要诉诸定义 4.3 的符号和标号：

\definition
    （4.5）在拓扑斯 $\mathcal E$ 中，继承定义 4.3 的符号和编号，应用定义 2.5、定义 2.5、定理 2.23、定义 2.12 的各种构造，公式 $\varphi$ 的真值表 $\lceil \varphi \rceil$ 被递归地定义为：

    1. $\lceil \mathsf{true} \rceil = t$，$\lceil \mathsf{false}\rceil = f$；
    2. $\lceil \tau = \sigma \rceil = (=_A) \circ (\lceil \tau \rceil, \lceil \sigma \rceil)$；
    3. $\lceil \tau \in \Sigma \rceil$ = $(\in_A) \circ (\lceil \tau \rceil, \lceil \Sigma \rceil)$；
    4. $\lceil \lnot \varphi \rceil = \lnot \circ \lceil \varphi \rceil$；
    5. $\lceil \varphi \wedge \psi \rceil = \wedge \circ (\lceil \varphi \rceil, \lceil \psi \rceil)$，$\lceil \varphi \vee \psi \rceil = \vee \circ (\lceil \varphi \rceil, \lceil \psi \rceil)$，$\lceil \varphi \implies \psi \rceil = (\implies) \circ (\lceil \varphi \rceil, \lceil \psi \rceil)$；
    6. 在 4.3.6 中，考虑投影 $p: A \times B_1 \times \cdots \times B_n \to B_1 \times \cdots \times B_n$ 和由 $\lceil \varphi \rceil$ 分类的子对象 $[\varphi] \rightarrowtail A \times B_1 \times \cdots \times B_n$，则 $\lceil \exists a\ \varphi(a, b_1, \cdots, b_n) \rceil$ 和 $\lceil \forall a \ \varphi(a, b_1, \cdots, b_n) \rceil$ 分别为 $\exists_p [\varphi]$ 和 $\forall_p [\varphi]$ 的特征态射；
    7. $\lceil \varphi(\sigma_1, \cdots, \sigma_n) \rceil = \lceil \varphi \rceil \circ (\lceil \sigma_1 \rceil, \cdots, \lceil \sigma_n \rceil)$。

当然，$\mathsf{true}$ 和 $\mathsf{false}$ 是没有自由变元的公式。如果把它们视作带有（未出现的）类型 $A$ 的自由变元 $a$ 的公式，对应的真值表可以被简单地写成：

$$
\mathsf{true}: A \to \mathbf 1 \stackrel t \to \Omega, \quad \mathsf{false}: A \to \mathbf 1 \stackrel f \to \Omega
$$

在有可能造成混淆的情况下，将其记为 $\mathsf{true}_A$ 和 $\mathsf{false}_A$。

最后，我们以一个显然但有用的观察作为这一节的尾声：

\proposition
    （4.6）在拓扑斯 $\mathcal E$ 中，考虑两个具备相同的类型为 $A_1, \cdots, A_n$ 的自由变元 $a_1, \cdots, a_n$ 的公式 $\varphi$ 和 $\psi$，将由 $\lceil \varphi \rceil$ 和 $\lceil \psi \rceil$ 分类的 $A_1 \times \cdots \times A_n$ 中的子对象分别记作 $[\varphi]$ 和 $[\psi]$，则由

    $$
    \lceil \mathsf{true} \rceil, \quad \lceil \mathsf{false} \rceil, \quad \lceil \varphi \wedge \psi \rceil, \quad \lceil \varphi \vee \psi \rceil, \quad \lceil \varphi \implies \psi \rceil, \quad \lceil \lnot \varphi \rceil
    $$

    所分类的 $A_1 \times \cdots \times A_n$ 中的子对象不外乎是其子对象规程的 Heyting 代数中的

    $$
    A_1 \times \cdots \times A_n, \quad 0, \quad [\varphi] \wedge [\psi], \quad [\varphi] \vee [\psi], \quad [\varphi] \implies [\psi], \quad \lnot [\varphi]
    $$

\proof
    由定义直接得出。

## 4.3 拓扑斯中的命题逻辑

下面我们需要说明，什么叫某个公式是真的，并且推断出拓扑斯的内逻辑中有效的推理规则。

\definition
    （4.7）在拓扑斯 $\mathcal E$ 中，设 $\varphi$ 是一个带有类型分别为 $A_1, \cdots, A_n$ 的变元 $a_1, \cdots, a_n$ 的公式，我们说这个公式为真当且仅当 $\lceil \varphi \rceil = \lceil \mathsf{true} \rceil$，记作 $\models \varphi$。这也就是说，$\lceil \varphi \rceil$ 分类的子对象就是 $A_1 \times \cdots \times A_n$ 本身。

\theorem
    （4.8）在拓扑斯 $\mathcal E$ 中，直觉主义谓词逻辑的公理全部成立。也就是说，给定三个带有相同自由变元的公式 $\varphi, \psi, \theta$，以下性质成立：

    \begin{aligned}
    (P1) & \models \varphi \implies (\psi \implies \varphi)\\
    (P2) & \models (\varphi \implies (\psi \implies \theta)) \implies ((\varphi \implies \psi) \implies (\varphi \implies \theta))\\
    (P3) & \models \varphi \implies (\psi \implies (\varphi \wedge \psi))\\
    (P4) & \models \varphi \wedge \psi \implies \varphi\\
    (P5) & \models \varphi \wedge \psi \implies \psi\\
    (P6) & \models \varphi \implies (\varphi \vee \psi)\\
    (P7) & \models \psi \implies (\varphi \vee \psi)\\
    (P8) & \models (\varphi \implies \theta) \implies ((\varphi \implies \theta) \implies ((\varphi \vee \psi) \implies \theta))\\
    (P9) & \models (\varphi \implies \psi) \implies ((\varphi \implies \lnot \psi) \implies \lnot \varphi)\\
    (P10) & \models \lnot \varphi \implies (\varphi \implies \psi)\\
    (P11) &\ 若\ \models \varphi\ 且 \ \models \varphi \implies \psi\ 则\ \models \psi\ \text{（肯定前件，modus ponens）}
    \end{aligned}

\proof
    假定 $\varphi, \psi, \theta$ 的自由变元为类型分别为 $A_1, \cdots, A_n$ 的变元 $a_1, \cdots, a_n$。由定义 4.7 和命题 4.6，我们只要表明由这些公式分类的 $A_1 \times \cdots \times A_n$ 的子对象就是 $A_1 \times \cdots \times A_n$ 自身。

    事实上，$(P1)$ 到 $(P11)$ 在任意 Heyting 代数中都成立（见定义 2.17）。例如，如果 $a, b$ 是 Heyting 代数 $H$ 中的两个元素，证明 $(P1)$ 就是要表明：

    $$
    1 = (a \implies (b \implies a))
    $$

    当然，这也就等价于证明：

    $$
    1 \leqslant (a \implies (b \implies a))
    $$

    即：

    $$
    a = 1 \wedge a \leqslant b \implies a
    $$

    这进一步地等价于证明：

    $$
    a \wedge b \leqslant a
    $$

    而这是显然的。

肯定前件规则是一条有效的公式之间的推断规则，它自己不是一个有效的公式。

参考文献 [4] 中的 6.7 节给出了一个从定理 4.8 可以导出的有效公式和推断规则的冗长列表。

下面的命题强调了它与经典逻辑的第一个重大区别；亦见例子 4.11。

\proposition
    （4.9）在拓扑斯 $\mathcal E$ 中，令 $\varphi$ 和 $\psi$ 为两个带有相同自由变元的公式：

    - 若 $\models \varphi \wedge \psi$，则 $\models \varphi$ **且** $\models \psi$；
    - 但若 $\models \varphi \vee \psi$，在通常情况下，$\models \varphi$ **或** $\models \psi$ 并不成立。

\proof
    与命题 4.8 的证明类似，也不妨考虑任意 Heyting 代数 $H$ 中的情形。给定 $a, b \in H$，当然 $a \wedge b = 1$ 迫使 $a = 1$ 且 $b = 1$；但是同样显然的是，$a \vee b = 1$ 并不意味着两个元素中一定有一个为 $1$。

当然，还有另外一个与经典逻辑的重大不同：排中律

$$
\models \varphi \vee \lnot \varphi
$$

在拓扑斯的内逻辑中不成立。回顾 3.3 节，排中律成立当且仅当拓扑斯是布尔的。

## 4.4 拓扑斯中的谓词逻辑

下面我们考虑包含量词的额外逻辑规则

\theorem
    （4.10）在拓扑斯 $\mathcal E$ 中，所有直觉主义谓词逻辑的公理也成立。明确地说，考虑两个带有相同自由变元的公式 $\varphi$ 和 $\psi$，以及项 $\tau$，以下性质成立：

    \begin{aligned}
    (P12) & \models (\forall x\ (\varphi \implies \psi)) \implies ((\forall x \ \varphi) \implies \forall x \ \psi)\\
    (P13) & \models (\exists x\ (\varphi \implies \psi)) \implies ((\exists x \ \varphi) \implies \exists x \ \psi)\\
    (P14) & \models \varphi \implies (\forall x \ \varphi)\ 若\ x\ 不是\ \varphi\ 中的一个自由变元\\
    (P15) & \models (\exists x \ \varphi) \implies \varphi \ 若 \ x\ 不是 \ \varphi\ 中的一个自由变元\\
    (P16) & \models (\forall x \ \varphi) \implies \varphi(\tau) \ 若 \ \tau \ 中不含 \ \varphi\ 的受限变元\\
    & \text{ 而且 $\varphi(\tau)$ 是在 $\varphi$ 中将 $x$ 用 $\tau$ 替代的结果}\\
    (P17) & \models  \varphi(\tau) \implies (\forall x \ \varphi) \ 若 \ \tau \ 中不含 \ \varphi\ 的受限变元\\
    & \text{ 而且 $\varphi(\tau)$ 是在 $\varphi$ 中将 $x$ 用 $\tau$ 替代的结果}\\
    (P18) &\ 若 \ \models \varphi \ 则 \ \models \forall x \ \varphi
    \end{aligned}

\proof
    为了简化记号，考虑 $\varphi$ 和 $\psi$ 带有类型分别为 $X$ 和 $A$ 的自由变元 $x$ 和 $a$。公式 $(P12)$ 中有自由变元 $a$，因此证明 $P12$ 就相当于证明在 $A$ 的子对象的 Heyting 代数中证明对应的结论。考虑投影 $p: X \times A \to A$，回顾定理 2.9，我们需要证明：

    $$
    A = [(\forall x\ (\varphi \implies \psi)) \implies ((\forall x \ \varphi) \implies (\forall x \ \psi))]
    $$

    也就是说：

    $$
    A \leqslant [\forall x\ (\varphi \implies \psi)] \implies ([\forall x \ \varphi] \implies [\forall x\ \psi])
    $$

    根据 Heyting 代数中 $\implies$ 的定义，这相当于是说：

    $$
    [\forall x \ (\varphi \implies \psi)] = A \wedge [\forall x \ \varphi \implies \psi] \leqslant ([\forall x\ \varphi] \implies [\forall x\ \psi])
    $$

    更进一步地：

    $$
    [\forall x\ (\varphi \implies \psi)] \wedge [\forall x\ \varphi] \leqslant [\forall x \ \psi]
    $$

    再应用定理 2.9 给出的伴随对 $p^{-1} \dashv \pi_p$，将其转化为：

    $$
    p^{-1}([\forall x\ (\varphi \implies \psi)] \wedge [\forall x \ \varphi]) \leqslant [\psi]
    $$

    即：

    $$
    p^{-1}[\forall x \ (\varphi \implies \psi)] \wedge p^{-1}[\forall x\ \varphi] \leqslant [\psi]
    $$

    伴随对 $p^{-1} \dashv \pi_p$ 的余单位表明，对于任意 $A$ 的子对象 $S$ 都有 $p^{-1}\forall x(S) \leqslant S$。于是：

    $$
    p^{-1}[\forall x \ (\varphi \implies \psi)] \wedge p^{-1}[\forall x\ \varphi] \leqslant [\varphi \implies \psi] \wedge [\varphi] = ([\varphi] \implies [\psi]) \wedge [\varphi] \leqslant [\psi]
    $$

    其它的性质的证明也是类似的。

同样的，在参考文献 [4] 的 6.8 节中，也有一长串能从定理 4.10 推出的有效公式列表。

接下来，我们用一个例子来表明在命题 4.9 中提到过的其与经典逻辑的不同。

!!! info "例子"
    （4.11）考虑实直线上的层拓扑斯。连续函数层（参见 1.2 节）满足以下命题：

    $$
    \models (\exists g\ f \times g = 1) \vee (\exists g\ (1 - f) \times g = 1)
    $$

    但是以下两个命题均不成立：

    $$
    \exists g\ f \times g = 1, \quad \exists g\ (1 - f) \times g = 1
    $$

\proof
    不妨假设 $f$ 为常元，即一个从 $\R$ 到 $\R$ 的连续函数。$f$ 为变元的证明也是类似的。

    若存在 $r \in \R$ 使得 $f(r) \neq 0$，则存在 $r$ 的一个开邻域 $U_r$ 其中 $f(r')$ 处处不为 $0$。设 $U$ 是这种形式的 $U_r$ 的并，那么任意 $r' \in U$，$f(r') \neq 0$，因此在 $U$ 上只要取 $g = \frac 1 f$ 即可。

    类似的，如果存在 $r \in \R$ 使得 $f(r) \neq 1$，则存在 $r$ 的一个开邻域 $V_r$ 其中 $f(r')$ 处处不为 $1$。取 $V$ 为 $V_r$ 的并，那么任意 $r' \in V$，$f(r') \neq 1$，因此在 $V$ 上只要取 $g = \frac 1 {1 - f}$ 即可。

    显然，$U \cup V = \R$，因此第一个命题成立。但是如果取一个有 $f(r_1) = 0$，$f(r_2) = 1$ 的 $f$，那么 $\exists g\ f \times g = 1$ 在 $r_1$ 的邻域不成立，$\exists g\ (1 - f) \times g = 1$ 在 $r_2$ 的邻域不成立，因此两者都不成立。

这个例子表明，在实直线上的层拓扑斯中，连续函数的层是一个“局部环”（local ring）：对于其中的任意元素 $f$，$f$ 和 $1 - f$ 至少有一个是可逆的。这个例子也表明了存在量词的“局部性质”：元素 $g$ 在每个点的邻域都存在，但是通常全局的 $g$ 不存在。

## 4.5 拓扑斯的结构，用其内语言描述

现在，我们的填字游戏进展到哪一步了？我们知道怎么构造合法的[^3]项和公式；我们给它们指派了一个实际的箭头或者拓扑斯中的对象；我们也已经知道一个公式为真是什么意思了。好，现在我宣布，在我们的填字游戏中，你每次写出一个为真的公式，你就能赢得一块比利时巧克力[^4]！哪怕你很喜欢比利时巧克力，恐怕你也并不乐意长时间这样玩下去。你真正感兴趣的，是去证明拓扑斯中的那些范畴论构造相关的定理：积、余等化子、指数，等等。至于形式化地玩弄前面给出来的那些规则，那是非常无聊的事，除非有时候它们在证明实际的范畴论性质时能派上用场。为了能够用这种填字游戏表示范畴论性质，我们还需要做一次翻译，把范畴论术语翻译成拓扑斯的内逻辑的说法。下面我们给出一些代表性（但并不完全）的范畴论术语的翻译：

[^3]: 作者混用了 valid 的两个义项，一个是指公式是良定（或者叫良构，well-formed）的，一个是指公式为真。在这里前者译作合法，后者译作有效。——译者注

[^4]: 比利时巧克力在欧洲非常有名，大概相当于在内地说高邮咸鸭蛋……？——译者注

\proposition
    （4.12）在拓扑斯 $\mathcal E$ 中，考虑：

    - 对象 $A$ 和 $B$；
    - 态射 $f, g: A \rightrightarrows B$ 和 $h: B \to C$；
    - 子对象 $A_1 \rightarrowtail A$，$A_2 \rightarrowtail A$ 和 $B' \rightarrowtail B$；
    - 类型 $A$ 的变量 $a, a'$，类型 $B$ 的变量 $b$ 和类型 $C$ 的变量 $c$；

    以下性质成立：

    1. $f = g$ 当且仅当 $\models f(a) = g(a)$；
    2. $f$ 是一个单同态当且仅当 $\models (f(a) = f(a')) \implies (a = a')$；
    3. $f$ 是一个满同态当且仅当 $\models \exists a \ f(a) = b$；
    4. $A_1 \cap A_2 = \{a | (a \in A_1) \wedge (a \in A_2)\}$；
    5. $A_1 \cup A_2 = \{a | (a \in A_1) \vee (a \in A_2)\}$；
    6. $\mathrm{Im}\ \Sigma_f(A_1) = \{b | \exists a((a \in A_1) \wedge (b = f(a)))\}$；
    7. $\pi_f(A_1) = \{b | \forall a ((f(a) = b) \implies (a \in A_1))\}$；
    8. $f^{-1}(B') = \{a | f(a) \in B'\}$；
    9. $\mathrm{Im}\ (f) = \{b | \exists a\ f(a) = b\}$；
    10. $\mathrm{Ker}\ (f, g) = \{a | f(a) = g(a)\}$；
    11. $f \times_B h = \{(a, c) | f(a) = h(c)\}$，指 $f$ 和 $h$ 的拉回。

