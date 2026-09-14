# SDUTHESIS: 山东大学本科毕业论文（理工类）模板

## 简介

`sduthesis` 是为山东大学理工类专业的本科毕业论文而设计的 LaTeX 模板。该模板基于[《山东大学本科毕业论文（设计）撰写规范》](docs/standards-2024.pdf)而编写，旨在帮助学生快速、高效地排版本科毕业论文。

## 主要功能

- **页面与文本格式**：自动配置符合规范的页面设置、字体和段距。
- **图表支持**：提供图表插入与自动编号功能，支持单图和子图。
- **数学公式**：集成常用数学宏包，搭配 `unicode-math` ，支持复杂公式的排版。
- **参考文献管理**：基于 `biblatex` 宏包，支持 GB/T 7714-2015 国家标准的文献引用格式。
- **结构清晰**：封面、摘要、目录、正文和附录等部分自动生成，无需担心格式问题。

## 使用说明

- **编译方式**：对主源文件 `main.tex` 按照 `xelatex->biber->xelatex->xelatex` 的顺序编译得到输出 PDF 文档 `main.pdf` 。
- **使用平台**：
  - 在中文 Windows 操作系统与较新的 TeXLive 本地发行版环境下，在 Visual Studio Code 中搭配 LaTeX Workshop 扩展使用。`.vscode/settings.json` 中提供了可能会优化使用体验的 Visual Studio Code 局部设置。
  - 在 Overleaf 平台上使用，编译器设置为 `xelatex` ，主文档设置为 `main.tex` ，TeXLive 版本选择较新版即可。注：在 Overleaf 平台上使用时，可能会产生 `fontspec` 宏包的 `Script` 警告，该警告不会对文档的编译造成影响，忽略即可。
  - 在 Windows 操作系统与 TeXstudio （版本4.8.1）中使用，直接用TeXstudio打开main.tex即可，编译配置方法见下方“模板在TexStudio中的使用”部分。

详细使用方法、配置说明与示例，请参考 [PDF 版本说明文档](README.pdf)。

## 模板在TeXstudio中的编译与使用

本人使用该仓库编译论文时使用的是TeXstudio 4.8.1，稍微探索了一下，将在TeXstudio编译论文的方法整理如下：

### Step 1: 打开“选项”

点击TeXstudio上方工具栏的“选项”按钮，如下图所示

![Step1](https://raw.githubusercontent.com/InfiniteBoyEric/sduthesis_for_undergraduate/main/img_for_README/step1.png)

### Step 2: 打开“设置”

点击“设置 TeXstudio”，如下图所示

![Step2](https://raw.githubusercontent.com/InfiniteBoyEric/sduthesis_for_undergraduate/main/img_for_README/step2.png)

### Step 3: 打开“构建”

在弹出的“设置 TeXstudio”窗口中点击“构建”，如下图所示

![Step3](https://raw.githubusercontent.com/InfiniteBoyEric/sduthesis_for_undergraduate/main/img_for_README/step3.png)

### Step 4: 添加用户命令

在“用户命令”处点击“+ 添加”，首先对命令进行命名，然后可在右侧输入框中直接输入`txs:///xelatex | txs:///biber | txs:///xelatex | txs:///xelatex | txs:///view-pdf-internal`，点击“确认”，直接跳转至Step 7；或也可以看到最右侧有一个齿轮图标的设置按钮，如下图所示

![Step4](https://raw.githubusercontent.com/InfiniteBoyEric/sduthesis_for_undergraduate/main/img_for_README/step4.png)

### Step 5: 添加构建命令
点击Step 4中看到的齿轮图标设置按钮，在弹出的窗口中，先点击左侧要添加的命令，然后点击中间的“添加”按钮，就可以将命令添加至右侧“选定的命令列表”了；依此添加`XeLaTex`-`Biber`-`XeLaTex`-`XeLaTex`-`内置 PDF 查看器`（注意顺序不能错，错了也可通过右侧下方的“向上”“向下”按钮调整；每一步命令具体在做什么建议询问AI），如下图所示

![Step5](https://raw.githubusercontent.com/InfiniteBoyEric/sduthesis_for_undergraduate/main/img_for_README/step5.png)

### Step 6: 完成命令构建

完成构建后右侧从上至下的顺序应当与下图一致，点击“确认”，再点击“确认”完成所有设置

![Step6](https://raw.githubusercontent.com/InfiniteBoyEric/sduthesis_for_undergraduate/main/img_for_README/step6.png)

### Step 7: 使用用户命令编译

在TeXstudio上方工具栏的“工具”选项下，可以看到“用户”一栏，其下就有刚刚命名好的用户命令，直接点击即可开始编译，或者后续直接使用其后提示的快捷键（比如我这里是 `Alt + Shift + F1`）启动编译，如下图所示

![Step7](https://raw.githubusercontent.com/InfiniteBoyEric/sduthesis_for_undergraduate/main/img_for_README/step7.png)

## 其他补充

### 关于格式

在最终提交的论文至系统时，直接编译生成的这篇论文格式还需要做如下调整：

1. 目录交叉引用的颜色（蓝色->黑色）：`./config/main/config-main.tex`中有字段`\hypersetup{ colorlinks=true, linkcolor=blue, urlcolor=linkdarkblue, citecolor=red, }`，改为`\hypersetup{colorlinks=true, linkcolor=black, urlcolor=black, citecolor=black, }`
2. 公式、表格、图片编号交叉引用的颜色（蓝色->黑色)：同上
3. 参考文献上角标交叉引用的颜色（红色->黑色）：同上
4. 参考文献作者名规范（应当调整为姓在前、名在后）:`./config/main/config-main.tex`中有字段`\usepackage[backend=biber, style=gb7714-2015, gbnamefmt=givenahead, gbpunctin=false]{biblatex}`，其中`gbnamefmt`可取的值有`uppercase`（默认值，姓名所有字母大写）、`lowercase`（不对姓名大小写做处理，保持 `.bib` 文件中的原始输入）、`givenahead`（名在前、姓在后）、`familyahead`（姓在前、名在后）等，因此姓前名后可以将`gbnamefmt=givenahead`直接改为`gbnamefmt=familyahead`

### 细节提醒

1. 会议论文集在一些论文网站的Cite生成的`.bib`文件或BibTex中易缺失会议地点/出版商，须自行补充
2. 所有英文文献应当统一格式：英文题目要么只有第一个单词首字母大写，要么每个单词首字母大写（介词preposition、连词conjunction、副词adverb应小写）；英文期刊/会议名每个单词首字母大写

## 联系方式

本仓库fork自[此处](https://github.com/wangzhukang/sduthesis)，如有问题或建议，建议通过以下渠道联系原作者：

- email：zhukangwang1005@gmail.com
- issue/pr：[GitHub - sduthesis](https://github.com/wangzhukang/sduthesis) 
