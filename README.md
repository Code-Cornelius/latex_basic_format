# Latex basic format

This repository sums up the template for using latex. One can copy the file article (or book), which lies in the
directory `paper`  and the directory `config`, and then write inside the template `.tex` file in order to get an already
configured latex file!

The configuration can be found inside the `config` folder, and the names of the files should not be changed. 
The dependency is such that a
minimal working example would require to have such directory tree:

```
Project
├── Config
│  └── the required config files. A rule of thumb is to simply copy the config file.
├── Project
│   └── project.tex
├── images_schools
└── page_de_garde.tex
```

With a bibliography, the minimal working example looks like:

```
Project
├── Config
│  └── the required config files. A rule of thumb is to simply copy the config file.
├── Project
│   ├── bibliographie
│   │  └── biblio.bib
│   └── project.tex
├── images_schools
└── page_de_garde.tex
```

In example, one can find some older projects where some pieces are interesting to understand how to use certain
libraries.

Respect the structure of the project as some imports needs to be updated if the directories' organisation is changed.

# Difference Article / Book

Book are "book" style, while article are "amsart" style. In the latter, there is neither "part" nor "chapter", as well as
no presentation page. Both support biblatex. In order to compile correctly the document, it should be compiled a few
times and with the additional BibTeX reading if using it.

## Two Columns article

use `\documentclass[10pt, twocolumn]{article}`, instead of `\documentclass[10pt]{article}`, in the article template.

## Authors name

use 

`\author{ LastName1, FirstName1\\ \texttt{first1.last1@xxxxx.com} \and LastName2, FirstName2\\ \texttt{first2.last2@xxxxx.com} }`

# Type Paper: a report or publication type?

`explain_abstract` and `acknowledgement` environment defined inside `configuration.tex`. The environment is called
`explain_abstract` and not abstract because abstract already exists. In order to have a more colourful presentation, though
it is not the classical formatting for publication, it is possible to set the variable

`\ColorfulFormattrue`

which is set by default to `false`, corresponding to a more classical style. In that situation, one can also
write: `\ColorfulFormatfalse`.

Before importing the configuration files, the line should be added at the top of the `.tex`.

    \ColorfulFormattrue % Setting the state of the boolean variable \ifReportFormat` to true, 
    % otherwise it's false already. Or you could write %\ColorfulFormatfalse

### ColorfulFormattrue

Then, in `config_font.tex` and `config_boxes.tex`, the environment is changed to put a specific formatting. In
particular, if the formatting is set to `true`, the following environments are defined:

    \begin{definition}[my def]
    \end{definition}
    
    \begin{theoreme}[label = thrm:X]{my theo} 
    \end{theoreme}
    
    \begin{demo}{}{} 
    \end{demo}
    
    \begin{ajoutationV}{}{} 
    \end{ajoutationV}

If one wants to disable such formatting, just replace the variable with:  `\ColorfulFormatfalse`.

The formatting is undergone inside `config_font` and inside `config_boxes`.

### ColorfulFormatfalse

When the variable is set to `false`, the following more classical definitions are made:

    \numberwithin{equation}{section}
    \newtheorem{theorem}{Theorem}[section]
    \newtheorem{corollary}[theorem]{Corollary}
    \newtheorem{lemma}[theorem]{Lemma}
    \newtheorem{proposition}[theorem]{Proposition}
    \newtheorem{conjecture}[theorem]{Conjecture}
    
    \theoremstyle{definition}
    \newtheorem{definition}[theorem]{Definition}
    \newtheorem{remark}[theorem]{Remark}
    \newtheorem{assumption}[theorem]{Assumption}

## Appendix

In order to have an appendix, use `\appendix`. 

In the case of articles, there is an issue of compatibility between the
package: `\usepackage[Rejne]{fncychap}` imported in configuration and having no chapter defined. The package modifies how chapters are displayed.
In the case of articles, the command chapter does not exist. 
The issue arises when the package is formatting the appendix as a chapter even though the latter does not exist for articles.
However, the bug only arises when one uses the `appendix` command.

The solution in the case of articles is to comment the usage of the package.

If you still want to use appendices with articles, you would need to comment the package `fncychap`'s import directly. Then, it works like a charm.

## Bibliography

Inside the special config file for bibliography, one can select the sorting. Traditionally, one uses the `nty`but no
sorting (numbering wrt order of appearance)
is useful in order to know if all references are used inside the text.
