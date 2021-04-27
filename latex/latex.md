# vscode + latex +linux

## 1.安装xelatex

```shell
sudo apt-get install texlive-science
```

## 2.安装工具

```shell
sudo apt-get install texlive-science
```

## 3.安装插件

vscode

latex workshop

## 4.设置setting.json

左下角 齿轮->setting

选择workshop 然后edit json

```json
{
    "latex-workshop.latex.recipes": [{
    "name": "xelatex",
    "tools": [
        "xelatex"
    ]
  }, {
    "name": "latexmk",
    "tools": [
        "latexmk"
    ]
  },
  
  {
    "name": "pdflatex -> bibtex -> pdflatex*2",
    "tools": [
        "pdflatex",
        "bibtex",
        "pdflatex",
        "pdflatex"
    ]
  }
  ],
  "latex-workshop.latex.tools": [{
  "name": "latexmk",
  "command": "latexmk",
  "args": [
    "-synctex=1",
    "-interaction=nonstopmode",
    "-file-line-error",
    "-pdf",
    "%DOC%"
  ]
  }, {
  "name": "xelatex",
  "command": "xelatex",
  "args": [
    "-synctex=1",
    "-interaction=nonstopmode",
    "-file-line-error",
    "%DOC%"
  ]
  }, {
  "name": "pdflatex",
  "command": "pdflatex",
  "args": [
    "-synctex=1",
    "-interaction=nonstopmode",
    "-file-line-error",
    "%DOC%"
  ]
  }, {
  "name": "bibtex",
  "command": "bibtex",
  "args": [
    "%DOCFILE%"
  ]
  }],
  "latex-workshop.view.pdf.viewer": "tab",
  "latex-workshop.latex.clean.fileTypes": [
  "*.aux",
  "*.bbl",
  "*.blg",
  "*.idx",
  "*.ind",
  "*.lof",
  "*.lot",
  "*.out",
  "*.toc",
  "*.acn",
  "*.acr",
  "*.alg",
  "*.glg",
  "*.glo",
  "*.gls",
  "*.ist",
  "*.fls",
  "*.log",
  "*.fdb_latexmk"
  ],
}

```

## 5.编译预览

Recipe:pdflatex -> bibtex -> pdflatex*2 

都在tex插件选项卡



### 6. 笔记

~~~
\usepackage{amsthm,amsmath,amssymb}

\usepackage{mathrsfs}

$\mathbb{R}$

$\mathcal{R}$

$\mathscr{R}$
%大写的字母
~~~

~~~
但是有时我们需要上/下标出现在一段非数学符号的正上/下方，如本文开头的需求，这时应该怎么办呢？

解决方法是用\mathop{expr1}命令将expr1转化成数学符号，写成

\mathop{expr1}\limits_{expr2}^{expr3}
这样就可以使用\limits命令了，例如命令

$f_3(d) = \mathop{max}\limits_{x_3}(2x_3 + f_4(d-x_3))$

~~~

得到$ f_3(d) = \mathop{max}\limits_{x_3}(2x_3 + f_4(d-x_3)) $ 

