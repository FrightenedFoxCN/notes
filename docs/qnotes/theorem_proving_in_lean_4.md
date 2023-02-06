原文链接：[Theorem Proving in Lean 4 (leanprover.github.io)](https://leanprover.github.io/theorem_proving_in_lean4/introduction.html)

## Dependent Type Theory 依赖类型论

类型论（type theory）给每个表达式以一个关联的类型。例如，自然数（`Nat`），从自然数到自然数的函数（`Nat → Nat`），它们都是类型。在 Lean 4 中，一个自然数是一个任意精度的无符号整数。

使用 `def` 关键字在 Lean 中声明对象（object），语法为：

```lean4
def m: Nat := 1
    ^  ^^^    ^ value of the object
    |  associated type
    object name
```

可以用 `#check` 命令来检查一个对象或对象构成的表达式的类型，例如：

```lean4
#check m
	   ^ the name of the object
#check m + 0
	   ^^^^^ or the expression
```

可以用 `#eval` 命令来检查一个表达式的值，例如：

```lean4
#eval m + 2
```

??? info 评论（comment）
    `/- -/` 表示评论块，`--` 表示行末评论，例如：
    ```lean4
    /- this is a comment -/
    #eval m + 2 -- and this is also one
    ```

可以使用已有的类型来组合成新的类型。一种方式是定义函数类型（function）：如果 `a` 和 `b` 都是类型，那么 `a → b` 也是类型。当然，这样的方式是可以嵌套的，例如 `Nat → (Nat → Nat)` 表示一个定义在自然数上的函数，它的值是一个自然数到自然数的函数。当然，它是右结合的，也就是说，上面那个表达式等价于 `Nat → Nat → Nat`，而 `(Nat → Nat) → Nat` 是一个定义域为函数的函数，我们称之为一个泛函（functional）。

另一种组合方式是类型之间的笛卡尔积（Cartesian product）：如果 `a` 和 `b` 都是类型，那么 `a × b` 也是类型。这个类型中的元素则被表示成一个有序对（ordered pair），例如 `(5, 9)` 是 `Nat × Nat` 类型的。我们可以使用 `.` 来访问某个有序对中的一个元素，例如：

```lean4
#eval (5, 9).1 -- output 5
#eval (5, 9).2 -- output 9
```

??? danger 下标越界
    注意，Lean 4 中的有序对下标的方式不同于很多编程语言中的数组，它是从 1 开始的。下标越界一般会报 invalid projection，但是如果把 0 当作下标，报错则是 invalid field notation。

注意到，`→` 和 `×` 都是 Unicode 字符，也可以使用 `->` 和 `Prod`（前缀式）来代替，例如：

```lean4
#check Nat → Nat     -- this line is equivalent to
#check Nat -> Nat    -- this line

#check Nat × Nat     -- and this one to
#check Prod Nat Nat  -- this one
```

??? info Unicode 符号的输入
    在 Lean 4 编辑器里（笔者用的是 VSCode），可以使用 `\to` 来打出 `→`，用 `\times` 打出 `×` 。我们以后会使用希腊字母表示类型，输入命令和 LaTeX 相同，特别地，用 `\a` 表示 `α`，用 `\b` 表示 `β`，用 `\g` 表示 `γ`。

使用 `f x` 这样的语法来表示 `f` 对值 `x` 的应用，例如：

```lean4
#eval Nat.succ 2 -- 3
#eval Nat.add 5 2 -- 7
```

注意，像 `Nat.add` 这类类型为 `Nat → Nat → Nat` 的函数是可以做到部分应用（partial application）的，例如：

```lean4
def add_five: Nat → Nat := Nat.add 5
#eval add_five 2
```

不如说，不把它定义成一个形如 `(Nat × Nat) → Nat` 的函数就是为了方便进行部分应用。

开篇我们就提到，要给每个表达式一个关联的类型。那么我们当然也可以给类型以它们所关联的类型。我们前面看到的自定类型都是 `Type` 类型的成员，它们的积以及它们组成的函数都是 `Type` 类型的，可以通过 `#check` 命令验证这一点。

当然，也可以声明新的类型，语法与上面一样，只不过我们将类型也视为一种对象：

```lean4
def α: Type := Nat
```

当然咯，我们也就有类型上的函数和类型的积，那么问题来了，`Type` 以及它的组合又都是什么类型的呢？使用 `#check` 验证可以发现它是 `Type 1` 类型的，而 `Type 1` 又是 `Type 2` 类型的，等等，而且每个层级当中的函数和积类型都是封闭的。因此，我们将这种方式称为可数的非层叠宇宙（countable hierachy of  non-cumulative universe）。可数意味着它的层数与自然数等价，非层叠意味着我们不会将下面的层级视作上面层级的子集，例如，`Nat` 是 `Type` 类型的不意味着它是 `Type 1` 类型的，当然，这些细节可能对于程序员而言只有一些理论趣味。`Type` 类型事实上是 `Type 0` 类型的，我们将它所属的层级的序号称为它的度（degree）。两个不同度数类型组成的函数属于两者中度较高者所属的层级，积也同理。

但是，在类型宇宙中有些操作可能是多态的（polymorphic）。例如，`List` 函数属于 `Type u_1 → Type u_1` 类型，其中 `u_1` 可以是任意层级，它给出一个类型的对象组成的一个列表。`Prod` 函数也同理，它是 `Type u_1 → Type u_2 → Type (max u_1 u_2)` 类型的。

可以使用 `universe` 关键字来指明一个宇宙变量，从而定义这种函数，例如，我们定义一个从 `Type u` 到 `Type u` 的函数 `f` ：

```lean4
universe u
def F (α: Type u): Type u := Prod α α
```

这也可以被简单地写成：

```
def F.{u} (α: Type u): Type u := Prod α α
```

另一种定义函数的方式是使用关键字 `fun` 或者 `λ`，这种方式被称为 λ-抽象（lambda abstraction）。例如：

```lean4
def add_five: Nat → Nat := fun (x: Nat) => x + 5
def add_five: Nat → Nat := λ (x: Nat) => x + 5
```

其中括号可以省略。我们可以看出，`λ x: Nat => x + 5` 本来就是一个 `Nat → Nat` 类型的函数对象，因此可以将其直接应用于 `Nat` 型的对象来求值。

还可以定义更加复杂的函数，例如：

```
def plus_one_or_two: Nat → Bool → Nat := fun x: Nat => fun y: Bool => if not y then x + 2 else x + 1

#eval plus_one_or_two 2 True
```

其中用到了 `if` 语句，它的语义是显然的。注意，这个例子表明应用过程也是从前往后的，这符合上面提到的 `→` 的结合性。我们还可以把它定义成：

```
def plus_one_or_two := fun (x: Nat) (y: Bool) => if not y then x + 2 else x + 1 -- type annotation of the function can be omitted
def plus_one_or_two := fun x y => if not y then x + 2 else x + 1 -- even the type annotation of the variables, if can be inferred
```

当然，类型变量和函数也可以是函数的参数。事实上，还有更简单的写法：

```lean4
def plus_one_or_two (x) (y) := if not y then x + 2 else x + 1
```

其中的类型说明（type annotation）全部省略了，完全体应该是：

```lean4
def plus_one_or_two (x: Nat) (y: Bool): Nat := if not y then x + 2 else x + 1
```

再来写一个更抽象的函数：

```
def compose (α β γ: Type) (g: β → γ) (f: α → β) (x: α): γ := g (f x)
```

这个函数首先接受三个类型作为第一组参数，然后根据这三个参数决定后面接受的参数的类型，最后返回函数复合之后的计算结果，比如：

```lean4
def f (n : Nat) : String := toString n
def g (s : String) : Bool := s.length > 0
#check compose Nat String Bool g f
```

这样得到的结果类型为 `Nat → Bool` ，应当不难验证。我们把这种一个项的“计算过程”称为正规化（normalization）过程，两个被化作同样的值的项被称为定义等价的（definitionally equal）。

可以使用 `let` 关键字定义在同一块表达式里面的局部定义（local definition）。它可以被视作一种“简写”，例如：

```lean4
def t (x: Nat): Nat := 
    let y := x + x 
    y * y
/- or like this -/
def t (x: Nat): Nat := let y := x + x; y * y
```

可以使用 `variable` 关键字定义变量，例如：

```lean4
variable (α β γ : Type) 
variable (g : β → γ) (f : α → β) (h : α → α) 
variable (x : α) 

def compose := g (f x) 
def doTwice := h (h x) 
def doThrice := h (h (h x))
```

这样可以省去很多类型说明，让代码变得更加简洁。在函数定义中，用到的变量会被自然地当成函数自变量来处理，进而自动计算出函数的类型。

但是，这样定义的变量是全局的，我们可以用 `section` 开启一个节，让变量只在节中发挥作用：

```lean4
section useful1
    variable (α β γ : Type) 
    variable (g : β → γ) (f : α → β) (h : α → α) 
    variable (x : α) 

    def compose := g (f x) 
    def doTwice := h (h x) 
    def doThrice := h (h (h x))
end useful1
```

节中的变量在节外就没有定义了（unknown identifier），但是其他定义还可以留下来。节的名字不是必须的。

同样的，定义也可以用名称空间分组。关键词 `namespace` 定义一个名称空间，`end` 结束一个名称空间。在名称空间之外，访问名称空间中的定义要用 `.` 运算符，例如：

```lean4
namespace ns
  def a: Nat := 10
end ns

#check ns.a

open ns
#check a
#check ns.a
```

`open` 关键字可以将名称空间中的东西暴露出来，它可以受到 `section` 的范围限制。名称空间可以嵌套，也和 `section` 一样具备限制范围的一些作用。

回到上面定义的的 `compose` 函数，这个函数的类型是什么？如果使用 `#check` 命令，我们将得到的结果是 `(α β γ : Type) → (β → γ) → (α → β) → α → γ`，这是个什么东西？

下面用一个更简单的例子来说明这一点。`List α` 返回一个类型的列表类型，我们尝试定义一个函数来做到对这个列表完成头插：

```lean4
def cons (α: Type) (a: α) (as: List α): List α := List.cons a as
```

这里直接调用了标准库中写好的函数来完成这个操作，但是它的类型是什么？使用 `#check` 命令的结果为 `(α : Type) → α → List α → List α` ，但是为什么？

注意到，尽管一开始我们会觉得它的类型是 `Type → α → List α → List α` ，但这并不正确。后面的 `α` 事实上是前面 `Type` 类型中的东西，也就是说，后面的类型推算是依赖于第一个“参数”的，这时我们必须在类型中说明它是如此。这种函数被称为依赖函数类型（dependent function type，或依赖箭头类型，dependent arrow type），它们的存在事实上表明了依赖类型论这个名字中依赖二字的由来。

对于任意的 `α` 和 `β`，定义 `(a: α) → β` 总是可能的。但是，当 `β` 与 `α` 无关时，它和 `α → β` 没什么区别。毋宁说，在依赖类型论中，`α → β` 只是 `(a: α) → β` 在 `β` 与 `α` 无关时的一种简写。

当然，定义依赖笛卡尔积类型（dependent Cartesian product type）也是可能的，形如 `(a: α) × β` 的类型和函数有着一样的解释。这也被称为 Σ-类型（sigma types）。我们也可以将其写作 `Σ a: α, β a`，也可以用 `⟨a, b⟩` 或 `Sigma.mk` 来构造积类型，例如：

```
def f.{u, v} (α : Type u) (β : α → Type v) (a : α) (b : β a) : Σ a, β a := Sigma.mk a b
```

在上面的定义里，`.{u, v}` 可以省略，因为 Lean 4 可以推断出它们都是宇宙。

最后，在上面定义 `cons` 时，我们用到了标准库函数。用 `#check List.cons` 查看它的类型为 `?m.758 → List ?m.758 → List ?m.758`，这是为什么？

注意到，对于 `cons` 函数，`α` 的类型信息可以被看成是多余的。因为它可以由给出的参数的类型直接推断出来。这里的一种方法是使用下划线来表明一个类型可以从定义中推断出来：

```lean4
#check cons _ 5 -- output: cons Nat 5 : List Nat → List Nat
```

但这还是很麻烦，虽然我们不需要写 `Nat` 类型，但还是要打下划线。因此，我们可以在函数定义的时候就说明，这个类型由后面的参数可以直接推断出来：

```lean4
def cons {α: Type} (a: α) (as: List α): List α := List.cons a as
```

这时这个函数的类型就变成了 `?m.703 → List ?m.703 → List ?m.703`，和标准库函数的类型完全一致。如果我们查看 `cons 5` 的类型，就会发现它已经是 `List Nat → List Nat` 了。也可以通过 `variable {α: Type}` 这样的语法指定省略类型的变量。

事实上，我们也可以直接指定它的类型，例如：

```lean4
#check (cons: Nat → List Nat → List Nat)
```

给出的结果就是 `Nat → List Nat → List Nat` 。当数字的类型不能被推断时，它默认会使用 `Nat` 类型，虽然有时 `Int` 也是可行的。

如果我们需要充分说明所有的参数，那么就需要使用 `@` 前缀。它指的是和其标识的函数名完全一样的函数，但其中所有隐藏的参数都被显式地要求了，例如：

```lean4
#check @cons -- output: @cons : {α : Type} → α → List α → List α
#check @cons Nat -- output: cons : Nat → List Nat → List Nat
```