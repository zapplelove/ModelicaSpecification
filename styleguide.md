# Modelica规范样式指南

这是Modelica规范文档的样式指南。


## 文档格式和工具链

该文档的源格式为LaTeX，源文件由pdfLaTeX和LaTeXML处理。
了解LaTeXML的含义是很好的，但是对于大多数贡献者和贡献来说，只检查pdfLaTeX输出是否良好就足够了，其思想是，在拉请求审查过程中应该发现潜在的问题。

本风格指南中描述的MSL-specific的LaTeX宏和环境定义在以下两个文件中:
- [preamble.tex](preamble.tex) – 主要文件的序言内容。
- [mlsshared.sty](mlsshared.sty) – 提取的样式部分将与其他应遵循相同样式的文档共享，如许多图形。


## 源代码格式化

### 尾随空格和空行

末尾不能有空格，每行(特别是文件的最后一行)应以换行符结束。
一个文件的开头和结尾不能有空行，并且一行中不能有超过两个空行。
在分区命令(如`\section`或`\subsubsection`)之前使用一到两个空行，文件的开头除外。
也建议在非段落分段命令之后设置空行。

在添加空行时要小心，因为它们实际上在诸如列表环境之前(`itemize`等)等地方是很重要的。
例如，如果列表前的文本是介绍，那么它应该与列表保持紧密联系:
```
下面的操作适用于切片操作:
\begin{itemize}
\item
    …
```

### 段落内的硬线

文档正在转换为 _one sentence per line_ 的源代码格式。
这意味着任何修改过的或新的文本都应该在源文件的单个物理行中单独包含每个句子。

当一个句子不适合一个屏幕行时，可以把这当作一个长句子会降低规范文档的可读性的提醒，并考虑将长句子拆分成更短的句子。
请记住，这样做的目的应该是提高规范文本的可读性，而不是提高 _one sentence per line_ 的格式化源代码的可读性。

一旦我们在正确的位置有了物理的断线，未来变化的差异就会变得清晰和容易把握，合并冲突也会更容易解决。

### 缩进

当缩进LaTeX环境的内容时，将使用2个空格的缩进。
建议不要在`\item`前添加缩进::
```
\begin{itemize}
\item
  首先是原始函数的所有输入，在这些输入之后，我们将为每个包含实数的输入附加一个导数。
  对于函数及其导数，这些公共输入必须具有相同的名称、类型和声明顺序。
\item
  构造输出的方法是先从一个空列表开始，然后按顺序为每个包含实数的输出附加一个导数。
  对于函数及其导数，输出必须具有相同的类型和声明顺序。
\end{itemize}
```

许多环境在使用时不缩进内容，包括`nonnormative`和`example`:
```
\begin{nonnormative}
这意味着最具限制性的导数应该先写出来。
\end{nonnormative}
```

## 语言术语的格式

### 语言中带有名称/关键字的内容

一般的规则是，当一个概念与Modelica语言中具有特定名称/关键字的结构直接相关时，使用代码风格的语言名称/关键字的连字符组合来引用该语言概念，并使用一个合格的自然语言单词作为普通文本编写。
例如:


Appearance | LaTeX source | Comment
--- | --- | ---
`connect`-equation | `\lstinline!connect!-equation` |
`if`-equation | `\lstinline!if!-equation` |
`if`-expression | `\lstinline!if!-expression` |
`when`-clause | `\lstinline!when!-clause` | A branch of a `when`-equation or `when`-statement
`import`-clause | `\lstinline!import!-clause` |
`for`-equation | `\lstinline!for!-equation` |
`for`-statement | `\lstinline!for!-statement` |
`for`-loop | `\lstinline!for!-loop` | A `for`-equation or `for`-statement
`start`-attribute | `\lstinline!start!-attribute` |


请注意，Modelica语法中经常有一个相关的规则，只有在极少数情况下，当它是实际的语法规则(而不是整个语言概念)被引用时，才应该在文本中使用它:

Appearance | LaTeX source
--- | ---
`if-equation` | `\lstinline[language=grammar]!if-equation!`

注意:连字符有时可能出现语法错误，但始终使用连字符有助于提高可读性，而且在某些情况下，连字符为阅读语言名称/关键字作为句子结构的一部分提供了额外的安全。
例如,请比较:
- 如果在翻译过程中求出它们的条件，方程可以简化。
- 如果`if`-方程的条件可以在翻译过程中求出，那么它就有可能被简化。

### 表达式

使用`_expression_`和`_call_`的不同结构:


Appearance | LaTeX source | Comment
--- | --- | ---
`if`-expression | `\lstinline!if!-expression` | Generic language concept
parameter-expression | `parameter-expression` | Expression with parameter variability
`Real` expression | `\lstinline!Real! expression` | Expression of type `Real`
array expression | `array expression` | Expression of array type
record expression | `record expression` | Expression of record type
`y` expression | `\lstinline!y! expression` | Expression for something named `y`
`convertElement` call | `\lstinline!convertElement! call` | A call expression with callee `convertElement`


特别是，避免使用内联代码和 _expression_ 的其他组合，而不是上面的变体。
对于其他需要，尽量找到一个不基于表达式的公式，以避免根据上述变体的误解。
例如，不要说“… can be dependent on class variables using the `DynamicSelect` expression”，而是说“… can be dependent on class variables using `DynamicSelect`”。

