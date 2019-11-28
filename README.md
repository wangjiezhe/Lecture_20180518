# Lecture for video course on May 18, 2018

- Class: ctexbeamer
- Theme: Madrid
- Colortheme: whale
- Fonttheme: professionalfonts

## 一些笔记

### 调整页面比例

```tex
\documentclass[UTF8,aspectratio=169]{ctexbeamer}
```

### 插入特殊数学符号

使用 `mathtools` 包（会自动加载 `amsmath` 包）：

```tex
\usepackage{mathtools}
```

### 插入方程组

使用 `dcases` 环境：

```tex
\begin{dcases}
...
\end{dcases}
```

### 插入特殊符号

```tex
\usepackage{pifont}
```

插入符号：

```tex
\ding{33}
\ding{254}
```

具体符号的代码可以查看 [Pifont][pifont]。

### 切换句号和句点

```tex
\catcode`。=\active
\def。{．}
```

### 定义新环境

```tex
\newenvironment<>{question}[1][]{
    \begin{exampleblock}#2{问题}}{\end{exampleblock}}
\newenvironment<>{answer}[1][]{
    \begin{alertblock}#2{答案}}{\end{alertblock}}
```

可选择的 block

- block (蓝色)
- exampleblock (绿色)
- alertblock (红色)

### 插入图片

使用 `subfigure` 包：

```tex
\graphicspath{{fig/}}
\usepackage{subfigure}
```

> 官网显示，`subfigure` 已废弃，建议使用 `subfig` 或者 `subcaption`。

插入图片：

```tex
\includegraphics[width=\textwidth]{3.jpg}
```

### 绘制箭头

插入 `tikz` 包：

```tex
\usepackage{tikz}
\newcommand\tikzmark[1]{
        \tikz[overlay,remember picture] \node[coordinate] (#1) {};
}
```

标记箭头的起始点：

```tex
\tikzmark{1 start}
...
\tikzmark{1 end}
```

显示箭头：

```tex
\begin{tikzpicture}[overlay, remember picture]
    \draw[thick, blue,->] (1 start) to [bend left](1 end);
\end{tikzpicture}
```

箭头带文字：

```tex
\begin{tikzpicture}[overlay, remember picture]
    \draw[thick, blue, <-] (2 start) -- node[below]{?:8/??} (2 end);
\end{tikzpicture}
```

### 重点显示

使用 `alert` 环境：

```tex
\alert{20}
```

[pifont]: https://freeze.sh/_/2016/pifont/
