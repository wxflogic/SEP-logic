[< 返回索引](../SEP_Logic_Chinese.md)

# 经典逻辑 (Classical Logic)

**原文链接**: [https://plato.stanford.edu/entries/logic-classical/](https://plato.stanford.edu/entries/logic-classical/)

## 前言

通常，一个逻辑由形式语言或非形式语言，以及一个演绎系统（deductive system）和/或一个模型论语义学（model-theoretic semantics）组成。语言的组成部分对应于像英语或希腊语这样的自然语言的一部分。演绎系统旨在捕捉、编纂或简单记录给定语言的有效论证（valid arguments），而语义学旨在捕捉、编纂或记录该语言至少一部分的意义或真值条件。

以下各节提供了典型逻辑的基础知识，有时称为“经典初等逻辑”或“经典一阶逻辑”。第2节开发了一种形式语言，具有严格的句法和语法。形式语言是固定字母表上递归定义的字符串集合。因此，它本身没有意义，或者更确切地说，其公式的意义由演绎系统和语义学赋予。一些符号在普通语言中有对应的部分。我们将论证（argument）定义为形式语言中非空句子的集合，其中一个被指定为结论。论证中的其他句子（如果有的话）是其前提。第3节为该语言建立了一个演绎系统，秉承自然演绎的精神。如果存在从论证的部分或全部前提导出结论的推导过程，则该论证是可导出的（derivable）。第4节提供了模型论语义学。如果在语义学中没有任何一种解释使得前提全为真而结论为假，则该论证是有效的（valid）。这反映了长期以来的观点，即有效论证是保真的（truth-preserving）。

在第5节中，我们将转向演绎系统与语义学之间的关系，特别是可导出性与有效性之间的关系。我们证明了一个论证只有在它是有效的情况下才是可导出的。这一令人愉悦的特性称为可靠性（soundness），意味着没有任何推导会将人从真前提引向假结论。因此，推导保持真理性。然后我们建立了一个逆命题，称为完全性（completeness），即一个论证只有在它是可导出的情况下才是有效的。这表明演绎系统足够丰富，可以为每个有效论证提供推导。所以有足够的推导：所有且仅有有效论证是可导出的。我们简要指出了该逻辑的其他特征，其中一些是可靠性和完全性的推论。

最后一节，第6节，致力于简要考察经典逻辑是“唯一正确的逻辑”这一哲学立场。

## 目录

- 1. 简介 (Introduction)
- 2. 语言 (Language)
    - 2.1 构件 (Building blocks)
    - 2.2 原子公式 (Atomic formulas)
    - 2.3 复合公式 (Compound formulas)
    - 2.4 句法特征 (Features of the syntax)
- 3. 演绎 (Deduction)
- 4. 语义学 (Semantics)
- 5. 元理论 (Meta-theory)
- 6. 唯一正确的逻辑？ (The One Right Logic?)
    - 6.1 经典一阶逻辑的竞争对手 (Rivals to classical, first-order logic)
    - 6.2 经典一阶逻辑的子逻辑 (Sublogics of classical, first-order logic)
- 参考文献 (Bibliography)
- 延伸阅读 (Further Reading)
- 学术工具 (Academic Tools)
- 其他网络资源 (Other Internet Resources)
- 相关词条 (Related Entries)

## 1. 简介

今天，逻辑既是数学的一个分支，也是哲学的一个分支。在大多数大型大学里，这两个系都开设逻辑课程，且彼此之间通常有很多重叠。形式语言、演绎系统和模型论语义学是数学对象，因此，逻辑学家对它们的数学属性和关系感兴趣。可靠性、完全性以及下面报告的大多数其他结果都是典型的例子。在哲学上，逻辑至少与正确推理的研究密切相关。推理是一种认知性的心理活动。所以逻辑至少与认识论密切结盟。逻辑也是计算机科学的一个核心分支，部分原因是逻辑系统中有趣的计算关系，部分原因是形式演绎论证与推理之间的紧密联系（参见关于递归函数、可计算性与复杂性以及计算机科学哲学的词条）。

这就引发了关于逻辑的各种数学方面的哲学相关性的问题。作为固定字母表上字符串集合的形式语言的属性——可推导性和有效性——如何与正确推理相关联？下面报告的数学结果与关于有效推理的原始哲学问题有什么关系？这是解释数学如何应用于非数学现实这一哲学问题的一个实例。

通常，普通的演绎推理发生在自然语言中，或者可能是在增加了某些数学符号的自然语言中。所以我们的问题始于自然语言与形式语言之间的关系。在不试图全面阐述的情况下，简述关于此事的几种观点可能会有所帮助。

一种观点认为，形式语言准确地展示了自然语言某些片段的实际特征。一些哲学家声称，自然语言的陈述句具有潜在的逻辑形式，而这些形式由形式语言的公式展示出来。其他作者认为，（成功的）陈述句表达命题；而形式语言的公式以某种方式展示这些命题的形式。在这样的观点看来，逻辑的组成部分提供了正确推理的潜在深层结构。如果自然语言句子背后的形式构成了一个有效或可推导的论证，那么这一段自然语言推理就是正确的。例如，参见 Montague [1974], Davidson [1984], Lycan [1984]（以及关于逻辑形式的词条）。

另一种观点，至少部分由戈特洛布·弗雷格（Gottlob Frege）和威廉·莱布尼茨（Wilhelm Leibniz）持有，认为由于自然语言充满了模糊性和歧义，应该用形式语言取而代之。W. V. O. 奎因（W. V. O. Quine）（例如，[1960], [1986]）持有的类似观点是，自然语言应该被规范化（regimented），清理干净以便进行严肃的科学和形而上学工作。这项事业的一个愿望是，规范化语言中的逻辑结构应当是透明的。应该很容易“读出”每个句子的逻辑属性。规范化语言在句法的明确严谨性和真值条件等方面类似于形式语言。

在这样的观点看来，可推导性和有效性代表了自然语言中正确推理的理想化。一段推理是正确的，只要它对应于，或者可以被规范化为，形式语言中的一个有效或可推导的论证。

当数学家和许多哲学家从事演绎推理时，他们偶尔会援引形式语言中的公式来帮助消除歧义，或者以其他方式澄清他们的意思。换句话说，有时形式语言中的公式被用于普通推理中。这表明人们可以将形式语言视为自然语言的附录。那么我们现在的问题涉及这个附录与原始语言之间的关系。在这个附录上清晰定义的可推导性和有效性，告诉了我们关于一般正确演绎推理的什么信息？

另一种观点是，形式语言是自然语言的数学模型，其意义大致类似于质点集合是物理对象系统的模型，或者玻尔结构是原子的模型。换句话说，形式语言展示了自然语言的某些特征或其理想化，同时忽略或简化了其他特征。数学模型的目的是阐明它们所模拟的事物，而不声称模型在所有方面都是准确的，也不声称模型应该取代它所模拟的事物。在这样的观点看来，可推导性和有效性代表了自然语言中正确推理（或许是不同方面）的数学模型。正确的演绎推理片段大致对应于有效或可推导的论证；不正确的推理片段大致对应于无效或不可推导的论证。例如，参见 Corcoran [1973], Shapiro [1998], 和 Cook [2002]。

这里不需要裁决这件事。也许真理在于上述选项的结合，或者也许其他某个选项是正确或最具启发性的。我们提出这件事只是为了给随后的形式处理增添一些哲学视角。

## 2. 语言

在这里，我们开发形式语言的基础，或者准确地说，是一类形式语言。同样，形式语言是固定字母表上递归定义的字符串集合。形式语言的某些方面对应于像英语这样的自然语言，或者在自然语言中有对应物。从技术上讲，这种“对应关系”不是形式开发的一部分，但我们会不时提及它，以激发某些特征和结果。

我们从*单数词项*（singular terms）的类似物开始，这些语言项的功能是表示一个人或物体。我们称这些为*词项*（terms）。我们假设有一组*个体常项*（individual constants）。这些是罗马字母表开头附近的小写字母，带或不带数字下标：

$$ a, b, c, \ldots, a_1, b_1, c_1, \ldots $$

我们设想有潜在无限多个体常项。在目前的系统中，每个常项都是单个字符，因此个体常项没有内部句法。因此我们有一个无限的字母表。这可以通过采用像 $d_{22}$ 这样的常项来避免，例如，它由三个字符组成，一个小写“$d$”后跟一对下标“2”。

我们还假设有一组*个体变项*（individual variables）。这些是字母表末尾附近的小写字母，带或不带数字下标：

$$ u, v, w, x, y, z, \ldots, u_1, v_1, w_1, x_1, y_1, z_1, \ldots $$

在普通的数学推理中，词项需要履行两个功能。我们需要能够表示特定的但未指定的（或任意的）对象，有时我们需要表达普遍性。在我们的系统中，我们使用一些常项来充当未指定指称的角色，并使用变项来表达普遍性。这两种用法在下面的形式处理中都有重述。一些逻辑学家使用不同的符号来表示未指定的对象（有时称为“个体参数”）和用于表达普遍性的变项。

常项和变项是我们形式语言中唯一的词项，所以我们所有的词项都是简单的，对应于专有名词和代词的某些用法。如果一个词项不是变项，我们称其为封闭的。一般来说，我们使用 $v$ 来表示变项，使用 $t$ 来表示封闭词项（即个体常项）。一些作者还引入了*函数字母*（function letters），允许对应于“$7+4$”和“比尔·克林顿的妻子”这样的复杂词项，或者包含变项的复杂词项，如“$x$的父亲”和“$x/y$”。针对数学家的逻辑书籍可能会包含函数字母，这可能是由于函数在数学论述中的核心地位。针对更广泛受众（或哲学学生）的书籍可能会省略函数字母，因为这简化了句法和理论。我们在这里遵循后一种路线。这是在展示具有更强表达资源的系统与使形式处理更复杂之间进行权衡的一个例子。

对于每个自然数 $n$，我们引入一组 $n$-元*谓词字母*（predicate letters）。这些是字母表开头或中间的大写字母。上标表示位置的数量，可能有也可能没有下标。例如，

$$ A^3, B^3, C^3, \ldots $$

是三元谓词字母。当不会引起混淆时，我们通常省略上标。我们还添加了一个特殊的二元谓词符号“$=$”表示同一性。

零元谓词字母有时被称为“句子字母”。它们对应于内部结构无关紧要的独立句子。一元谓词字母，称为“单子谓词字母”（monadic predicate letters），对应于表示属性的语言项，如“是人”、“是红色的”或“是质数”。二元谓词字母，称为“二元谓词字母”（binary predicate letters），对应于表示二元关系的语言项，如“是...的父母”或“大于”。三元谓词字母对应于三元关系，如“位于...之间的直线上”。依此类推。

语言的*非逻辑术语*由其个体常项和谓词字母组成。符号“$=$”（同一性）不是非逻辑符号。通过将同一性视为逻辑的，我们在演绎系统和模型论语义学中为其提供了明确的处理。大多数作者都这样做，但在这个问题上存在一些争议（Quine [1986, Chapter 5]）。如果 $K$ 是一组常项和谓词字母，那么我们给出了建立在这组非逻辑术语之上的语言 $\mathcal{L}1K=$ 的基础。它可以被称为关于 $K$ 的*带同一性的一阶语言*。一个缺乏同一性符号（或将同一性视为非逻辑的）的类似语言可以被称为 $\mathcal{L}1K$，即关于 $K$ 的*不带同一性的一阶语言*。

如果 $V$ 是 $K$ 中的一个 $n$-元谓词字母，且 $t_1, \ldots, t_n$ 是 $K$ 的词项，则 $Vt_1 \ldots t_n$ 是 $\mathcal{L}1K=$ 的一个*原子公式*。注意，词项 $t_1, \ldots, t_n$ 不必是不同的。原子公式的例子包括：

$$ Pa, \quad Qx, \quad Rab, \quad Aabc $$

最后一个是某种关系 $(A)$ 在三个对象 $(a, b, c)$ 之间成立的陈述的类似物。如果 $t_1$ 和 $t_2$ 是词项，那么 $t_1 = t_2$ 也是 $\mathcal{L}1K=$ 的原子公式。它对应于 $t_1$ 等同于 $t_2$ 的断言。

如果一个原子公式没有变项，则称为*原子句子*。如果有变项，则称为*开放的*。在上面的例子列表中，第一个和第二个是开放的；其余的是句子。

我们现在引入词汇表的最后几项：

$$ \neg, \quad \&, \quad \vee, \quad \rightarrow, \quad \leftrightarrow, \quad \forall, \quad \exists, \quad (, \quad ) $$

我们给出 $\mathcal{L}1K=$ 的*公式*的递归定义：

1. $\mathcal{L}1K=$ 的所有原子公式都是 $\mathcal{L}1K=$ 的公式。
2. 如果 $\theta$ 是 $\mathcal{L}1K=$ 的公式，那么 $\neg \theta$ 也是。

对应于 $\neg \theta$ 的公式因此表示“并非 $\theta$ 的情况”。符号“$\neg$”称为“否定”，是一个一元联结词。

3. 如果 $\theta$ 和 $\psi$ 是 $\mathcal{L}1K=$ 的公式，那么 $(\theta \& \psi)$ 也是。

符号“$\&$”对应于英语中的“和”（当“和”用于连接句子时）。所以 $(\theta \& \psi)$ 可以读作“$\theta$ 和 $\psi$”。公式 $(\theta \& \psi)$ 称为 $\theta$ 和 $\psi$ 的“合取”。

4. 如果 $\theta$ 和 $\psi$ 是 $\mathcal{L}1K=$ 的公式，那么 $(\theta \vee \psi)$ 也是。

符号“$\vee$”对应于“或者...或者...或者两者兼有”，所以 $(\theta \vee \psi)$ 可以读作“$\theta$ 或 $\psi$”。公式 $(\theta \vee \psi)$ 称为 $\theta$ 和 $\psi$ 的“析取”。

5. 如果 $\theta$ 和 $\psi$ 是 $\mathcal{L}1K=$ 的公式，那么 $(\theta \rightarrow \psi)$ 也是。

箭头“$\rightarrow$”大致对应于“如果...那么...”，所以 $(\theta \rightarrow \psi)$ 可以读作“如果 $\theta$ 那么 $\psi$”或“$\theta$ 仅当 $\psi$”。

符号“$\&$”、“$\vee$”和“$\rightarrow$”称为“二元联结词”，因为它们用于将两个公式“连接”成一个。一些作者引入 $(\theta \leftrightarrow \psi)$ 作为 $((\theta \rightarrow \psi) \& (\psi \rightarrow \theta))$ 的缩写。符号“$\leftrightarrow$”是“当且仅当”这一短语的类似物。

6. 如果 $\theta$ 是 $\mathcal{L}1K=$ 的公式且 $v$ 是一个变项，那么 $\forall v \theta$ 是 $\mathcal{L}1K=$ 的公式。

符号“$\forall$”称为*全称量词*，是“对于所有”的类似物；所以 $\forall v \theta$ 可以读作“对于所有 $v$，$\theta$”。

7. 如果 $\theta$ 是 $\mathcal{L}1K=$ 的公式且 $v$ 是一个变项，那么 $\exists v \theta$ 是 $\mathcal{L}1K=$ 的公式。

符号“$\exists$”称为*存在量词*，是“存在”或“有一个”的类似物；所以 $\exists v \theta$ 可以读作“存在一个 $v$ 使得 $\theta$”。

8. 就这些了。也就是说，所有公式都是根据规则 (1)–(7) 构造的。

条款 (8) 允许我们对公式的复杂性进行归纳。如果某个属性对原子公式成立，并且在条款 (2)–(7) 的操作下封闭，那么该属性对所有公式成立。这里有一个简单的例子：

> **定理 1**。 $\mathcal{L}1K=$ 的每个公式具有相同数量的左括号和右括号。此外，每个左括号对应一个唯一的右括号，该右括号位于左括号的右侧。同样，每个右括号对应一个唯一的左括号，该左括号位于给定右括号的左侧。如果一个括号出现在一对匹配的括号之间，那么它的配对也出现在那一对匹配的括号内。换句话说，出现在一对匹配括号内的括号本身也是匹配的。

> **证明**：根据条款 (8)，每个公式都是使用条款 (2)–(7) 从原子公式构建的。原子公式没有括号。括号仅在条款 (3)–(5) 中引入，每次它们都是作为匹配的集合引入的。所以在公式构造的任何阶段，括号都是成对出现的。

我们接下来定义公式中变项出现的*自由*或*约束*的概念。紧跟在量词后面的变项（如在“$\forall x$”和“$\exists y$”中）既不是自由的也不是约束的。我们甚至不认为那是变项的出现。出现在原子公式中的所有变项都是自由的。如果一个变项在 $\theta$ 或 $\psi$ 中自由（或约束）出现，那么同一出现也在 $\neg \theta, (\theta \& \psi), (\theta \vee \psi)$ 和 $(\theta \rightarrow \psi)$ 中是自由（或约束）的。也就是说，（一元和二元）联结词不会改变其中出现的变项的状态。变项 $v$ 在 $\theta$ 中的所有出现在 $\forall v \theta$ 和 $\exists v \theta$ 中都是约束的。$v$ 在 $\theta$ 中的任何*自由*出现都被初始量词约束。出现在 $\theta$ 中的所有其他变项在 $\forall v \theta$ 和 $\exists v \theta$ 中是自由或约束的，正如它们在 $\theta$ 中一样。

例如，在公式 $(\forall x(Axy \vee Bx) \& Bx)$ 中，“$x$”在 $Axy$ 和第一个 $Bx$ 中的出现被量词约束。“$y$”的出现和“$x$”的最后一次出现是自由的。在 $\forall x(Ax \rightarrow \exists xBx)$ 中，$Ax$ 中的“$x$”被初始全称量词约束，而 $x$ 的另一次出现被存在量词约束。上述句法允许这种“双重约束”。虽然它不会产生任何歧义（见下文），但为了品味和清晰起见，我们将避免此类公式。

句法还允许所谓的空约束，如 $\forall xBc$。在下文中也将避免这种情况。一些逻辑处理在句法上排除了空约束和双重约束。这简化了下面的一些处理，并使其他处理复杂化。

自由变项对应于占位符，而约束变项用于表达普遍性。如果一个公式没有自由变项，则称为*句子*。如果一个公式有自由变项，则称为*开放的*。

在转向演绎系统和语义学之前，我们要提到迄今为止开发的语言的一些特征。这有助于区分形式语言与像英语这样的自然语言。

我们首先假设所有类别都是不相交的。例如，没有联结词同时是量词或变项，非逻辑词项也不是括号或联结词。此外，每个类别内的项目也是不同的。例如，析取符号不兼作否定符号，也许更重要的是，没有二元谓词同时是一元谓词。

像英语这样的自然语言与像 $\mathcal{L}1K=$ 这样的形式语言之间的一个区别是，后者不应有任何歧义。符号的不同类别不重叠以及没有符号兼职的政策，避免了有时称为“多义性”（equivocation）的歧义，即一个词有两个含义：“我要去银行（bank，也指河岸）。”但还有其他种类的歧义。考虑英语句子：

> John is married, and Mary is single, or Joe is crazy.

它可以意味着约翰已婚，并且玛丽单身或乔疯了；或者它可以意味着约翰已婚且玛丽单身，或者乔疯了。像这样的歧义，由于解析同一句子的方式不同，有时被称为“结构歧义”（amphiboly）。如果我们的形式语言中没有括号，它就会有结构歧义。例如，会有一个“公式” $A \& B \vee C$。这应该是 $((A \& B) \vee C)$，还是 $(A \& (B \vee C))$？括号解决了本可能成为结构歧义的问题。

我们可以确定我们的语言中没有其他结构歧义吗？也就是说，我们可以确定 $\mathcal{L}1K=$ 的每个公式只能以一种方式组合吗？我们的下一个任务是回答这个问题。

让我们暂时使用术语“一元标记”来指代否定符号 $(\neg)$ 或后跟变项的量词（例如，$\forall x, \exists z$）。

> **引理 2**。每个公式由零个或多个一元标记组成的字符串，后跟一个原子公式或通过条款 (3)–(5) 之一使用二元联结词生成的公式组成。

> **证明**：我们对公式的复杂性进行归纳，或者换句话说，对应用的形成规则的数量进行归纳。该引理显然对原子公式成立。设 $n$ 是一个自然数，并假设该引理对由 $n$ 个或更少条款 (2)–(7) 实例构成的任何公式成立。设 $\theta$ 是由 $n+1$ 个实例构成的公式。如果用于构造 $\theta$ 的最后一个条款是 (3)、(4) 或 (5)，则该引理成立。如果用于构造 $\theta$ 的最后一个条款是 (2)，则 $\theta$ 是 $\neg \psi$。由于 $\psi$ 是用 $n$ 个规则实例构成的，因此该引理对 $\psi$ 成立（通过归纳假设），因此它对 $\theta$ 成立。类似的推理表明，如果最后一个条款是 (6) 或 (7)，则该引理对 $\theta$ 成立。根据条款 (8)，这穷尽了所有情况，因此通过归纳，该引理对 $\theta$ 成立。

> **引理 3**。如果公式 $\theta$ 包含左括号，则它以右括号结尾，该右括号与 $\theta$ 中最左边的左括号匹配。

> **证明**：这里我们也对用于构造公式的 (2)–(7) 实例的数量进行归纳。显然，该引理对原子公式成立，因为它们没有括号。假设该引理对用 $n$ 个或更少 (2)–(7) 实例构造的公式成立，并设 $\theta$ 是用 $n+1$ 个实例构造的。如果应用的最后一个条款是 (3)–(5)，则该引理成立，因为 $\theta$ 本身以左括号开头并以匹配的右括号结尾。如果应用的最后一个条款是 (2)，则 $\theta$ 是 $\neg \psi$，归纳假设适用于 $\psi$。同样，如果应用的最后一个条款是 (6) 或 (7)，则 $\theta$ 由量词、变项和我们可以应用归纳假设的公式组成。由此可知，该引理对 $\theta$ 成立。

> **引理 4**。每个公式至少包含一个原子公式。

证明通过对用于构造公式的 (2)–(7) 实例的数量进行归纳来进行，我们将其留作练习。

> **定理 5**。设 $\alpha, \beta$ 是我们字母表上的非空字符序列，使得 $\alpha \beta$（即 $\alpha$ 后跟 $\beta$）是一个公式。那么 $\alpha$ *不是*一个公式。

> **证明**：根据定理 1 和引理 3，如果 $\alpha$ 包含左括号，则与 $\alpha \beta$ 中最左边的左括号匹配的右括号位于 $\alpha \beta$ 的末尾，因此匹配的右括号在 $\beta$ 中。所以，$\alpha$ 的左括号比右括号多。根据定理 1，$\alpha$ 不是公式。现在假设 $\alpha$ 不包含任何左括号。根据引理 2，$\alpha \beta$ 由零个或多个一元标记组成的字符串，后跟原子公式或通过条款 (3)–(5) 之一使用二元联结词生成的公式组成。如果后一个公式是通过条款 (3)–(5) 之一生成的，则它以左括号开头。由于 $\alpha$ 不包含任何括号，它必须是一串一元标记。但那样 $\alpha$ 就不包含任何原子公式，因此根据引理 4，$\alpha$ 不是公式。剩下的唯一情况是 $\alpha \beta$ 由一串一元标记后跟原子公式组成，形式为 $t_1 = t_2$ 或 $Pt_1 \ldots t_n$。同样，如果 $\alpha$ 仅由一元标记组成，它就不是公式，因此 $\alpha$ 必须由开始 $\alpha \beta$ 的一元标记，后跟单独的 $t_1$，单独的 $t_1 =$，或谓词字母 $P$，以及可能一些（但不是全部）词项 $t_1, \ldots, t_n$ 组成。在前两种情况下，根据类别不重叠的政策，$\alpha$ 不包含原子公式。由于 $P$ 是 $n$-元谓词字母，根据谓词字母不同的政策，$P$ 不是任何 $m \neq n$ 的 $m$-元谓词字母。所以 $\alpha$ 中由 $P$ 后跟词项组成的部分不是原子公式。在所有这些情况下，$\alpha$ 都不包含原子公式。根据引理 4，$\alpha$ 不是公式。

我们终于可以证明我们的语言中没有结构歧义。

> **定理 6**。设 $\theta$ 是 $\mathcal{L}1K=$ 的任意公式。如果 $\theta$ 不是原子的，则在 (2)–(7) 中有且仅有一个是用于构造 $\theta$ 的最后一个条款。也就是说，$\theta$ 不可能是由两个不同的条款生成的。此外，由条款 (2)–(7) 生成的公式都不是原子的。

> **证明**：根据条款 (8)，要么 $\theta$ 是原子的，要么它是由 (2)–(7) 之一生成的。因此，$\theta$ 中的第一个符号必须是谓词字母、词项、一元标记或左括号。如果 $\theta$ 中的第一个符号是谓词字母或词项，则 $\theta$ 是原子的。在这种情况下，$\theta$ 不是由 (2)–(7) 中的任何一个生成的，因为所有这些公式都以谓词字母或词项以外的内容开头。如果 $\theta$ 中的第一个符号是否定符号“$\neg$”，那么 $\theta$ 是由条款 (2) 生成的，而不是由任何其他条款生成的（因为其他条款生成的公式以量词或左括号开头）。同样，如果 $\theta$ 以全称量词开头，则它是由条款 (6) 生成的，而不是由任何其他条款生成的；如果 $\theta$ 以存在量词开头，则它是由条款 (7) 生成的，而不是由任何其他条款生成的。剩下的唯一情况是 $\theta$ 以左括号开头。在这种情况下，它必须是由 (3)–(5) 之一生成的，而不是由任何其他条款生成的。我们只需要排除 $\theta$ 是由 (3)–(5) 中的不止一个生成的可能性。举个例子，假设 $\theta$ 是由 (3) 和 (4) 生成的。那么 $\theta$ 是 $(\psi_1 \& \psi_2)$，且 $\theta$ 也是 $(\psi_3 \vee \psi_4)$，其中 $\psi_1, \psi_2, \psi_3$ 和 $\psi_4$ 本身也是公式。也就是说，$(\psi_1 \& \psi_2)$ 与 $(\psi_3 \vee \psi_4)$ 是同一个公式。根据定理 5，$\psi_1$ 不能是 $\psi_3$ 的真部分，$\psi_3$ 也不能是 $\psi_1$ 的真部分。所以 $\psi_1$ 必须与 $\psi_3$ 是同一个公式。但那样“$\&$”必须与“$\vee$”是同一个符号，这与所有符号都不同的政策相矛盾。所以 $\theta$ 不是同时由条款 (3) 和条款 (4) 生成的。类似的推理可以处理其他组合。

这个结果有时被称为“唯一可读性”。它表明每个公式都是通过各种条款以确切的一种方式从原子公式生成的。如果 $\theta$ 是由条款 (2) 生成的，那么它的*主联结词*是初始的“$\neg$”。如果 $\theta$ 是由条款 (3)、(4) 或 (5) 生成的，那么它的*主联结词*分别是引入的“$\&$”、“$\vee$”或“$\rightarrow$”。如果 $\theta$ 是由条款 (6) 或 (7) 生成的，那么它的*主联结词*是初始量词。我们为这些枯燥的细节道歉。我们包含它们是为了表明句法的精确度和严谨性水平。
## 3. 演绎 (Deduction)

我们现在为我们的语言引入一个演绎系统 $D$。如上所述，我们将论证定义为形式语言中非空句子的集合，其中一个被指定为结论。如果论证中还有其他句子，它们就是前提。按照惯例，我们使用“$\Gamma$”、“$\Gamma'$”、“$\Gamma_1$”等来表示句子集合，使用字母“$\phi$”、“$\psi$”、“$\theta$”（大写或小写，带或不带下标）来表示单个句子。我们写“$\Gamma, \Gamma'$”表示 $\Gamma$ 和 $\Gamma'$ 的并集，写“$\Gamma, \phi$”表示 $\Gamma$ 与 $\{\phi\}$ 的并集。

我们将论证写成 $\langle \Gamma, \phi \rangle$ 的形式，其中 $\Gamma$ 是一组句子（前提），$\phi$ 是一个句子（结论）。请记住 $\Gamma$ 可能为空。我们写 $\Gamma \vdash \phi$ 来表示 $\phi$ 可以从 $\Gamma$ 导出，或者换句话说，论证 $\langle \Gamma, \phi \rangle$ 在 $D$ 中是可导出的。我们可以写 $\Gamma \vdash_D \phi$ 来强调演绎系统 $D$。我们写 $\vdash \phi$ 或 $\vdash_D \phi$ 来表示 $\phi$ 可以（在 $D$ 中）从空前提集导出。

$D$ 中的规则被选择来匹配与语言中逻辑术语的英语对应物有关的逻辑关系。同样，我们通过递归定义可导性关系。我们从一个假设规则开始：

(As) 如果 $\phi$ 是 $\Gamma$ 的成员，那么 $\Gamma \vdash \phi$。

因此我们要有 $\{\phi \} \vdash \phi$；每个前提都由其自身得出。接下来，我们为每个联结词和量词提出两个条款。这些条款指明了如何“引入”和“消除”以每个符号为主联结词的句子。

首先，回想一下“$\&$”是英语联结词“和”（and）的类似物。直观地说，如果人们推导出了 $\theta$ 并且推导出了 $\psi$，那么就可以推导出形式为 $(\theta \& \psi)$ 的句子。反之，人们可以从 $(\theta \& \psi)$ 推导出 $\theta$，也可以从 $(\theta \& \psi)$ 推导出 $\psi$：

$(\& \mathrm{I})$
如果 $\Gamma_1 \vdash \theta$ 且 $\Gamma_2 \vdash \psi$，那么 $\Gamma_1, \Gamma_2 \vdash (\theta \& \psi)$。

$(\& \mathrm{E})$
如果 $\Gamma \vdash (\theta \& \psi)$ 那么 $\Gamma \vdash \theta$；如果 $\Gamma \vdash (\theta \& \psi)$ 那么 $\Gamma \vdash \psi$。

名称“&I”代表“&-引入”；“&E”代表“&-消除”。

既然符号“$\vee$”对应于英语的“或”（or），$(\theta \vee \psi)$ 应该可以从 $\theta$ 导出，且 $(\theta \vee \psi)$ 也应该可以从 $\psi$ 导出：

$(\vee \mathrm{I})$
如果 $\Gamma \vdash \theta$ 那么 $\Gamma \vdash (\theta \vee \psi)$；如果 $\Gamma \vdash \psi$ 那么 $\Gamma \vdash (\theta \vee \psi)$。

消除规则稍微复杂一些。假设“$\theta$ 或 $\psi$”为真。再假设 $\phi$ 从 $\theta$ 得出，且 $\phi$ 从 $\psi$ 得出。人们可以推断，如果 $\theta$ 为真，那么 $\phi$ 为真。如果反之 $\psi$ 为真，我们要有 $\phi$ 为真。所以无论哪种方式，$\phi$ 必须为真。

$(\vee \mathrm{E})$
如果 $\Gamma_1 \vdash (\theta \vee \psi), \Gamma_2, \theta \vdash \phi$ 且 $\Gamma_3, \psi \vdash \phi$，那么 $\Gamma_1, \Gamma_2, \Gamma_3 \vdash \phi$。

对于接下来的条款，回想一下符号“$\rightarrow$”是英语“如果...那么...”结构的类似物。如果人们知道或假设 $(\theta \rightarrow \psi)$ 并且也知道或假设 $\theta$，那么人们可以得出 $\psi$。反之，如果人们从假设 $\theta$ 推导出 $\psi$，那么人们可以得出 $(\theta \rightarrow \psi)$。

$({\rightarrow}\mathrm{I})$
如果 $\Gamma, \theta \vdash \psi$，那么 $\Gamma \vdash (\theta \rightarrow \psi)$。

$({\rightarrow}\mathrm{E})$
如果 $\Gamma_1 \vdash (\theta \rightarrow \psi)$ 且 $\Gamma_2 \vdash \theta$，那么 $\Gamma_1, \Gamma_2 \vdash \psi$。

这个消除规则有时被称为“肯定前件”（modus ponens）。在一些逻辑教科书中，引入规则被证明为“演绎定理”。

我们接下来的条款是针对否定符号“$\neg$”的。其基本思想是句子 $\psi$ 与其否定 $\neg \psi$ 是不一致的。它们不可能都为真。我们称一对句子 $\psi, \neg \psi$ 为矛盾对立面。如果人们可以从假设 $\theta$ 推导出这样一对句子，那么人们可以得出 $\theta$ 为假，或者换句话说，人们可以得出 $\neg \theta$。

$(\neg \mathrm{I})$
如果 $\Gamma_1, \theta \vdash \psi$ 且 $\Gamma_2, \theta \vdash \neg \psi$，那么 $\Gamma_1, \Gamma_2 \vdash \neg \theta$。

根据 (As)，我们有 $\{A, \neg A\} \vdash A$ 和 $\{A, \neg A\} \vdash \neg A$。所以根据 $\neg$I 我们有 $\{A\} \vdash \neg \neg A$。然而，我们还没有逆命题。直观地说，$\neg \neg \theta$ 对应于“并非并非...的情况”。人们可能会认为这最后等同于 $\theta$，我们要有一个具有该效果的规则：

(DNE)
如果 $\Gamma \vdash \neg \neg \theta$，那么 $\Gamma \vdash \theta$。

名称 DNE 代表“双重否定消除”。关于这个推论存在一些争议。它被那些不认为每个有意义的句子要么为真要么不为真的哲学家和数学家所拒绝。直觉主义逻辑（Intuitionistic logic）不认可有问题的推论（例如，参见 Dummett [2000]，或关于直觉主义逻辑或直觉主义逻辑历史的词条），但是，再次强调，经典逻辑认可。

为了说明迄今为止提出的演绎系统 $D$ 的部分，我们展示 $\vdash (A \vee \neg A)$：

1. $\{\neg(A \vee \neg A), A\} \vdash \neg(A \vee \neg A)$，根据 (As)
2. $\{\neg(A \vee \neg A), A\} \vdash A$，根据 (As)。
3. $\{\neg(A \vee \neg A), A\} \vdash (A \vee \neg A)$，根据 $(\vee$I)，来自 (ii)。
4. $\{\neg(A \vee \neg A)\} \vdash \neg A$，根据 $(\neg$I)，来自 (i) 和 (iii)。
5. $\{\neg(A \vee \neg A), \neg A\} \vdash \neg(A \vee \neg A)$，根据 (As)
6. $\{\neg(A \vee \neg A), \neg A\} \vdash \neg A$，根据 (As)
7. $\{\neg(A \vee \neg A), \neg A\} \vdash (A \vee \neg A)$，根据 $(\vee$I)，来自 (vi)。
8. $\{\neg(A \vee \neg A)\} \vdash \neg \neg A$，根据 $(\neg$I)，来自 (v) 和 (vii)。
9. $\vdash \neg \neg(A \vee \neg A)$，根据 $(\neg$I)，来自 (iv) 和 (viii)。
10. $\vdash (A \vee \neg A)$，根据 (DNE)，来自 (ix)。

原则 $(\theta \vee \neg \theta)$ 有时被称为排中律。它在直觉主义逻辑中是无效的。

设 $\theta, \neg \theta$ 是一对矛盾对立面，设 $\psi$ 是任何句子。根据 (As) 我们有 $\{\theta, \neg \theta, \neg \psi \} \vdash \theta$ 和 $\{\theta, \neg \theta, \neg \psi \} \vdash \neg \theta$。所以根据 $(\neg$I)，$\{\theta, \neg \theta \} \vdash \neg \neg \psi$。所以，根据 (DNE) 我们有 $\{\theta, \neg \theta \} \vdash \psi$。也就是说，任何事物都可以从一对矛盾对立面得出。一些逻辑学家引入一条规则来编纂类似的推论：

如果 $\Gamma_1 \vdash \theta$ 且 $\Gamma_2 \vdash \neg \theta$，那么对于任何句子 $\psi, \Gamma_1, \Gamma_2 \vdash \psi$

这个推论有时被称为 *ex falso quodlibet*（由假得全），或者更形象地称为“爆炸”。有些人称之为“$\neg$-消除”，但这可能稍微扩展了“消除”的概念。我们在 $D$ 中并未正式包含 *ex falso quodlibet* 作为单独的规则，但如下所示（定理 10），它的每个实例在我们的系统 $D$ 中都是可导出的。

一些逻辑学家反对 *ex falso quodlibet*，理由是句子 $\psi$ 可能与 $\Gamma$ 中的任何前提都不相关。例如，假设一个人从关于人性和关于某些人的事实的一些前提 $\Gamma$ 开始，然后推导出了“克林顿有婚外性关系”和“克林顿没有婚外性关系”这两个句子。人们或许可以得出结论，前提 $\Gamma$ 有问题。但是我们应该被允许从 $\Gamma$ 推导出任何东西吗？我们应该被允许推导出“经济是稳健的”吗？

少数被称为双面真理主义者（dialetheists）的逻辑学家认为，某些矛盾实际上是真的。对他们来说，*ex falso quodlibet* 不是保真的。

反对 *ex falso quodlibet* 的演绎系统被称为次协调的（paraconsistent）。大多数相关逻辑（relevant logics）都是次协调的。参见关于相关逻辑、次协调逻辑和双面真理主义的词条。或者参见 Anderson 和 Belnap [1975], Anderson, Belnap, 和 Dunn [1992], 以及 Tennant [1997] 关于相关逻辑的更全面概述；以及 Priest [2006a,b] 关于双面真理主义的概述。这涉及关于逻辑后承本质的深刻哲学问题。作为哲学百科全书中的一篇文章，很难避免哲学问题，但篇幅限制排除了在这里对此问题进行更全面的处理。只要指出推论 *ex falso quodlibet* 在经典逻辑系统中得到认可就足够了，这也是本文的主题。它对于建立演绎系统与语义学之间的平衡至关重要（见下文 §5）。

$D$ 的下一部分是量词的条款。设 $\theta$ 是一个公式，$v$ 是一个变项，$t$ 是一个词项（即，变项或常项）。然后定义 $\theta(v|t)$ 为将 $\theta$ 中 $v$ 的每个自由出现替换为 $t$ 的结果。所以，如果 $\theta$ 是 $(Qx \& \exists xPxy)$，那么 $\theta(x|c)$ 就是 $(Qc \& \exists xPxy)$。$x$ 的最后一次出现不是自由的。

形式为 $\forall v \theta$ 的句子是英语“对于每个 $v, \theta$ 成立”的类似物。所以人们应该能够从 $\forall v \theta$ 推断出 $\theta(v|t)$，对于任何封闭词项 $t$。回想一下，我们在系统中的唯一封闭词项是常项。

$(\forall \mathrm{E})$
如果 $\Gamma \vdash \forall v \theta$，那么 $\Gamma \vdash \theta(v|t)$，对于任何封闭词项 $t$。

这里的想法是，如果 $\forall v \theta$ 为真，那么无论 $t$ 是什么，$\theta$ 对 $t$ 都应该成立。

全称量词的引入条款稍微复杂一些。假设句子 $\theta$ 包含封闭词项 $t$，并且 $\theta$ 已从一组前提 $\Gamma$ 推导出来。如果封闭词项 $t$ 不出现在 $\Gamma$ 的任何成员中，那么无论 $t$ 可能表示哪个对象，$\theta$ 都将成立。也就是说，$\forall v \theta$ 成立。

$(\forall \mathrm{I})$
对于任何封闭词项 $t$，如果 $\Gamma \vdash \theta (v|t)$，那么 $\Gamma \vdash \forall v\theta$，前提是 $t$ 不在 $\Gamma$ 或 $\theta$ 中。

这个规则 $(\forall \mathbf{I})$ 对应于数学中的常见推论。假设一位数学家说“设 $n$ 为自然数”，并接着证明 $n$ 具有某种属性 $P$，而不假设关于 $n$ 的任何事情（除了它是自然数）。然后她提醒读者 $n$ 是“任意的”，并得出结论 $P$ 对所有自然数成立。词项 $t$ 不出现在任何前提中的条件保证了它确实是“任意的”。它可以是任何对象，所以我们关于它的任何结论对所有对象都成立。

存在量词是英语表达“存在”（there exists），或者也许只是“有”（there is）的类似物。如果我们已经确定（或假设）给定对象 $t$ 具有给定属性，那么就可以得出结论：有东西具有该属性。

$(\exists \mathrm{I})$
对于任何封闭词项 $t$，如果 $\Gamma \vdash \theta (v|t)$ 那么 $\Gamma \vdash \exists v\theta$。

$\exists$ 的消除规则并不那么简单：

$(\exists \mathrm{E})$
对于任何封闭词项 $t$，如果 $\Gamma_1 \vdash \exists v\theta$ 且 $\Gamma_2, \theta(v|t) \vdash \phi$，那么 $\Gamma_1, \Gamma_2 \vdash \phi$，前提是 $t$ 不出现在 $\phi$、$\Gamma_2$ 或 $\theta$ 中。

这个消除规则也对应于一种常见的推论。假设一位数学家假设或以某种方式得出结论：存在一个具有给定属性 $P$ 的自然数。然后她说“设 $n$ 为这样一个自然数，使得 $Pn$”，并接着建立一个不提及数字 $n$ 的句子 $\phi$。如果 $\phi$ 的推导不涉及关于 $n$ 的任何事情（除了它具有给定属性 $P$ 的假设），那么 $n$ 可能是任何具有属性 $P$ 的数字。也就是说，$n$ 是一个具有属性 $P$ 的任意数字。$n$ 是哪个数字并不重要。由于 $\phi$ 没有提及 $n$，它从某物具有属性 $P$ 的断言中得出。添加到 $(\exists$E) 的规定是为了保证 $t$ 是“任意的”。

最后的项目是同一性符号“=”的规则。引入规则尽可能简单：

$({=}\mathrm{I})$
$\Gamma \vdash t=t$，其中 $t$ 是任何封闭词项。

这个“推论”对应于万物与其自身同一的公理。消除规则对应于一个原则：如果 $a$ 等同于 $b$，那么对 $a$ 为真的任何事情对 $b$ 也为真。

$({=}\mathrm{E})$
对于任何封闭词项 $t_1$ 和 $t_2$，如果 $\Gamma_1 \vdash t_1 =t_2$ 且 $\Gamma_2 \vdash \theta$，那么 $\Gamma_1, \Gamma_2 \vdash \theta'$，其中 $\theta'$ 是通过用 $t_2$ 替换一个或多个出现的 $t_1$ 从 $\theta$ 获得的。

规则 $({=}\mathrm{E})$ 表明我们语言的表达资源受到一定限制。例如，假设哈利（Harry）等同于唐纳德（Donald）（因为他淘气的父母给了他两个名字）。根据大多数人的直觉，由此和“迪克（Dick）知道哈利是邪恶的”并不能得出“迪克知道唐纳德是邪恶的”，原因是迪克可能不知道哈利等同于唐纳德。这种等同物不能安全地相互替换的语境称为“不透明的”（opaque）。我们假设我们的语言 $\mathcal{L}1K=$ 没有不透明语境。

最后一个条款完成了演绎系统 $D$ 的描述：

(*)
就这些了。$\Gamma \vdash \theta$ 仅当 $\theta$ 根据上述规则从 $\Gamma$ 的成员得出。

同样，这个条款允许对用于建立论证的规则进行归纳证明。如果论证的一个属性对 (As) 和 $({=}\mathrm{I})$ 的所有实例成立，并且如果其他规则保持该属性，那么在 $D$ 中可导出的每个论证都享有该属性。

在继续 $\mathcal{L}1K=$ 的模型论之前，我们暂停注意一下演绎系统的几个特征。为了说明严谨程度，我们从一个引理开始：如果一个句子不包含特定的封闭词项，我们可以对我们证明它的句子集合进行微小的更改而不会出现问题。我们这里允许自己扩展一些以前的符号：对于任何词项 $t$ 和 $t'$，以及任何公式 $\theta$，我们说 $\theta(t|t')$ 是用 $t'$ 替换 $\theta$ 中所有自由出现的 $t$ 的结果。

