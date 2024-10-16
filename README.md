# sduthesis: 山东大学本科毕业论文（理工类）模板

## 简介

`sduthesis` 是为山东大学理工类专业的本科毕业论文（设计）的 LaTeX 模板。该模板基于《山东大学本科毕业论文（设计）撰写规范》而编写，旨在帮助学生快速、高效地排版本科毕业论文。

## 主要功能

- **页面与文本格式**：自动配置符合规范的页面设置、字体和段距。
- **图表支持**：提供图表插入与自动编号功能，支持单图和子图。
- **数学公式**：集成常用数学宏包，搭配`unicode-math`，支持复杂公式的排版。
- **参考文献管理**：基于 `biblatex` 宏包，支持 GB/T 7714-2015 国家标准的文献引用格式。
- **结构清晰**：封面、摘要、目录、正文和附录等部分自动生成，无需担心格式问题。

## 使用说明

- 对主源文件`main.tex`按照`xelatex->biber->xelatex->xelatex`的顺序编译得到输出 PDF 文档`main.pdf`。
- 建议在中文 Windows 操作系统（默认安装了模板所需的中文字体：宋体、黑体和楷体）与较新的 TEXLive 本地发行版环境下，在 Visual Studio Code 中搭配 LaTeX Workshop 扩展使用。
- 详细使用方法和配置说明，请参考 [README.pdf](README.pdf)。

## 联系方式

如有问题或建议，请通过以下渠道联系：

- 作者邮箱：zhukangwang1005@gmail.com
- 项目主页：[GitHub - sduthesis](https://github.com/wangzhukang/sduthesis)
