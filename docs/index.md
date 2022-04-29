# Sphinx 快速使用

参考文档：[Sphinx 官方指南](https://www.sphinx-doc.org/en/master/index.html)

## 入门

- 在 VS code 中打开终端，使用 conda 为编写文档创建新环境。

``` 
conda create -n writing python=3.10
conda activate writing 
```

```
pip install sphinx
```

- 一般来讲，我们会创建并在 `/docs` 目录下去编写文档。
   
```
cd docs && sphinx-quikstart
```
   

使用 `sphinx-quikstar` 命令可以快速在文件夹内为项目创建基本目录和配置布局所需的一系列 docs，并按照提示输入信息：

```
   > 独立的源文件和构建目录（y/n)[n]: 
   > 项目名称:
   > 作者名称: 
   > 项目发行版本 []:
   > 项目语种 [en]: zh_CN
```


    此时，`/docs` 目录下将产生新的文件及文件夹：

    - `build/` ：一个空目录，将保存渲染的文档。
    - `make.bat` 和 `Makefile` ：方便脚本来简化一些常见的 Sphinx 操作，例如渲染内容。
    - `source/conf.py`：包含 Sphinx 项目配置的 Python 脚本。它包含您指定的项目名称和版本sphinx-quickstart，以及一些额外的配置键。
    - `source/index.rst`：项目的根文档，作为欢迎页面，包含“目录树”（或toctree）的根。
  
- 终端中输入以下命令来渲染文档，得到的 html 文件将保存在 `/build` 文件夹下：
   
```
   make html
```

   例图：
   ![](https://www.sphinx-doc.org/en/master/_images/lumache-first-light.png)

## 自定义设定

### 使用自定义主题

主题是自定义文档外观的一种方式。Sphinx 有几个[内置主题](https://www.sphinx-doc.org/en/master/usage/theming.html#builtin-themes)，也有[第三方](https://sphinx-themes.org/)的。

例如，要在 HTML 文档中使用Furo第三方主题，首先需要安装它，如下所示：

```
pip install furo
```

在 `docs/source/conf.py` 中修改主题：

```
# The theme to use for HTML and HTML Help pages.  See the documentation for
# a list of builtin themes.
#
html_theme = 'furo'
```

### Markdown

- 安装 Markdown 解析器MyST-Parser：
   
```
   pip install --upgrade myst-parser
```

- 将myst_parser添加到 list of configured extensions（``docs/source/conf.py`` 中)：
   
```
   extensions = ['myst_parser']
```

- 调整 source_suffix 变量，将 Sphinx 配置为解析所有带有扩展名 .md 和 .txtMarkdown 的文件：

```
   source_suffix = {
    '.rst': 'restructuredtext',
    '.txt': 'markdown',
    '.md': 'markdown',
   }
```

   