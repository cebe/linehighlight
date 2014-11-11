linehighlight
=============

linehighlight - code line highlighting for LaTeX lstlisting (in beamer)

This package allows you to highlight lines in a source code listing.
It is mostly used in beamer presentations, to point to certain code
potions. The provided environment allows you to embed a listing and to define
highlighted lines in a simple and clean way, without messing up your LaTeX
code, the source code example and especially without loosing lstlisting
source highlighting.

> Note: This currently does not work with listings that have a caption.
> Also all the paddings and spacings of lstlisting will be set to 0.

To use this package, do the following:

1. Download the `linehighlight.sty` file to your LaTeX project.
2. Include the package using:

```latex
% allow using color 
\usepackage{color}
\usepackage{xcolor}

% the lstlistings package
\usepackage{listings}
% highlighting lines in listings
\usepackage{linehighlight}

% set colors for code background and highlighting
\definecolor{codehighlight}{rgb}{0.95,0.8,0.8}
\definecolor{codebackground}{rgb}{0.95,0.95,0.95}

```

Define a listing, like this:

```latex
\begin{linehighlight}{
      \only<1,3>{ % Only on slides 1 and 3 (beamer stuff)
            \highline{1,3,5} % highlight code lines 1,3 and 5.
      }
      \only<2>{ % Only on slide 2 (beamer)
            \highline{2,...,8} % highlight lines 2 to 8.
      }
}
      % put your \lstinputlisting{} or \begin{lstlisting}...\end{lstlisting} here
\end{linehighlight}
```

Thanks to [@tobyS](https://github.com/tobyS) for the initial version and idea.

Screenshot of highlighting:

![Screenshot of qalisting highlighted lines.](http://github.com/cebe/linehighlight/raw/master/screenshot.png)

Usage with normal text or math
------------------------------

The line highlighting also works with normal text or math and pseudo code.
Currently only a little hack has to be applied here to make the alignment work.
Add a `\vspace{.05cm}` after the linehighlight environment.

```latex
 \begin{linehighlight}{
       \only<2>{\highline{2}}
       % ...
}%
\vspace{.05cm}
    $ k \leftarrow 0 $ \\
    $ G_k \leftarrow G $ \\
\end{linehighligh
```

### Force indentation

The linehighlight environment seems to remove all indentation that you may have in you algorithm or code.
Prepending the lines with a `\hspace*{0.5cm}` can bring it back:

```latex
$ k \leftarrow 0 $ \\
$ G_k \leftarrow G $ \\
$ \textbf{while } |G_k| > 0 \textbf{ do} $ \\
\hspace*{0.5cm} $ \textbf{while } \{n \in G_k : k > |deg(n)|\} \neq \emptyset \textbf{ do} $ \\
\hspace*{1.0cm} $    G_k \leftarrow G_k \setminus \{n \in G_k : k > |deg(n)|\} $ \\
\hspace*{0.5cm} $ \textbf{end while} $ \\
\hspace*{0.5cm} $ G_{k+1} \leftarrow G_k $ \\
\hspace*{0.5cm} $ k \leftarrow k + 1 $ \\
$ \textbf{end while} $%
```