注意: There is no need for hyphenation of "`convertElement` call" since we don't say "`Real` call" for a call expression of type `Real` (we have "`Real` expression" for this purpose).

### 关键词本身

当引用关键字本身时，不使用连字符，在可能的情况下，使用比 _keyword_ 更好的描述词:

Appearance | LaTeX source | Comment
--- | --- | ---
the `input` prefix | `\lstinline!prefix! prefix` | For more prefixes, see `class-prefixes`, `base-prefix`, and `type-prefix` in the grammar.
the `final` modifier | `the \lstinline!final! modifier` |
the `each` keyword | `the \lstinline!each! keyword` |

根据上下文，还可以交换顺序，或者完全省略描述词:

Appearance | LaTeX source
--- | ---
the keyword `each` | `the keyword \lstinline!each!`
declared as `final` | `declared as \lstinline!final!`

### 命名函数和操作符

当引用operator的命名函数时，不使用连字符，并且通常不与任何描述词组合:

Appearance | LaTeX source
--- | ---
the `smooth` operator | `the \lstinline!smooth! operator`
where `pre` is not explicitly used | `where \lstinline!pre! is not explicitly used`

### 还有一些特殊情况

带有特殊格式规则的各种术语的不完整列表:

Appearance | LaTeX source | Comment
--- | --- | ---
start value | `start value` | Value of the `start`-attribute (there could be exceptions!)
connection equation | `connection equation` | Equation generated from analysis of `connect`-equations
reduction expression | `reduction expression` |
base class | `base class` | Similarly: derived class
base-clock | `base-clock` | Similarly: sub-cock

## 定义

新术语要么在`definition`环境中引入，要么作为运行文本的一部分引入。
当运行文本的一部分时，引入的术语应该在定义处标记为`\firstuse`。
一般来说，用`\firstuse`引入的术语应该出现在文档索引中，默认情况下，`\firstuse`的强制参数会自动传递给`\index`。
要改变索引条目的外观，可以使用`\firstuse`的可选参数重写默认值，例如 `\firstuse[array!variable]{array variable}`.
当大写或复数/单数不同时，这也很有用;除了像名字这样的东西，索引中应该使用小写字母，而术语通常应该以单数形式出现，例如，`\firstuse[vector]{Vectors}`.
在很少的情况下，人们只想要`\firstuse`的标准化排版，但索引中没有条目，这可以通过为可选参数传递一个破折号来实现，例如， `\firstuse[---]{constant}`.
当抑制索引中的出现时，建议在源文件中添加注释解释原因。
使用`\firstuse`后，通常会直接调用`\index`，以便在文档索引中添加更多变体中的术语。

If the new terminology is used before being introduced, it should be marked with `\willintroduce` (instead of `\firstuse`) to alert the reader that this is not a term that is expected to be known yet by a first-time reader.

## Miscellaneous

### Use of `\emph` and italics

To put emphasis on a word or small piece of text, use `\emph`.

Italics is used via the semantic macros `\firstuse` and `\willintroduce` when new terminology is introduced in the running text instead of the bulkier `definition` environment.

Refrain from using non-semantical font switching commands for producing italics (`\textit`, `\textsl`, `\itshape`).

Note that the document is full of text set in italics, since this is used for both non-normative text and examples, through the `nonnormative` and `example` environments.

### Use of boldface

Non-semantical font switching commands for producing boldface (`\textbf`, `\bfseries`) may only be used for styling as part of higher level semantic constructs such as the _amsthm.sty_ `\newtheoremstyle` definitions.
For purposes of marking emphasis, see use of `\emph` instead.

### Ordinals

Ordinals are written with _th_ in normal font, possibly combined with a math styled expression for the number:
```
Fixed ordinals: 1st, 2nd, 3rd.
Symbolic ordinals: $n$th, $(n+1)$th.
```

## Code listings

### Modelica listings

Modelica listings are written with indentation in steps of 2 spaces.

A space is typically added on each side of a binary operator, and after comma.

Code snippets may start with an indented line as long as there's some line in the listing with zero indentation, like this:
```
  Real x(start = 1.0, fixed = true);
equation
  der(x) = -x;
```

Each line should fit within the width of the page.
Use hard line breaks and manual additional indentation of continued lines to meet this requirement.
A semicolon in a matrix should either be followed by a line break or by a space.

### Grammar (extended BNF) listings

Grammar listings use the `language=grammar`, and are written with indentation in steps of 3 spaces:
```
\begin{lstlisting}[language=grammar]
stored-definition :
   [ within [ name ] ";" ]
   { [ final ] class-definition ";" }
\end{lstlisting}
```

When a grammar rule is mentioned in the text, the rule shall be formatted with the _grammar_ language:
```
The node shall contain a \lstinline[language=grammar]!stored-definition! that…
```

## English natural language text

This section gives guidelines for how the natural language text in English should be written.

The text is written in American English.

### Contractions

Avoid contractions such as _isn't_ or _won't_; write _is not_ or _will/would not_ instead.

### Inline code at beginning of sentence

When a sentence starts with inline code,
> `import`-clauses are not inherited.

this may be rewritten using _The_ inserted before the inline code to avoid a lower case letter at the beginning of the sentence:

> The `import`-clauses are not inherited.
