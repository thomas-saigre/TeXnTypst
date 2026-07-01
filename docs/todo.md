---
icon: lucide/list-todo
---

Equivalent of [`todonotes`](https://ctan.org/pkg/todonotes), using [`drafting`](https://typst.app/universe/package/drafting).


### Package to load, and preamble

=== "LaTeX"

    ```tex
    \usepackage[colorinlistoftodos,prependcaption,textsize=small]{todonotes}
    \usepackage{regexpatch}
    \makeatletter
    \xpatchcmd{\@todo}{\setkeys{todonotes}{#1}}{\setkeys{todonotes}{inline,#1}}{}{}
    \makeatother

    \newcommand{\mycomment}[1]{%
        {%
        \todo[color=blue,size=\small]{%
        #1}%
        }
    }
    ```

=== "Typst"

    ```typst
    #import "@preview/drafting:0.2.2": *

    #let todo = inline-note.with(stroke:red)
    #let mycomment = inline-note.with(stroke: rgb("#5941D1"))
    ```

### Display the list of to-dos

=== "LaTeX"

    ```tex
    \listoftodos
    ```


=== "Typst"

    ```typst
    #note-outline(level: 2)     // the level is for table of content
    ```


### Add a to-do, or a comment

=== "LaTeX"
    ```tex
    \todo{Item}
    \mycomment{Fix this}
    ```

=== "Typst"
    ```typst
    #todo[Item]
    #mycomment[Fix this]
    ```
