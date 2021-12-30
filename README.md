<img src="https://github.com/modelica/MA-Logos/raw/master/HighRes/Modelica_Language.svg?sanitize=true" width="250px"/>

# Modelica规范
这个存储库包含Modelica语言规范，托管在https://github.com/modelica/ModelicaSpecification。开发活动由[Modelica Association Project Language (MAP-LANG)](https://modelica.org/projects)组织。

## 描述

Modelica®是一种用于信息物理系统建模的语言，支持由数学方程控制的组件的因果连接，以促进从第一性原理建模。
它提供了面向对象的结构，便于模型的重用，并且可以方便地用于复杂系统的建模，包括机械、电气、电子、磁性、液压、热、控制、电力或面向过程的子组件。

## 发行

版本    | 链接                                                               | 发行年份 |
------- | ----------------------------------------------------------------- | --------|
3.6-dev | [Master branch](https://github.com/modelica/ModelicaSpecification/tree/master) [HTML](https://specification.modelica.org/master/) [PDF](https://specification.modelica.org/master/MLS.pdf)| not yet |
3.5 | [3.5 branch](https://github.com/modelica/ModelicaSpecification/tree/maint/3.5) [HTML](https://specification.modelica.org/maint/3.5/MLS.html) [PDF](https://specification.modelica.org/maint/3.5/MLS.pdf)| 2021 |
3.4     | [3.4 branch](https://github.com/modelica/ModelicaSpecification/tree/maint/3.4) [HTML](https://specification.modelica.org/maint/3.4/MLS.html) [PDF](https://modelica.org/documents/ModelicaSpec34.pdf)          | 2017    |
3.3rev1 | [PDF](https://modelica.org/documents/ModelicaSpec33Revision1.pdf) | 2014    |
3.2rev2 | [PDF](https://modelica.org/documents/ModelicaSpec32Revision2.pdf) | 2013    |
3.2rev1 | [PDF](https://modelica.org/documents/ModelicaSpec32Revision1.pdf) | 2012    |
3.3     | [PDF](https://modelica.org/documents/ModelicaSpec33.pdf)          | 2012    |
3.2     | [PDF](https://modelica.org/documents/ModelicaSpec32.pdf)          | 2010    |
3.1     | [PDF](https://modelica.org/documents/ModelicaSpec31.pdf)          | 2009    |
3.0     | [PDF](https://modelica.org/documents/ModelicaSpec30.pdf)          | 2007    |
2.2     | [PDF](https://modelica.org/documents/ModelicaSpec22.pdf)          | 2005    |
2.1     | [PDF](https://modelica.org/documents/ModelicaSpec21.pdf)          | 2004    |
2.0     | [PDF](https://modelica.org/documents/ModelicaSpec20.pdf)          | 2002    |
1.4     | [PDF](https://modelica.org/documents/ModelicaSpec14.pdf)          | 2000    |
1.3     | [PDF](https://modelica.org/documents/ModelicaSpec13norev.pdf)     | 1999    |
1.2     | [PDF](https://modelica.org/documents/modelicaspec12norev.pdf)     | 1999    |
1.1     | [PDF](https://modelica.org/documents/ModelicaSpec11.pdf)          | 1998    |
1.0     | [PDF](https://modelica.org/documents/Modelica1.pdf)               | 1997    |

发布版本的更多信息: https://www.modelica.org/documents

## 贡献
1. 如果你发现一个错误，并且不确定你可以纠正它，首先检查它是否已经报告，然后打开一个[issue](https://github.com/modelica/ModelicaSpecification/issues)详细描述它——重点是为什么应该更改它。
2. 如果你有信心你可以纠正这个问题，fork这个存储库并创建一个pull-request，在pull-request中解释这个问题和纠正;你还必须签署一份CLA。
3. 重要的扩展被处理为Modelica变更建议(MCPs)。这可以从对建议的扩展的简单描述开始。然后，它将被用于有一个基本原理来解释更改如何帮助用户，并证明它可以有效地实现;最后是一个带有更改的pull-request。

有关详细信息，请参见[Development Process](https://github.com/modelica/ModelicaSpecification/blob/master/RationaleMCP/DevelopmentProcess.md)。
mcp的列表可以在这里找到:[RationaleMCP](https://github.com/modelica/ModelicaSpecification/tree/master/RationaleMCP).

CLA:贡献者的许可协议。(细节如下)

如何编辑和生成最终的文档
* 阅读[style guide](styleguide.md).
* 对于在线编辑，您可以使用www.overleaf.com (详情如下)
* pdf文件是用pdflatex生成的，这是大多数LaTeX安装的一部分，我们使用http://miktex.org/download
* html文档使用LaTeXML生成。这是更复杂的安装-可以选择跳过:
1. 首先你需要perl，我们使用http://strawberryperl.com/
2. 然后是官方的LaTeXML包(0.8.5或更新): http://dlmf.nist.gov/LaTeXML/get.html#SS4.SSS0.Px1 或 https://github.com/brucemiller/LaTeXML
3. 确切的命令在Makefile中

也可以在pull请求中获得预览。
会有一个链接到[status check](https://test.openmodelica.org/jenkins/job/ModelicaAssociation/job/ModelicaSpecification/view/change-requests/)，它会检查文档是否可以生成，并提供下载选项。
