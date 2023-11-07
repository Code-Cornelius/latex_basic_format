Add these lines:

```latex 
%%%%%%%%%%%%%%% Specifically to add the UCL Banner. Requires the existence of the file `UCL_Banner.png`
\usepackage{eso-pic}
\makeatletter
% Rewrite the command maketitle, but it includes the same content as the original one apart from the added (marked) part.
\def\@maketitle{
    \newpage
    \null
%%%%%% Added
    \AddToShipoutPictureBG*{
        \AtPageUpperLeft{
            \raisebox{-\height}{\hspace*{-0.24cm} \includegraphics[width=\paperwidth]{UCL_Banner.png}}
        }
    }
    \vspace{3 cm}
%%%%%%
    \vskip 2em
    \begin{center}
        \let \footnote \thanks
        {\LARGE \@title \par}
        \vskip 1.5em
            {\large
        \lineskip .5em
        \begin{tabular}[t]{c}
            \@author
        \end{tabular}\par}
        \vskip 1em
            {\large \@date}
    \end{center}
    \par
    \vskip 1.5em}
\makeatother
%%%%%%%%%%%%%%%
```