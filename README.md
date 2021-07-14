# latex basic format

This repository sums up the template for using latex. 
One can copy the file article (or book) and config, 
and then write inside the template `.tex` file in order to get an already configured latex file!

The configuration can be found inside config folder, and the names should not be changed.
The dependency is such that a minimal working example would require to have such directory tree:

```
Project
├── Config
│  └── the required config files
├── Project
│   └── project.tex
├── images_schools
└── page_de_garde.tex
```

In example, one can find some older projects where some pieces are interesting to understand how to use certain libraries.








# Difference Article / Book

There is no bibliography in article's template.
It is the only difference; in `config_book.tex`, compared to `config_article.tex`, there is this additional line:

    \input{../config/config_biblio}



# Type Paper: a report or publication type?
Since I like using colors in my report, which is not the classical formatting for publication, 
I have a set a variable that defines the behavior of configuration.

At the top of `configuration.tex`, one finds the line:

`\ReportFormattrue`

this defines the variable `\ReportFormat` as `true`. Then, in `config_font.tex` and `config_boxes.tex`, the environment is changed to put a specific formatting.
In particular, if the formatting is set to `true`, the particular following environments are defined:

    \begin{definition}[my def]
    \end{definition}
    
    \begin{theoreme}[label = thrm:X]{my theo} 
    \end{theoreme}
    
    \begin{demo}{}{} 
    \end{demo}
    
    \begin{ajoutationV}{}{} 
    \end{ajoutationV}
    
If one wants to disable such formatting, just replace the variable by:  `\ReportFormatfalse`




