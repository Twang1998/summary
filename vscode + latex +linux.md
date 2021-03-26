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

得到$ f_3(d) = \mathop{max}\limits_{x_3}(2x_3 + f_4(d-x_3)) $ 得到

~~~latex
% subfigure
% \begin{figure}[!t]
% \centering
% \subfigure[输入信号]{
% \includegraphics[width=0.45\textwidth]{figures/linkwgn.pdf}
% %\caption{fig1}
% }
% \quad
% \subfigure[2阶AR模型输出信号]{
% \includegraphics[width=0.45\textwidth]{figures/linkAR.pdf}
% }
% \quad
% \subfigure[逆系统恢复信号]{
% \includegraphics[width=0.45\textwidth]{figures/linkinverse.pdf}
% }

% \caption{Simulink仿真结果}
% \label{fig:simall}
% \end{figure}


% subfig
% \begin{figure}[]
% 	\centering
% 	\subfloat[Arabic numerals]{\label{fig:a}\includegraphics[width=0.45\textwidth]{linkwgn.pdf}}\quad
% 	\subfloat[Arabic numerals]{\label{fig:b}\includegraphics[width=0.45\textwidth]{linkwgn.pdf}}\\	
	
% 	\subfloat[Arabic numerals]{\label{fig:b}\includegraphics[width=0.45\textwidth]{linkwgn.pdf}}\\
% 	\caption{Capital Roman numerals.}
% 	\label{fig}
% \end{figure}


% subcaption
\begin{figure}[t]
    \centering
    \begin{subfigure}[*]{0.45\textwidth}
        \includegraphics[width=\textwidth]{linkwgn.pdf}
        \subcaption{输入信号}       %可以决定caption位置是上是下。
      
        \label{fig:subfig1}
    \end{subfigure}%
    \quad
    \begin{subfigure}[]{0.45\textwidth}
    \includegraphics[width=\textwidth]{linkAR.pdf}
        \subcaption{2阶AR模型输出信号}
        \label{fig:subfig2}
    \end{subfigure}
 
    \begin{subfigure}[]{0.45\textwidth}
    \includegraphics[width=\textwidth]{figures/linkinverse.pdf}
        \subcaption{逆系统恢复信号}
        % \rule{\linewidth}{3cm}
        \label{fig:subfig3}
    \end{subfigure}
    \caption{Simulink仿真结果}
    \label{fig:simall}
\end{figure}
~~~



