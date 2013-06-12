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
\usepackage{listings}
\usepackage{linehighlight}
```
3. Define some listing, like::
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

Screenshot of highlighting:

.. image:: http://github.com/tobyS/qalisting/raw/master/screenshot.png
   :alt:   Screenshot of qalisting highlighted lines.
