#latex首行无缩进
* 局部设置 \noident
* 全局设置 \usepackage{parskip}
* 换行 \medskip 不只是单倍行距

#输入中文
* Document-->Document Setting-->format
* 选择utf8编码
* \document[UTF8]{article}
* \usepackage{CJK}
* \begin{CJK}{UTF8}{song}....\end{UTF8}

#加入背景色
* \usepackage{color}
* \definecolor{shadecolor}{rgb}{0.92,0.92,0.92}
* \begin{shaded}...\end{shaded}

#公式大括号
\\[P(X=x)=

   \begin{pmatrix}

            x-1 \\

            r-1

   \end{pmatrix}

\\]

#多行公式对齐
* \usepackage{amsmath}
* \\[

	\begin{aligned}

	.....

	\end{aligned}

	\\]
#写伪代码

* \usepackage{algorithm}
* \usepackage{algorithmicx}
* \usepackage{algpseudocode}
* \begin{algorithm}
* \begin{algorithmic}
   .....
  \end{algorithmic}
* \end{algorithm}





 