**引理 7**。如果 $\Gamma_1$ 和 $\Gamma_2$ 的区别仅在于：凡是 $\Gamma_1$ 包含 $\theta$ 的地方，$\Gamma_2$ 包含 $\theta(t|t')$，那么对于任何不包含 $t$ 或 $t'$ 的句子 $\phi$，如果 $\Gamma_1 \vdash \phi$ 那么 $\Gamma_2 \vdash \phi$。

**证明**：证明通过对 $\phi$ 的证明步骤数进行归纳来进行。此证明的关键在于，只要 $\theta$ 不包含 $t$ 或 $t'$，就有 $\theta=\theta(t|t')$。当 $\phi$ 的证明步骤数为一时，这意味着应用的最后（且唯一）规则是 (As) 或 (=I)。那么，由于 $\phi$ 不包含 $t$ 或 $t'$，如果 $\Gamma_1 \vdash \phi$，我们只需对 $\Gamma_2$ 应用相同的规则（(As) 或 (=I)）即可得到 $\Gamma_2 \vdash \phi$。假设 $\phi$ 的证明有 $n>1$ 步，并且引理 7 对任何少于 $n$ 步的证明成立。假设应用于 $\Gamma_1$ 的第 $n$ 个规则是 $(\& I)$。那么 $\phi$ 是 $\psi \& \chi$，且 $\Gamma_1 \vdash \phi \& \chi$。但那时我们知道证明中的先前步骤包括 $\Gamma_1 \vdash \psi$ 和 $\Gamma_1 \vdash \chi$，根据归纳，我们有 $\Gamma_2 \vdash \psi$ 和 $\Gamma_2 \vdash \chi$，因为 $\psi$ 和 $\chi$ 都不包含 $t$ 或 $t'$。所以，我们只需对 $\Gamma_2$ 应用 $(\& I)$ 即可按要求得到 $\Gamma_2 \vdash \psi \& \chi$。现在假设在 $\Gamma_1 \vdash \phi$ 的证明中应用的最后一步是 $(\& E)$。那么，在 $\phi$ 的证明的先前步骤中，我们知道对于某个句子 $\psi$ 有 $\Gamma_1 \vdash \phi \& \psi$。如果 $\psi$ 不包含 $t$，那么我们只需对 $\Gamma_2$ 应用 $(\& E)$ 即可获得所需结果。唯一的复杂情况是如果 $\psi$ 包含 $t$。那么我们将有 $\Gamma_2 \vdash (\phi \& \psi)(t|t')$。但是，由于 $(\phi \& \psi)(t|t')$ 是 $\phi(t|t') \& \psi(t|t')$，而 $\phi(t|t')$ 就是 $\phi$，我们可以直接应用 $(\& E)$ 按要求得到 $\Gamma_2 \vdash \phi$。其他规则的情况类似。

**定理 8**。弱化规则（The rule of Weakening）。如果 $\Gamma_1 \vdash \phi$ 且 $\Gamma_1 \subseteq \Gamma_2$，那么 $\Gamma_2 \vdash \phi$。

**证明**：再次，我们对用于得出 $\Gamma_1 \vdash \phi$ 的规则数量进行归纳。假设 $n>0$ 是一个自然数，并且该定理对任何使用少于 $n$ 条规则导出的论证成立。假设 $\Gamma_1 \vdash \phi$ 恰好使用了 $n$ 条规则。如果 $n=1$，那么规则要么是 (As) 要么是 $(=$I)。在这些情况下，通过相同的规则有 $\Gamma_2 \vdash \phi$。如果应用的最后一条规则是 (&I)，那么 $\phi$ 的形式为 $(\theta \& \psi)$，并且我们有 $\Gamma_3 \vdash \theta$ 和 $\Gamma_4 \vdash \psi$，其中 $\Gamma_1 = \Gamma_3, \Gamma_4$。我们将归纳假设应用于 $\theta$ 和 $\psi$ 的推导，得到 $\Gamma_2 \vdash \theta$ 和 $\Gamma_2 \vdash \psi$，然后将 (&I) 应用于结果得到 $\Gamma_2 \vdash \phi$。大多数其他情况完全像这样。只有在规则 $(\forall$I) 和 $(\exists$E) 中会出现轻微的复杂情况，因为那里我们必须注意规则的条件。

假设用于得到 $\Gamma_1 \vdash \phi$ 的最后一条规则是 $(\forall$I)。所以 $\phi$ 是形式为 $\forall v\theta$ 的句子，并且我们有 $\Gamma_1 \vdash \theta (v|t)$ 且 $t$ 不出现在 $\Gamma_1$ 的任何成员中或 $\theta$ 中。问题是 $t$ 可能出现在 $\Gamma_2$ 的成员中，所以我们不能直接援引归纳假设并将 $(\forall$I) 应用于结果。所以，设 $t'$ 为不出现在 $\Gamma_2$ 中任何句子中的词项。设 $\Gamma'$ 为在 $\Gamma_2$ 中用 $t'$ 替换所有 $t$ 的结果。那么，由于 $t$ 不出现在 $\Gamma_1$ 中，$\Gamma_1 \subseteq \Gamma'$。所以，归纳假设给我们 $\Gamma' \vdash \theta (v|t)$，并且我们知道 $\Gamma'$ 不包含 $t$，所以我们可以应用 $(\forall I)$ 得到 $\Gamma' \vdash \forall v\theta$。但是 $\forall v\theta$ 不包含 $t$ 或 $t'$，所以根据引理 7，$\Gamma_2 \vdash \forall v\theta$。

假设应用的最后一条规则是 $(\exists$E)，我们有 $\Gamma_3 \vdash \exists v\theta$ 和 $\Gamma_4, \theta (v|t) \vdash \phi$，其中 $\Gamma_1$ 为 $\Gamma_3, \Gamma_4$，且 $t$ 不在 $\phi$、$\Gamma_4$ 或 $\theta$ 中。如果 $t$ 在 $\Gamma_2$ 中不自由出现，我们应用归纳假设得到 $\Gamma_2 \vdash \exists v\theta$，然后应用 $(\exists$E) 最终得到 $\Gamma_2 \vdash \phi$。如果 $t$ 在 $\Gamma_2$ 中自由出现，那么我们遵循与 $\forall I$ 类似的程序，使用引理 7。

定理 8 允许我们随意添加前提。由此可见，$\Gamma \vdash \phi$ 当且仅当存在子集 $\Gamma' \subseteq \Gamma$ 使得 $\Gamma' \vdash \phi$。一些相关逻辑系统没有弱化，亚结构逻辑也没有（参见关于相关逻辑、亚结构逻辑和线性逻辑的词条）。

根据条款 (*)，所有推导都在有限步数内建立。所以我们有

**定理 9**。 $\Gamma \vdash \phi$ 当且仅当存在有限的 $\Gamma' \subseteq \Gamma$ 使得 $\Gamma' \vdash \phi$。

**定理 10**。规则 *ex falso quodlibet* 是 $D$ 的“派生规则”：如果 $\Gamma_1 \vdash \theta$ 且 $\Gamma_2 \vdash \neg \theta$，那么对于任何句子 $\psi$，$\Gamma_1, \Gamma_2 \vdash \psi$。

**证明**：假设 $\Gamma_1 \vdash \theta$ 且 $\Gamma_2 \vdash \neg \theta$。那么根据定理 8，$\Gamma_1, \neg \psi \vdash \theta$，且 $\Gamma_2, \neg \psi \vdash \neg \theta$。所以根据 $(\neg$I)，$\Gamma_1, \Gamma_2 \vdash \neg \neg \psi$。根据 (DNE)，$\Gamma_1, \Gamma_2 \vdash \psi$。

**定理 11**。剪切规则（The rule of Cut）。如果 $\Gamma_1 \vdash \psi$ 且 $\Gamma_2, \psi \vdash \theta$，那么 $\Gamma_1, \Gamma_2 \vdash \theta$。

**证明**：假设 $\Gamma_1 \vdash \psi$ 且 $\Gamma_2, \psi \vdash \theta$。我们对用于建立 $\Gamma_2, \psi \vdash \theta$ 的规则数量进行归纳。假设 $n$ 是一个自然数，并且该定理对任何使用少于 $n$ 条规则导出的论证成立。假设 $\Gamma_2, \psi \vdash \theta$ 恰好使用了 $n$ 条规则。如果使用的最后一条规则是 $(=$I)，那么 $\Gamma_1, \Gamma_2 \vdash \theta$ 也是 $(=$I) 的一个实例。如果 $\Gamma_2, \psi \vdash \theta$ 是 (As) 的一个实例，那么要么 $\theta$ 是 $\psi$，要么 $\theta$ 是 $\Gamma_2$ 的成员。在前一种情况下，我们要有 $\Gamma_1 \vdash \theta$ 根据假设，并通过弱化（定理 8）得到 $\Gamma_1, \Gamma_2 \vdash \theta$。在后一种情况下，$\Gamma_1, \Gamma_2 \vdash \theta$ 本身就是 (As) 的一个实例。假设 $\Gamma_2, \psi \vdash \theta$ 是使用 (&E) 获得的。那么我们有 $\Gamma_2, \psi \vdash (\theta \& \phi)$。归纳假设给我们 $\Gamma_1, \Gamma_2 \vdash (\theta \& \phi)$，并且 (&E) 产生 $\Gamma_1, \Gamma_2 \vdash \theta$。其余情况类似。

定理 11 允许我们将推论串联起来。这符合建立定理和引理，然后随意在后面使用这些定理和引理的实践。有些人认为，剪切原则对于推理至关重要。在某些逻辑系统中，剪切原则是一个深刻的定理；在其他系统中它是无效的。这里的系统设计部分是为了使定理 11 的证明直截了当。

如果 $\Gamma \vdash_D \theta$，那么我们说句子 $\theta$ 是句子集 $\Gamma$ 的演绎后承（deductive consequence），并且论证 $\langle \Gamma, \theta \rangle$ 是演绎有效的。如果 $\vdash_D \theta$，则句子 $\theta$ 是逻辑定理，或演绎逻辑真理。也就是说，如果 $\theta$ 是空集的演绎后承，它就是一个逻辑定理。如果不存在句子 $\theta$ 使得 $\Gamma \vdash_D \theta$ 且 $\Gamma \vdash_D \neg \theta$，则句子集 $\Gamma$ 是一致的（consistent）。也就是说，如果一个集合不蕴涵一对矛盾对立的句子，它就是一致的。

**定理 12**。集合 $\Gamma$ 是一致的，当且仅当存在一个句子 $\theta$，使得并非 $\Gamma \vdash \theta$。

**证明**：假设 $\Gamma$ 是一致的，令 $\theta$ 为任何句子。那么要么并非 $\Gamma \vdash \theta$，要么并非 $\Gamma \vdash \neg \theta$。对于逆命题，假设 $\Gamma$ 是不一致的，令 $\psi$ 为任何句子。我们有存在一个句子使得 $\Gamma \vdash \theta$ 和 $\Gamma \vdash \neg \theta$ 都成立。根据 *ex falso quodlibet*（定理 10），$\Gamma \vdash \psi$。

定义语言 $\mathcal{L}1K=$ 的句子集 $\Gamma$ 为最大一致的（maximally consistent），如果 $\Gamma$ 是一致的，并且对于 $\mathcal{L}1K=$ 的每个句子 $\theta$，如果 $\theta$ 不在 $\Gamma$ 中，那么 $\Gamma, \theta$ 是不一致的。换句话说，如果 $\Gamma$ 是一致的，并且添加任何不在 $\Gamma$ 中的句子都会使其不一致，那么 $\Gamma$ 就是最大一致的。注意，如果 $\Gamma$ 是最大一致的，那么 $\Gamma \vdash \theta$ 当且仅当 $\theta$ 在 $\Gamma$ 中。

**定理 13**。林登鲍姆引理（The Lindenbaum Lemma）。设 $\Gamma$ 为 $\mathcal{L}1K=$ 的任何一致句子集。那么存在 $\mathcal{L}1K=$ 的句子集 $\Gamma'$ 使得 $\Gamma \subseteq \Gamma'$ 并且 $\Gamma'$ 是最大一致的。

**证明**：虽然该定理通常成立，但我们在这里假设非逻辑术语集 $K$ 要么是有限的，要么是可数无限的（即自然数的大小，通常称为 $\aleph_0$）。由此可见，存在 $\mathcal{L}1K=$ 的句子的枚举 $\theta_0, \theta_1, \ldots$，使得 $\mathcal{L}1K=$ 的每个句子最终都会出现在列表中。通过递归定义一个句子集序列，如下所示：$\Gamma_0$ 是 $\Gamma$；对于每个自然数 $n$，如果 $\Gamma_n, \theta_n$ 是一致的，那么令 $\Gamma_{n+1} = \Gamma_n, \theta_n$。否则，令 $\Gamma_{n+1} = \Gamma_n$。令 $\Gamma'$ 为所有集合 $\Gamma_n$ 的并集。直观地说，这个想法是遍历 $\mathcal{L}1K=$ 的句子，如果将其放入 $\Gamma'$ 会产生一致的集合，就将其放入。注意每个 $\Gamma_n$ 都是一致的。假设 $\Gamma'$ 是不一致的。那么存在一个句子 $\theta$ 使得 $\Gamma' \vdash \theta$ 且 $\Gamma' \vdash \neg \theta$。根据定理 9 和弱化（定理 8），存在 $\Gamma'$ 的有限子集 $\Gamma''$ 使得 $\Gamma'' \vdash \theta$ 且 $\Gamma'' \vdash \neg \theta$。因为 $\Gamma''$ 是有限的，存在一个自然数 $n$ 使得 $\Gamma''$ 的每个成员都在 $\Gamma_n$ 中。所以，再次根据弱化，$\Gamma_n \vdash \theta$ 且 $\Gamma_n \vdash \neg \theta$。所以 $\Gamma_n$ 是不一致的，这与构造相矛盾。所以 $\Gamma'$ 是一致的。现在假设一个句子 $\theta$ 不在 $\Gamma'$ 中。我们必须证明 $\Gamma', \theta$ 是不一致的。句子 $\theta$ 必须出现在上述句子列表中；设 $\theta$ 为 $\theta_m$。由于 $\theta_m$ 不在 $\Gamma'$ 中，那么它不在 $\Gamma_{m+1}$ 中。这只有在 $\Gamma_m, \theta_m$ 不一致时才会发生。所以可以从 $\Gamma_m, \theta_m$ 推导出一对矛盾对立面。根据弱化，可以从 $\Gamma', \theta_m$ 推导出一对矛盾对立面。所以 $\Gamma', \theta_m$ 是不一致的。因此，$\Gamma'$ 是最大一致的。

注意，这个证明使用了对应于排中律的原则。在 $\Gamma'$ 的构造中，我们假设在每个阶段，$\Gamma_n$ 要么一致要么不一致。反对排中律的直觉主义者不接受林登鲍姆引理。

## 4. 语义学 (Semantics)

设 $K$ 为一组非逻辑术语。语言 $\mathcal{L}1K=$ 的一个解释是一个结构 $M = \langle d, I\rangle$，其中 $d$ 是一个非空集合，称为解释的**论域**（domain-of-discourse），或简称**域**（domain），$I$ 是一个解释函数。非形式地说，域是我们解释语言 $\mathcal{L}1K=$ 所关于的内容。它是变项取值的范围。解释函数为非逻辑词项分配适当的外延。特别是，

如果 $c$ 是 $K$ 中的常项，那么 $I(c)$ 是域 $d$ 的成员。

因此我们假设每个常项都表示某物。不假设这一点的系统称为自由逻辑（free logics）（参见关于自由逻辑的词条）。继续，

如果 $P^0$ 是 $K$ 中的零元谓词字母，那么 $I(P)$ 是一个真值，真或假。

如果 $Q^1$ 是 $K$ 中的一元谓词字母，那么 $I(Q)$ 是 $d$ 的一个子集。直观地说，$I(Q)$ 是谓词 $Q$ 对其成立的域成员的集合。例如，$I(Q)$ 可能是域中红色成员的集合。

如果 $R^2$ 是 $K$ 中的二元谓词字母，那么 $I(R)$ 是 $d$ 的成员的有序对的集合。直观地说，$I(R)$ 是关系 $R$ 在其之间成立的域成员对的集合。例如，$I(R)$ 可能是对 $\langle a,b\rangle$ 的集合，使得 $a$ 和 $b$ 是域中 $a$ 爱 $b$ 的成员。

一般来说，如果 $S^n$ 是 $K$ 中的 $n$ 元谓词字母，那么 $I(S)$ 是 $d$ 的成员的有序 $n$ 元组的集合。

如果 $s$ 是从变项到 $M$ 的域 $d$ 的函数，则定义 $s$ 为解释 $M$ 上的**变项赋值**（variable-assignment），或简称**赋值**。变项赋值的作用是为开放公式的自由变项分配指称。（在某种意义上，量词决定了约束变项的“意义”。）

设 $t$ 为 $\mathcal{L}1K=$ 的一个词项。我们根据解释函数和变项赋值定义 $t$ 在 $M$ 中 $s$ 下的指称：

如果 $t$ 是常项，那么 $D_{M,s}(t)$ 是 $I(t)$，如果 $t$ 是变项，那么 $D_{M,s}(t)$ 是 $s(t)$。

也就是说，解释 $M$ 为常项分配指称，而变项赋值为（自由）变项分配指称。如果语言包含函数符号，指称函数将通过递归定义。

我们现在定义解释、变项赋值和 $\mathcal{L}1K=$ 的公式之间的**满足**（satisfaction）关系。如果 $\phi$ 是 $\mathcal{L}1K=$ 的公式，$M$ 是 $\mathcal{L}1K=$ 的解释，且 $s$ 是 $M$ 上的变项赋值，那么我们写 $M,s\vDash \phi$ 表示 $M$ 在赋值 $s$ 下满足 $\phi$。其思想是 $M,s\vDash \phi$ 是“$\phi$ 在通过 $s$ 解释为 $M$ 时为真”的类似物。

我们对 $\mathcal{L}1K=$ 公式的复杂性进行递归。

如果 $t_1$ 和 $t_2$ 是词项，那么 $M,s\vDash t_1 =t_2$ 当且仅当 $D_{M,s}(t_1)$ 与 $D_{M,s}(t_2)$ 相同。

这再简单不过了。恒等式 $t_1 =t_2$ 为真当且仅当词项 $t_1$ 和 $t_2$ 表示同一个东西。

如果 $P^0$ 是 $K$ 中的零元谓词字母，那么 $M,s\vDash P$ 当且仅当 $I(P)$ 为真。

如果 $S^n$ 是 $K$ 中的 $n$ 元谓词字母且 $t_1, \ldots,t_n$ 是词项，那么 $M,s\vDash St_1 \ldots t_n$ 当且仅当 $n$ 元组 $\langle D_{M,s}(t_1), \ldots,D_{M,s}(t_n)\rangle$ 在 $I(S)$ 中。

这解决了原子公式。我们现在处理语言的复合公式，或多或少遵循逻辑术语的英语对应物的含义。

$M,s\vDash \neg \theta$ 当且仅当并非 $M,s\vDash \theta$。

$M,s\vDash (\theta \& \psi)$ 当且仅当 $M,s\vDash \theta$ 且 $M,s\vDash \psi$。

$M,s\vDash (\theta \vee \psi)$ 当且仅当 $M,s\vDash \theta$ 或 $M,s\vDash \psi$。

$M,s\vDash (\theta \rightarrow \psi)$ 当且仅当并非 $M,s\vDash \theta$，或 $M,s\vDash \psi$。

$M,s\vDash \forall v\theta$ 当且仅当 $M,s'\vDash \theta$，对于每个除了可能在变项 $v$ 处之外与 $s$ 一致的赋值 $s'$。

这里的想法是 $\forall v\theta$ 为真当且仅当无论分配给变项 $v$ 什么，$\theta$ 都为真。最后一个条款类似。

$M,s\vDash \exists v\theta$ 当且仅当 $M,s'\vDash \theta$，对于某个除了可能在变项 $v$ 处之外与 $s$ 一致的赋值 $s'$。

所以 $\exists v\theta$ 为真，如果存在一个对 $v$ 的赋值使 $\theta$ 为真。

定理 6，唯一可读性，向我们保证这个定义是连贯的。在分解公式的每个阶段，恰好有一个条款适用，因此我们永远不会得到关于满足的矛盾判决。

如上所述，变项赋值的作用是为自由变项提供指称。我们现在表明变项赋值没有其他作用。

**定理 14**。对于任何公式 $\theta$，如果 $s_1$ 和 $s_2$ 在 $\theta$ 中的自由变项上一致，那么 $M,s_1 \vDash \theta$ 当且仅当 $M,s_2 \vDash \theta$。

**证明**：我们对公式 $\theta$ 的复杂性进行归纳。如果 $\theta$ 是原子的，定理显然成立，因为在这些情况下只有变项赋值在 $\theta$ 中变项处的值参与定义。假设定理对所有比 $\theta$ 简单的公式成立。并假设 $s_1$ 和 $s_2$ 在 $\theta$ 的自由变项上一致。首先，假设 $\theta$ 是否定，$\neg \psi$。那么，根据归纳假设，$M,s_1 \vDash \psi$ 当且仅当 $M,s_2 \vDash \psi$。所以，根据否定条款，$M,s_1 \vDash \neg \psi$ 当且仅当 $M,s_2 \vDash \neg \psi$。$\theta$ 中主联结词为二元的情况也很直接。假设 $\theta$ 是 $\exists v\psi$，并且 $M,s_1 \vDash \exists v\psi$。那么存在一个除了可能在 $v$ 处之外与 $s_1$ 一致的赋值 $s_1'$ 使得 $M,s_1'\vDash \psi$。设 $s_2'$ 为在不在 $\psi$ 中的自由变项上与 $s_2$ 一致并在其他变项上与 $s_1'$ 一致的赋值。那么，根据归纳假设，$M,s_2'\vDash \psi$。注意 $s_2'$ 除了可能在 $v$ 处之外与 $s_2$ 一致。所以 $M,s_2 \vDash \exists v\psi$。逆命题相同，$\theta$ 以全称量词开头的情况类似。

根据定理 14，如果 $\theta$ 是一个句子，且 $s_1, s_2$ 是任何两个变项赋值，那么 $M,s_1 \vDash \theta$ 当且仅当 $M,s_2 \vDash \theta$。所以如果对于某个或所有变项赋值 $s$ 有 $M,s\vDash \theta$，我们可以只写 $M\vDash \theta$。所以我们定义

$M\vDash \theta$ 其中 $\theta$ 是句子，当且仅当对于所有变项赋值 $s$ 有 $M,s\vDash \theta$。

在这种情况下，我们称 $M$ 为 $\theta$ 的**模型**。

假设 $K' \subseteq K$ 是两组非逻辑词项。如果 $M = \langle d, I\rangle$ 是 $\mathcal{L}1K=$ 的解释，那么我们定义 $M$ 对 $\mathcal{L}1K'{=}$ 的**限制**为解释 $M'=\langle d, I'\rangle$，其中 $I'$ 是 $I$ 对 $K'$ 的限制。也就是说，$M$ 和 $M'$ 具有相同的域，并在 $K'$ 中的非逻辑术语上一致。简单的归纳确立了以下内容：

**定理 15**。如果 $M'$ 是 $M$ 对 $\mathcal{L}1K'{=}$ 的限制，那么对于 $\mathcal{L}1K'$ 的每个句子 $\theta$，$M\vDash\theta$ 当且仅当 $M'\vDash \theta$。

**定理 16**。如果两个解释 $M_1$ 和 $M_2$ 具有相同的域并且在句子 $\theta$ 的所有非逻辑术语上一致，那么 $M_1\vDash\theta$ 当且仅当 $M_2\vDash \theta$。

简而言之，句子 $\theta$ 的满足仅取决于论域和 $\theta$ 中非逻辑术语的解释。

我们说论证 $\langle \Gamma, \theta \rangle$ 是**语义有效**（semantically valid）的，或简称**有效**的，写为 $\Gamma \vDash \theta$，如果对于语言的每个解释 $M$，如果 $M\vDash\psi$（对于 $\Gamma$ 的每个成员 $\psi$），那么 $M\vDash\theta$。如果 $\Gamma \vDash \theta$，我们也说 $\theta$ 是 $\Gamma$ 的**逻辑后承**（logical consequence），或语义后承，或模型论后承。这个定义对应于非形式的想法，即如果前提不可能全为真而结论为假，则论证是有效的。我们对逻辑后承的定义也认可了一个共同的论点，即有效论证是保真的——只要满足代表真理。正式地说，$\mathcal{L}1K=$ 中的论证是有效的，如果在前提为真的每种语言解释下其结论都为真。有效性是可导性的模型论对应物。

句子 $\theta$ 是**逻辑真**（logically true）的，或**有效**的，如果对于每个解释 $M$，$M\vDash \theta$。一个句子是逻辑真的当且仅当它是空集的后承。如果 $\theta$ 是逻辑真的，那么对于任何句子集 $\Gamma$，$\Gamma \vDash \theta$。逻辑真是定理性的模型论对应物。

句子 $\theta$ 是**可满足**（satisfiable）的，如果存在解释 $M$ 使得 $M\vDash \theta$。也就是说，如果有一个解释满足它，则 $\theta$ 是可满足的。句子集 $\Gamma$ 是可满足的，如果存在解释 $M$ 使得对于 $\Gamma$ 中的每个句子 $\theta$，$M\vDash\theta$。如果 $\Gamma$ 是一组句子，且对于 $\Gamma$ 中的每个句子 $\theta$，$M\vDash \theta$，那么我们说 $M$ 是 $\Gamma$ 的**模型**。所以一组句子如果是可满足的，如果它有一个模型。可满足性是一致性的模型论对应物。

注意 $\Gamma \vDash \theta$ 当且仅当集合 $\Gamma, \neg \theta$ 是不可满足的。由此可见，如果集合 $\Gamma$ 是不可满足的，那么如果 $\theta$ 是任何句子，$\Gamma \vDash \theta$。这是 *ex falso quodlibet* 的模型论对应物（参见定理 10）。作为定理 12 的类似物，我们要有以下内容：

**定理 17**。设 $\Gamma$ 为一组句子。以下是等价的：(a) $\Gamma$ 是可满足的；(b) 不存在句子 $\theta$ 使得 $\Gamma \vDash \theta$ 和 $\Gamma \vDash \neg \theta$ 都成立；(c) 存在某个句子 $\psi$ 使得并非 $\Gamma \vDash \psi$。

**证明**：(a)$\Rightarrow$(b)：假设 $\Gamma$ 是可满足的，令 $\theta$ 为任何句子。存在解释 $M$ 使得对于 $\Gamma$ 的每个成员 $\psi$，$M\vDash \psi$。根据否定的条款，我们不能同时有 $M\vDash \theta$ 和 $M\vDash \neg \theta$。所以要么 $\langle \Gamma, \theta \rangle$ 不是有效的，要么 $\langle \Gamma, \neg \theta \rangle$ 不是有效的。(b)$\Rightarrow$(c)：这是直接的。(c)$\Rightarrow$(a)：假设并非 $\Gamma \vDash \psi$。那么存在解释 $M$ 使得对于 $\Gamma$ 中的每个句子 $\theta$，$M\vDash \theta$，且并非 $M\vDash \psi$。更不用说，$M$ 满足 $\Gamma$ 的每个成员，所以 $\Gamma$ 是可满足的。

## 5. 元理论 (Meta-theory)

我们现在提出一些将演绎概念与其模型论对应物联系起来的结果。第一个可能是最直接的。我们在定义 $D$ 的各种规则和定义满足的各种条款时，都或多或少地以逻辑术语的英语对应物的含义为动机（在两种情况下都进行了相同的简化）。所以人们会期望一个论证只有在语义上有效时才是可导出的，或演绎有效的。

**定理 18**。可靠性（Soundness）。对于任何句子 $\theta$ 和句子集 $\Gamma$，如果 $\Gamma \vdash_D \theta$，那么 $\Gamma \vDash \theta$。

**证明**：我们对用于建立 $\Gamma \vdash \theta$ 的条款数量进行归纳。所以设 $n$ 为一个自然数，并假设该定理对任何以少于 $n$ 步建立为演绎有效的论证成立。并假设 $\Gamma \vdash \theta$ 恰好使用了 $n$ 步。如果应用的最后一条规则是 $(=$I) 那么 $\theta$ 是形式为 $t=t$ 的句子，所以 $\theta$ 是逻辑真的。更不用说，$\Gamma \vDash \theta$。如果应用的最后一条规则是 (As)，那么 $\theta$ 是 $\Gamma$ 的成员，所以当然任何满足 $\Gamma$ 每个成员的解释也满足 $\theta$。假设应用的最后一条规则是 (&I)。所以 $\theta$ 具有形式 $(\phi \& \psi)$，并且我们有 $\Gamma_1 \vdash \phi$ 和 $\Gamma_2 \vdash \psi$，其中 $\Gamma = \Gamma_1, \Gamma_2$。归纳假设给我们 $\Gamma_1 \vDash \phi$ 和 $\Gamma_2 \vDash \psi$。假设 $M$ 满足 $\Gamma$ 的每个成员。那么 $M$ 满足 $\Gamma_1$ 的每个成员，所以 $M$ 满足 $\phi$。同样，$M$ 满足 $\Gamma_2$ 的每个成员，所以 $M$ 满足 $\psi$。因此，根据满足定义中的“$\&$”条款，$M$ 满足 $\theta$。所以 $\Gamma \vDash \theta$。

假设应用的最后一个条款是 $(\exists\mathrm{E})$。所以我们有 $\Gamma_1 \vdash \exists v\phi$ 和 $\Gamma_2, \phi(v|t) \vdash \theta$，其中 $\Gamma = \Gamma_1, \Gamma_2$，且 $t$ 不出现在 $\phi, \theta$ 或 $\Gamma_2$ 的任何成员中。

我们需要证明 $\Gamma\vDash\theta$。根据归纳假设，我们有 $\Gamma_1\vDash\exists v\phi$ 和 $\Gamma_2, \phi(v|t)\vDash\theta$。设 $M$ 为一个解释，使得 $M$ 使 $\Gamma$ 的每个成员为真。所以，$M$ 使 $\Gamma_1$ 和 $\Gamma_2$ 的每个成员为真。那么对于所有变项赋值 $s$，$M,s\vDash\exists v\phi$，所以存在一个 $s'$ 使得 $M,s'\vDash\phi$。设 $M'$ 仅在 $I_{M'}(t)=s'(v)$ 方面与 $M$ 不同。那么，$M',s'\vDash\phi(v|t)$ 且 $M',s'\vDash\Gamma_2$，因为 $t$ 不出现在 $\phi$ 或 $\Gamma_2$ 中。所以，$M',s'\vDash\theta$。由于 $t$ 不出现在 $\theta$ 中且 $M'$ 仅在 $I_{M'}(t)$ 方面与 $M$ 不同，$M,s'\vDash\theta$。由于 $\theta$ 是一个句子，$s'$ 无关紧要，所以 $M\vDash\theta$ 如愿。注意这里 $(\exists$E) 限制的作用。其他情况也是直接的。

**推论 19**。设 $\Gamma$ 为一组句子。如果 $\Gamma$ 是可满足的，那么 $\Gamma$ 是一致的。

**证明**：假设 $\Gamma$ 是可满足的。所以设 $M$ 为一个解释，使得 $M$ 满足 $\Gamma$ 的每个成员。假设 $\Gamma$ 是不一致的。那么存在一个句子 $\theta$ 使得 $\Gamma \vdash \theta$ 且 $\Gamma \vdash \neg \theta$。根据可靠性（定理 18），$\Gamma \vDash \theta$ 且 $\Gamma \vDash \neg \theta$。所以我们要有 $M\vDash \theta$ 和 $M\vDash \neg \theta$。但这是不可能的，鉴于满足定义中的否定条款。

尽管演绎系统 $D$ 和模型论语义学是在考虑到逻辑术语的含义的情况下开发的，但不应自动期望可靠性（或推论 19）的逆命题成立。就我们目前所知，我们可能没有包含足够的推理规则来推导出每个有效论证。可靠性和推论 19 的逆命题是数理逻辑中最重要和最有影响力的结果之一。我们从后者开始。

**定理 20**。完全性（Completeness）。哥德尔 [1930]。设 $\Gamma$ 为一组句子。如果 $\Gamma$ 是一致的，那么 $\Gamma$ 是可满足的。

**证明**：完全性的证明相当复杂。我们在这里只勾勒一下。设 $\Gamma$ 为 $\mathcal{L}1K=$ 的一致句子集。同样，为简单起见，我们假设非逻辑术语集 $K$ 要么是有限的，要么是可数无限的（尽管即使 $K$ 是不可数的，定理也成立）。目前的任务是找到一个解释 $M$，使得 $M$ 满足 $\Gamma$ 的每个成员。考虑通过添加可数无限的新个体常项 $c_0, c_1,\ldots$ 从 $\mathcal{L}1K=$ 获得的语言。我们规定常项 $c_0, c_1,\ldots$ 彼此不同，且都不出现在 $K$ 中。这个构造（归功于 Leon Henkin）的一个有趣特征是，我们利用语言本身来构建语言的解释，使用一些常项作为论域的成员。设 $\theta_0 (x), \theta_1 (x),\ldots$ 为扩展语言中至多有一个自由变项的公式的枚举，使得每个至多有一个自由变项的公式最终都会出现在列表中。通过递归定义句子集序列（扩展语言的）$\Gamma_0, \Gamma_1,\ldots$ 如下：$\Gamma_0 = \Gamma$；且 $\Gamma_{n+1} = \Gamma_n, (\exists x\theta_n \rightarrow \theta_{n}(x|c_i))$，其中 $c_i$ 是上述列表中第一个不出现在 $\theta_n$ 或 $\Gamma_n$ 任何成员中的常项。这里的基本思想是，如果 $\exists x\theta_n$ 为真，那么 $c_i$ 就是这样一个 $x$。设 $\Gamma'$ 为所有集合 $\Gamma_n$ 的并集。

我们勾勒一个 $\Gamma'$ 是一致的证明。假设 $\Gamma'$ 是不一致的。根据定理 9，存在 $\Gamma$ 的一个有限子集是不一致的，所以集合 $\Gamma_m$ 中的一个是不一致的。根据假设，$\Gamma_0 = \Gamma$ 是一致的。设 $n$ 为最小的数，使得 $\Gamma_n$ 是一致的，但 $\Gamma_{n+1} = \Gamma_n, (\exists x\theta_n \rightarrow \theta_{n}(x|c_i))$ 是不一致的。根据 $(\neg$I)，我们要有

$$ \tag{1} \Gamma_n \vdash \neg(\exists x\theta_n \rightarrow \theta_n(x|c_i)). $$

根据 *ex falso quodlibet*（定理 10），$\Gamma_n, \neg \exists x\theta_n, \exists x\theta_n \vdash \theta_n (x|c_i)$。所以根据 $(\rightarrow$I)，$\Gamma_n, \neg \exists x\theta_n \vdash (\exists x\theta_n \rightarrow \theta_n (x|c_i))$。由此和 (1)，我们有 $\Gamma_n \vdash \neg \neg \exists x\theta_n$，根据 $(\neg$I)，且根据 (DNE) 我们有

$$ \tag{2} \Gamma_n \vdash \exists x\theta_n . $$

根据 (As)，$\Gamma_n, \theta_n (x|c_i), \exists x\theta_n \vdash \theta_n (x|c_i)$。所以根据 $(\rightarrow$I)，$\Gamma_n, \theta_n (x|c_i) \vdash (\exists x\theta_{n} \rightarrow \theta_{n}(x|c_i))$。由此和 (1)，我们有 $\Gamma_n \vdash \neg \theta_n (x|c_i)$，根据 $(\neg$I)。设 $t$ 为不出现在 $\theta_n$ 或 $\Gamma_n$ 任何成员中的词项。通过将 $t$ 统一代换为 $c_i$，我们可以将 $\Gamma_n \vdash \neg \theta_n (x|c_i)$ 的推导转化为 $\Gamma_n \vdash \neg \theta_n (x|t)$。根据 $(\forall$I)，我们有

$$ \tag{3} \Gamma_n \vdash \forall v\neg \theta_n (x|v). $$

根据 (As) 我们有 $\{\forall v\neg \theta_n (x|v), \theta_n\} \vdash \theta_n$ 且根据 $(\forall$E) 我们有 $\{\forall v\neg \theta_n (x|v), \theta_n\} \vdash \neg \theta_n$。所以 $\{\forall v\neg \theta_n (x|v), \theta_n\}$ 是不一致的。设 $\phi$ 为语言的任何句子。根据 *ex falso quodlibet*（定理 10），我们要有 $\{\forall v\neg \theta_n (x|v), \theta_n\} \vdash \phi$ 且 $\{\forall v\neg \theta_n (x|v), \theta_n\} \vdash \neg \phi$。所以结合 (2)，我们要有 $\Gamma_n, \forall v\neg \theta_n (x|v) \vdash \phi$ 且 $\Gamma_n, \forall v\neg \theta_n (x|v) \vdash \neg \phi$，根据 $(\exists$E)。根据剪切（定理 11），$\Gamma_n \vdash \phi$ 且 $\Gamma_n \vdash \neg \phi$。所以 $\Gamma_n$ 是不一致的，与假设矛盾。所以 $\Gamma'$ 是一致的。

应用林登鲍姆引理（定理 13），设 $\Gamma''$ 为包含 $\Gamma'$ 的最大一致句子集（扩展语言的）。所以，当然，$\Gamma''$ 包含 $\Gamma$。我们现在可以定义一个解释 $M$，使得 $M$ 满足 $\Gamma''$ 的每个成员。

如果我们在语言中没有同一性符号，我们会让 $M$ 的域为新常项的集合 $\{c_0, c_1, \ldots \}$。但实际上，$\Gamma''$ 中可能有形式为 $c_{i}=c_{j}$（其中 $i\ne j$）的句子。如果是这样，我们不能让 $c_i$ 和 $c_j$ 都在解释的域中（因为它们是不同的常项）。所以我们定义 $M$ 的域 $d$ 为集合 $\{c_i \mid$ 不存在 $j < i$ 使得 $c_{i}=c_{j}$ 在 $\Gamma''$ 中 $\}$。换句话说，如果 $\Gamma''$ 没有声明 $c_i$ 与列表中较早的常项同一，则 $c_i$ 在 $M$ 的域中。注意对于每个新常项 $c_i$，恰好有一个 $j \le i$ 使得 $c_j$ 在 $d$ 中且句子 $c_{i}=c_{j}$ 在 $\Gamma''$ 中。

我们现在定义解释函数 $I$。设 $a$ 为扩展语言中的任何常项。根据 $(=$I) 和 $(\exists$I)，$\Gamma'' \vdash \exists x x=a$，因此 $\exists x x=a \in \Gamma''$。根据 $\Gamma'$ 的构造，$\Gamma''$ 中有形式为 $(\exists x x=a \rightarrow c_i =a)$ 的句子。我们要有 $c_i =a$ 在 $\Gamma''$ 中。如上所述，在 $d$ 中恰好有一个 $c_j$ 使得 $c_{i}=c_{j}$ 在 $\Gamma''$ 中。令 $I(a)=c_j$。注意如果 $c_i$ 是域 $d$ 中的常项，那么 $I(c_i)=c_i$。即 $d$ 中的每个 $c_i$ 表示其自身。

设 $P$ 为 $K$ 中的零元谓词字母。如果 $P$ 在 $\Gamma''$ 中，则 $I(P)$ 为真，否则为假。设 $Q$ 为 $K$ 中的一元谓词字母。那么 $I(Q)$ 是常项集合 $\{c_i \mid c_i$ 在 $d$ 中且句子 $Qc$ 在 $\Gamma''$ 中 $\}$。设 $R$ 为 $K$ 中的二元谓词字母。那么 $I(R)$ 是常项对集合 $\{\langle c_i,c_j\rangle \mid c_i$ 在 $d$ 中，$c_j$ 在 $d$ 中，且句子 $Rc_{i}c_{j}$ 在 $\Gamma''$ 中 $\}$。三元谓词等类似解释。实际上，$I$ 按照 $\Gamma''$ 中的情况解释非逻辑术语。

这个证明的最后一项是一个引理：对于扩展语言中的每个句子 $\theta$，$M\vDash \theta$ 当且仅当 $\theta$ 在 $\Gamma''$ 中。这是通过对 $\theta$ 的复杂性进行归纳来进行的。$\theta$ 为原子的情况遵循 $M$ 的定义（即域 $d$ 和解释函数 $I$）。其他情况遵循满足定义中的各个条款。

由于 $\Gamma \subseteq \Gamma''$，我们要有 $M$ 满足 $\Gamma$ 的每个成员。根据定理 15，$M$ 对原始语言 $\mathcal{L}1K=$ 的限制和 $s$ 也满足 $\Gamma$ 的每个成员。因此 $\Gamma$ 是可满足的。

可靠性（定理 18）的一个逆命题是一个直接的推论：

**定理 21**。对于任何句子 $\theta$ 和句子集 $\Gamma$，如果 $\Gamma \vDash \theta$，那么 $\Gamma \vdash_D \theta$。

**证明**：假设 $\Gamma \vDash \theta$。那么不存在解释 $M$ 使得 $M$ 满足 $\Gamma$ 的每个成员但不满足 $\theta$。所以集合 $\Gamma, \neg \theta$ 是不可满足的。根据完全性（定理 20），$\Gamma, \neg \theta$ 是不一致的。所以存在一个句子 $\phi$ 使得 $\Gamma, \neg \theta \vdash \phi$ 且 $\Gamma, \neg \theta \vdash \neg \phi$。根据 $(\neg$I)，$\Gamma \vdash \neg \neg \theta$，且根据 (DNE) $\Gamma \vdash \theta$。

我们的下一项是定理 9、可靠性（定理 18）和完全性的推论：

**推论 22**。紧致性（Compactness）。一组句子 $\Gamma$ 是可满足的，当且仅当 $\Gamma$ 的每个有限子集是可满足的。

**证明**：如果 $M$ 满足 $\Gamma$ 的每个成员，那么 $M$ 满足 $\Gamma$ 的每个有限子集的每个成员。对于逆命题，假设 $\Gamma$ 是不可满足的。那么我们证明 $\Gamma$ 的某个有限子集是不可满足的。根据完全性（定理 20），$\Gamma$ 是不一致的。根据定理 9（和弱化），存在 $\Gamma$ 的一个有限子集 $\Gamma' \subseteq \Gamma$ 使得 $\Gamma'$ 是不一致的。根据推论 19，$\Gamma'$ 是不可满足的。

可靠性和完全性共同蕴涵：一个论证当且仅当它是有效的时才是可导出的，一组句子当且仅当它是可满足的时才是一致的。所以我们可以在模型论和证明论概念之间来回转换，将一个属性转移到另一个。紧致性在模型论中成立，因为所有推导都只使用有限数量的前提。

回想一下，在完全性（定理 20）的证明中，我们做了一个简化假设，即非逻辑常项集 $K$ 要么是有限的，要么是可数无限的。我们产生的解释本身要么是有限的，要么是可数无限的。因此，我们有以下内容：

**推论 23**。勒文海姆-斯科伦定理（Löwenheim-Skolem Theorem）。设 $\Gamma$ 为语言 $\mathcal{L}1K=$ 的可满足句子集。如果 $\Gamma$ 要么是有限的，要么是可数无限的，那么 $\Gamma$ 有一个域要么是有限的要么是可数无限的模型。

一般来说，设 $\Gamma$ 为 $\mathcal{L}1K=$ 的可满足句子集，令 $\kappa$ 为 $\Gamma$ 的大小和可数无限中的较大者。那么 $\Gamma$ 有一个域大小至多为 $\kappa$ 的模型。

推论 23 有一个更强的版本。设 $M_1 =\langle d_1,I_1\rangle$ 和 $M_2 =\langle d_2,I_2\rangle$ 为语言 $\mathcal{L}1K=$ 的解释。定义 $M_1$ 为 $M_2$ 的**子模型**（submodel），如果 $d_1 \subseteq d_2$，对于每个常项 $c$ 有 $I_1 (c) = I_2 (c)$，且 $I_1$ 是 $I_2$ 对 $d_1$ 的限制。例如，如果 $R$ 是 $K$ 中的二元关系字母，那么对于 $d_1$ 中的所有 $a,b$，对 $\langle a,b\rangle$ 在 $I_1 (R)$ 中当且仅当 $\langle a,b\rangle$ 在 $I_2 (R)$ 中。如果我们已经在非逻辑术语中包含了函数字母，我们还需要求 $d_1$ 在 $M_2$ 中的解释下是封闭的。注意如果 $M_1$ 是 $M_2$ 的子模型，那么 $M_1$ 上的任何变项赋值也是 $M_2$ 上的变项赋值。

称两个解释 $M_1 =\langle d_1,I_1\rangle, M_2 =\langle d_2,I_2\rangle$ 是**等价**的，如果其中一个是另一个的子模型，并且对于语言的任何公式和子模型上的任何变项赋值 $s$，$M_1,s\vDash \theta$ 当且仅当 $M_2,s\vDash \theta$。注意如果两个解释是等价的，那么它们满足相同的句子。

**定理 25**。向下勒文海姆-斯科伦定理（Downward Löwenheim-Skolem Theorem）。设 $M = \langle d,I\rangle$ 为语言 $\mathcal{L}1K=$ 的解释。设 $d_1$ 为 $d$ 的任何子集，令 $\kappa$ 为 $K$ 的大小、$d_1$ 的大小和可数无限中的最大值。那么存在 $M$ 的一个子模型 $M' = \langle d',I'\rangle$ 使得 (1) $d'$ 不大于 $\kappa$，且 (2) $M$ 和 $M'$ 是等价的。特别是，如果非逻辑术语集 $K$ 要么是有限的要么是可数无限的，那么任何解释都有一个域要么是有限的要么是可数无限的等价子模型。

**证明**：像完全性一样，这个证明很复杂，我们满足于勾勒一下。向下勒文海姆-斯科伦定理援引了选择公理，实际上，它等价于选择公理（参见关于选择公理的词条）。所以设 $C$ 为 $d$ 的幂集上的选择函数，使得对于每个非空子集 $e \subseteq d$，$C(e)$ 是 $e$ 的成员。我们规定如果 $e$ 是空集，那么 $C(e)$ 是 $C(d)$。

设 $s$ 为 $M$ 上的变项赋值，设 $\theta$ 为 $\mathcal{L}1K=$ 的公式，设 $v$ 为变项。定义 $\theta$ 在 $s$ 上的 $v$-见证（$v$-witness），写为 $w_v (\theta,s)$，如下：设 $q$ 为所有元素 $c \in d$ 的集合，使得存在一个在除 $v$ 之外所有变项上与 $s$ 一致的变项赋值 $s'$，使得 $M,s'\vDash \theta$，且 $s'(v)=c$。那么 $w_v (\theta,s) = C(q)$。注意如果 $M,s\vDash \exists v\theta$，那么 $q$ 是域中可以在 $\theta$ 中代替 $v$ 的元素的集合。实际上，$M,s\vDash \exists v\theta$ 当且仅当 $q$ 非空。所以如果 $M,s\vDash \exists v\theta$，那么 $w_v (\theta,s)$（即 $C(q)$）是可以在 $\theta$ 中代替 $v$ 的域的选定元素。在某种意义上，它是验证 $M,s\vDash \exists v\theta$ 的“见证”。

如果 $e$ 是域 $d$ 的非空子集，则定义变项赋值 $s$ 为 $e$-赋值，如果对于所有变项 $u$，$s(u)$ 都在 $e$ 中。也就是说，$s$ 是 $e$-赋值如果 $s$ 为每个变项分配 $e$ 的一个元素。定义 $e$ 的斯科伦壳（Skolem-hull），$sk(e)$，为集合：

$$ e \cup \{w_v (\theta,s) \mid \theta \text{ 是 } \mathcal{L}1K= \text{ 中的公式}, v \text{ 是变项，且 } s \text{ 是 } e\text{-赋值} \}. $$

也就是说，$e$ 的斯科伦壳是集合 $e$ 加上每个 $e$-赋值上每个公式的每个 $v$-见证。粗略地说，其思想是从 $e$ 开始，然后投入足够的元素使每个存在量化的公式为真。然而，我们不能满足于斯科伦壳。一旦我们将“见证”投入域中，我们需要处理 $sk(e)$ 赋值。实际上，我们需要一个本身是其自身斯科伦壳的集合，并且也包含给定的子集 $d_1$。

我们如下定义非空集合序列 $e_0, e_1,\ldots$：如果 $d$ 的给定子集 $d_1$ 为空且 $K$ 中没有常项，那么令 $e_0$ 为 $C(d)$，即应用于整个域的选择函数；否则令 $e_0$ 为 $d_1$ 与 $K$ 中常项在 $I$ 下的指称的并集。对于每个自然数 $n$，$e_{n+1}$ 是 $sk(e_n)$。最后，令 $d'$ 为所有集合 $e_n$ 的并集，令 $I'$ 为 $I$ 对 $d'$ 的限制。我们的解释是 $M' = \langle d',I'\rangle$。

显然，$d_1$ 是 $d'$ 的子集，所以 $M'$ 是 $M$ 的子模型。令 $\kappa$ 为 $K$ 的大小、$d_1$ 的大小和可数无限中的最大值。计算显示 $d'$ 的大小至多为 $\kappa$，基于这样的事实：至多有 $\kappa$ 多个公式，因此在每个阶段至多有 $\kappa$ 多个见证。顺便注意，这个计算依赖于这样一个事实：大小至多为 $\kappa$ 的集合的可数并集本身至多为 $\kappa$。这也依赖于选择公理。

最后一项是证明 $M'$ 等价于 $M$：对于每个公式 $\theta$ 和 $M'$ 上的每个变项赋值 $s$，

$$ M,s\vDash \theta \text{ 当且仅当 } M',s\vDash \theta. $$

证明通过对 $\theta$ 的复杂性进行归纳来进行。不幸的是，篇幅限制要求我们将这一步留作练习。

紧致性（推论 22）的另一个推论是勒文海姆-斯科伦定理的反面：

**定理 26**。向上勒文海姆-斯科伦定理（Upward Löwenheim-Skolem Theorem）。设 $\Gamma$ 为 $\mathcal{L}1K=$ 的任何句子集，使得对于每个自然数 $n$，存在解释 $M_n = \langle d_n,I_n\rangle$，使得 $d_n$ 至少有 $n$ 个元素，且 $M_n$ 满足 $\Gamma$ 的每个成员。换句话说，$\Gamma$ 是可满足的，且满足 $\Gamma$ 每个成员的解释的大小没有有限上限。那么对于任何无限基数 $\kappa$，存在解释 $M=\langle d,I\rangle$，使得 $d$ 的大小至少为 $\kappa$ 且 $M$ 满足 $\Gamma$ 的每个成员。

**证明**：向语言中添加一组大小为 $\kappa$ 的新常项 $\{c_{\alpha} \mid \alpha < \kappa \}$，使得如果 $c$ 是 $K$ 中的常项，则 $c_{\alpha}$ 不同于 $c$，且如果 $\alpha < \beta < \kappa$，则 $c_{\alpha}$ 是与 $c_{\beta}$ 不同的常项。考虑由 $\Gamma$ 和集合 $\{\neg c_{\alpha}=c_{\beta} \mid \alpha \ne \beta \}$ 组成的句子集 $\Gamma'$。也就是说，$\Gamma'$ 由 $\Gamma$ 以及大意为任何两个不同的新常项表示不同对象的陈述组成。设 $\Gamma''$ 为 $\Gamma'$ 的任何有限子集，令 $m$ 为出现在 $\Gamma''$ 中的新常项的数量。然后将解释 $M_m$ 扩展为新语言的解释 $M_m'$，方法是将 $\Gamma''$ 中的每个新常项解释为域 $d_m$ 的不同成员。根据假设，$d_m$ 中有足够的成员来做这件事。可以随意解释其他新常项。所以 $M_m$ 是 $M_m'$ 的限制。根据假设（和定理 15），$M'_m$ 满足 $\Gamma$ 的每个成员。此外 $M'_m$ 满足 $\Gamma''$ 中 $\{\neg c_{\alpha}=c_{\beta} \mid \alpha \ne \beta \}$ 的成员。所以 $M'_m$ 满足 $\Gamma''$ 的每个成员。根据紧致性，存在解释 $M = \langle d,I\rangle$ 使得 $M$ 满足 $\Gamma'$ 的每个成员。由于 $\Gamma'$ 包含 $\{\neg c_{\alpha}=c_{\beta} \mid \alpha \ne \beta \}$ 的每个成员，$M$ 的域 $d$ 的大小必须至少为 $\kappa$，因为每个新常项必须有不同的指称。根据定理 15，$M$ 对原始语言 $\mathcal{L}1K=$ 的限制满足 $\Gamma$ 的每个成员。

结合起来，向下和向上勒文海姆-斯科伦定理的证明表明，对于任何可满足的句子集 $\Gamma$，如果 $\Gamma$ 的模型没有有限界限，那么对于任何无限基数 $\kappa$，存在 $\Gamma$ 的一个模型，其域的大小恰好为 $\kappa$。此外，如果 $M$ 是任何域为无限的解释，那么对于任何无限基数 $\kappa$，存在一个解释 $M'$，其域的大小恰好为 $\kappa$，使得 $M$ 和 $M'$ 是等价的。

这些结果表明像 $\mathcal{L}1K=$ 这样的一阶语言在表达资源上的弱点。没有任何可满足的句子集能保证其模型都是可数无限的，也没有任何可满足的句子集能保证其模型是不可数的。所以在某种意义上，一阶语言不能表达“可数无限”的概念，至少在模型论中不能。（参见关于二阶和高阶逻辑的词条。）

设 $A$ 为一阶语言 $\mathcal{L}1K=$ 中的任何句子集，其中 $K$ 包含算术术语，并假设 $A$ 的每个成员对自然数都为真。我们甚至可以让 $A$ 为 $\mathcal{L}1K=$ 中所有对自然数为真的句子的集合。那么 $A$ 有不可数的模型，实际上有任何无限基数的模型。这种解释属于有时被称为算术的非预期模型（unintended models）或非标准模型（non-standard models）。设 $B$ 为任何对实数成立的一阶句子集，设 $C$ 为集合论的任何一阶公理化。那么如果 $B$ 和 $C$ 是可满足的（在无限解释中），那么它们每一个都有可数无限的模型。也就是说，任何一阶的、可满足的集合论或实数理论，都有（非预期的）自然数大小的模型。这是尽管（看似）陈述宇宙是不可数的句子在大多数集合论中是可证明的事实。这种情况被称为斯科伦悖论（Skolem paradox），引发了很多讨论，但我们必须让读者参考别处以获取其样本（参见关于斯科伦悖论和 Shapiro 1996 的词条）。

## 6. 唯一正确的逻辑？ (The One Right Logic?)

逻辑肯定与正确推理有关，或者至少与正确演绎推理有关。这种联系的细节是微妙且有争议的——参见 Harman [1984] 的有影响力的研究。通常我们会说，如果一个人没有逻辑地推理，他就推理得很差，或者如果一个给定的（演绎）论证被证明是无效的，那么它就是糟糕的，必须撤回。

一些哲学家和逻辑学家坚持认为，在表征有效性的作用中，只有一个逻辑系统是唯一正确的。其中，一些人，也许是大多数人，赞成经典一阶逻辑是唯一正确的，即“唯一真逻辑”（One True Logic）。例如，参见 Quine [1986], Resnik [1996], Rumfitt [2015], Williamson [2017] 以及许多其他人。

经典一阶逻辑被赋予这一角色也许并不令人惊讶。它具有或多或少直观的规则，而且对于其强度而言是简单的。正如我们在第 5 节中看到的，经典一阶逻辑具有有趣且重要的元理论属性，如可靠性和完全性，这些属性导致了许多重要的数学和逻辑研究。

然而，如前所述，经典一阶逻辑的主要元理论属性导致了形式语言和模型论语义学的表达限制。像有限性、可数性、最小封闭性、自然数等关键概念无法被表达。

Barwise [1985, 5] 曾经评论道：

> 作为逻辑学家，我们通过让别人相信逻辑是一阶的，然后让他们相信现代数学的概念几乎没有一个能真正被一阶逻辑捕捉到，从而对我们的学科造成了损害。

Wang [1974, 154] 也说：

> 当我们对集合论或经典分析感兴趣时，勒文海姆-斯科伦定理通常被视为一阶逻辑的一种缺陷……[这]些定理所建立的不是一阶逻辑是唯一可能的逻辑，而是当我们某种意义上否认不可数概念的现实性时，它是唯一可能的逻辑……

对经典一阶逻辑的其他批评也被提出。它在处理某些悖论（例如，参见罗素悖论的词条）方面存在问题，它明显过度生成信念（参见逻辑的规范地位的词条），有些人认为它有一些论证与我们通常认为的思维方式不符（例如，参见相关逻辑的词条）。

对于那些批评经典一阶逻辑作为唯一真逻辑的人来说，主要有两个选择。一是提出某种其他逻辑作为唯一真逻辑。Priest [2006a] 描述了人们可能用来确定唯一真逻辑的方法论。

另一个主要选择是简单地否认存在一个有资格成为唯一真逻辑的单一逻辑。这种观点的一个实例是一种逻辑虚无主义（logical nihilism），即没有正确逻辑的论点。另一个是逻辑多元主义（logical pluralism），即各种不同的逻辑都有资格作为正确的，或最好的，甚至真的逻辑，至少在各种语境中。

当然，这里不是详细探讨这个问题的地方。参见 Beall 和 Restall [2006] 和 Shapiro [2014] 关于多元主义的例子，以及关于逻辑多元主义的词条，以了解逻辑多元主义和逻辑虚无主义的概况。

我们以对经典一阶逻辑的一些主要替代方案的简要勾勒结束，并提供对本百科全书其他工作和词条的参考。另见 Shapiro 和 Kouri Kissel [2022] 的后半部分。

### 6.1 经典一阶逻辑的竞争对手 (Rivals to classical, first-order logic)

近年来，已经做了一些工作来“逼近”经典逻辑。其想法是尽可能接近经典逻辑，以保留其一些好处，同时消除经典逻辑的一些限制，比如更接近直觉推理或应用于模糊性和悖论等事物。

例如，Barrio, Pailos 和 Szmuc [2020] 表明我们可以在所谓的 ST 层级（ST 代表严格-宽容，来自 Cobreros, Egre, Ripley 和 van Rooij [2012a,b]）中逼近经典逻辑。这使他们能够在层级的每个级别避免某些经典问题，如某些悖论，同时在考虑整个层级时保持经典逻辑强度的许多好处。

Dave Ripley [2013] 提供了“经典逻辑”的多矢算版本，他认为这解决了一些悖论。值得注意的是，他声称它至少解决了堆垛悖论（Sorites Paradox）和说谎者悖论（Liar Paradox）（参见关于堆垛悖论和说谎者悖论的词条）。该系统保守地扩展了经典逻辑。Ripley 声称这就是使其成为经典的原因。然而，该系统不是传递的，也没有剪切规则。

当然，关于这些新逻辑是否真的是经典的，存在一些问题，但这仍然是有益的工作。

扩展经典一阶逻辑的一种方法是向底层形式语言添加额外的算子。模态逻辑添加了指定必然性和可能性的算子。所以，我们可以说一个命题可能是真的，或者必然是真的，而不仅仅是真的。

W. V. O Quine [1953] 曾经争辩说，量词在模态算子内部约束变项是不连贯的，但对此事的看法已经发生了很大变化（例如，参见 Barcan [1990]）。现在有一个繁荣的产业正在开发模态逻辑以捕捉各种模态和时态算子。参见关于模态逻辑的词条。

上面勾勒的所有形式语言都只有一种变项。这些有时被称为一阶变项。语言的每个解释都有一个域，这是一阶变项的范围。根据给定的解释，这就是语言所关于的内容。二阶变项的范围是该域中项目的属性、集合、类、关系或函数。三阶变项的范围是二阶变项范围内的任何东西的属性、类、关系。依此类推。

如果形式语言有二阶变项和一阶变项，没有其他变项，则称为二阶的；如果有三阶、二阶和一阶变项，没有其他变项，则称为三阶的，等等。如果形式语言至少是二阶的，则称为高阶的。

如前所述，说经典一阶逻辑是当代逻辑理论的范式并不夸张。大多数教科书根本不提得高阶语言，其余的大多数也只给予很少的处理。

已经为二阶和高阶语言提出了许多不同的演绎系统和模型论语义学。对于语义学，模型论的主要额外特征是指定高阶变项的范围。

在亨金语义学（Henkin semantics）中，每个解释指定高阶变项的特定范围。对于单子二阶变项，每个解释指定域的幂集的一个非空子集，对于二元二阶变项，指定域成员的有序对的一个非空集合，等等。该系统具有上述所有的限制性元理论结果。存在一个对亨金语义学可靠且完全的演绎系统；逻辑是紧致的；向下和向上勒文海姆-斯科伦定理都成立。

在所谓的标准语义学（standard semantics），有时称为完全语义学（full semantics）中，单子二阶变项的范围是域的整个幂集；二元二阶变项的范围是域成员有序对的整个类，等等。可以证明，具有标准语义学的二阶语言可以表征许多数学概念和结构（直到同构）。例子包括有限性、可数性、良基性、最小封闭性以及像自然数、实数和复数这样的结构的概念。结果，经典一阶逻辑的限制性定理都不成立：没有有效的演绎系统既可靠又完全，逻辑不是紧致的，两个勒文海姆-斯科伦定理都失效。一些人，如 Quine [1986]，认为具有标准语义学的二阶逻辑实际上不是逻辑，而是一种数学形式，特别是集合论。关于这一点的更多信息，请参见 Shapiro [1991] 和关于高阶逻辑的词条，以及那里引用的许多参考文献。

人们也可以考虑将广义量词（generalized quantifiers）作为经典一阶逻辑的扩展（参见关于广义量词的词条）。这些量词允许在经典的“所有”和“一些”之间进行扩展，并可以容纳像“大多数”、“少于一半”、“通常”等量词。它们从逻辑和语言学的角度来看都是有用的。例如，Kennedy 和 Väänänen [2021] 使用广义量词来论证“不可数”是一个逻辑概念。

### 6.2 经典一阶逻辑的子逻辑 (Sublogics of classical, first-order logic)

一些哲学家和逻辑学家认为经典一阶逻辑太强了：它宣称某些论证形式是有效的，而实际上并不是。这里我们勾勒两种提议。

直觉主义逻辑的拥护者拒绝（所谓的）排中律的有效性：

$$ (\Phi \vee \neg \Phi) $$

以及与此相关的其他推论，如双重否定消除（DNE）：

$$ \neg \neg \Phi \vdash \Phi $$

粗略地说，这些限制有两个主要的动机。传统的直觉主义者 L. E. J. Brouwer（例如，[1964a], [1964b]）和 Arend Heyting（例如 [1956]）认为数学的本质是理想化的心理构造。例如，考虑命题：对于每个自然数 $n$，存在一个素数 $m > n$ 使得 $m < n!+2$。对于 Brouwer 来说，这个命题调用了一个程序，该程序给定任何自然数 $n$，产生一个大于 $n$ 但小于 $n!+2$ 的素数 $m$。该命题表达了这种程序的存在。鉴于这种取向，我们没有理由认为对于任何数学命题 $\Phi$，我们可以建立与 $\Phi$ 相关的程序或与 $\neg \Phi$ 相关的程序。

Michael Dummett（例如，[1978]）提供了关于语言如何作为交流工具发挥作用的一般论证，以论证直觉主义逻辑是唯一正确的，即唯一真逻辑，而不仅仅是对于数学。

关于直觉主义逻辑及其哲学动机的概述，请参见关于直觉主义逻辑的词条。

这次要宣布无效的目标推论是我们上面称为 *ex falso quodlibet*，缩写为 (EFQ) 的推论：

$$ \text{如果 } \Gamma_1 \vdash \Theta \text{ 且 } \Gamma_2 \vdash \neg\Theta \text{ 那么 } \Gamma_1, \Gamma_2 \vdash \Psi $$

我们可以关注这类推论的一种情况：

$$ \Phi, \neg\Phi \vdash \Psi $$

有时被形象地称为“爆炸”。它说任何东西都从矛盾中得出。

视 (EFQ) 为无效的逻辑称为次协调逻辑（paraconsistent）。广义地说，有两个阵营的逻辑学家倡导次协调系统，要么作为唯一真逻辑的候选者，要么作为多元主义的实例。一个阵营由坚持在有效论证中前提必须与结论相关的逻辑学家组成。通常，相关逻辑学家（relevance logicians）也反对某些被称为实质蕴涵悖论的经典逻辑真理，如 $(\Phi \rightarrow (\Psi \rightarrow \Phi))$ 和 $(\Phi \rightarrow (\Psi \rightarrow \Psi))$。

更多信息，请参见关于相关逻辑的词条，或 Kerr [2019]。经典著作包括 Anderson 和 Belnap [1975], Anderson Belnap 和 Dunn [1992], 和 Read [1988]。Neil Tennant [2017] 的核心逻辑既是相关的又是直觉主义的。

另一个偏爱次协调逻辑（或多种次协调逻辑）的主要逻辑学家阵营是双面真理主义（dialetheism）的拥护者，即认为某些矛盾，某些形式为

$$ (\Phi \& \neg \Phi) $$

的句子是真的。一个假定的例子是当 $\Phi$ 是语义悖论的陈述时，例如说谎者悖论。例如，考虑一个说 $\Phi$ 不为真的句子 $\Phi$。

在一个 (EFQ) 成立的系统中，任何真的矛盾都会蕴涵形式语言的每个句子，从而使语言和理论变得微不足道。所以，显然，任何用于双面真理主义的逻辑都必须是次协调的。参见关于双面真理主义的词条。这里的经典著作是 Priest [2006a]。

当然，这里展示的小样本并不包括作为经典一阶逻辑竞争对手提出的每个逻辑系统，同样要么作为唯一真逻辑的候选者，要么作为逻辑多元主义的进一步实例。例如，参见关于亚结构逻辑、模糊逻辑和许多其他的词条。
