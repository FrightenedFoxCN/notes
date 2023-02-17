---
comments: true
---

# 计算理论笔记 Theory of Computation Overview

计算理论（theory of computation）研究的核心问题就是计算（computation）。我们需要思考的问题是：什么是计算；什么可以计算或不可以计算；如果可以计算，这个问题有多难计算；如果不可以计算，这个问题不可以计算的程度有多少。这个系列（前半部分的）主要框架（01A, 03A 和 05A 中的部分）来自于浙江大学计算理论课程毛宇尘老师的授课，插入了大量笔者个人的想法和来源于其他参考资料的结论和思路，应当完全覆盖并超越这门课程本身。这门课程事实上只部分地回答了前两个问题，对于第三个问题一带而过，而对于第四个问题几乎完全没有讨论，但是在这个系列里，我会尽可能完整地展现整个理论从新生到现代的全貌。笔者才疏学浅，如有疏漏，望指正。

## 预计目录（部分）

注：已完成✅ 已建立页面☑️ 未完成❎

|序号 | <center>标题</center> | 是否已完成|
|:----:|----------------------------------------------------------|:----:|
| 01A | [有限自动机和正则语言 Finite Automata and Regular Languages](01A) | ☑️ |
| 01B | [范畴化的自动机 Automata in Category Context](01B) | ☑️ |
| 02A | 线性语言及其机器实现 Linear Languages and Correspounding Machine | ❎ |
| 02B | 更多（简单的）自动机和拓扑化 More Simple Automata, Finite Topology | ❎ |
| 03A | 下推自动机和上下文无关语言 Push-down Automata and Context-free Languages | ☑️ |
| 03B | 语言、逻辑和推理 Languages, Logic and Deduction | ❎ |
| 04A | 随机自动机、量子自动机概述 Stochastic Automata, Quantum Automata | ❎ |
| 04B | 物理相关的杂谈：信息熵和可逆性 Physics-related Topics: Entropy and Reversibility | ❎ |
| 05A | 图灵机 Turing Machines | ❎ | 
| 05B | lambda 演算和 Curry-Howard 同构 Lambda Calculus and Curry-Howard Isomorphism | ❎ |
| 06A | 可计算函数 Computable Functions | ❎ |
| 06B | 结构化不动点定理 Structural Fixed Point Theorem | ❎ |
| 07A | 带谕示机的图灵机 Oracled Turing Machine | ❎ |
| 07B | 度和 Turing 跳跃 Degrees and Turing Jump | ❎ |