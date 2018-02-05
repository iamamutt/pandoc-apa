---
# This is a comment, you may remove fields that you don't use. Not all options are shown below. See `README.md`.
mode:                         # enter only one of three document types, defaults to
    doc: true                 #   man:, jou:, or doc:
title: Writing an APA manuscript from Pandoc markdown
subtitle: APA from markdown
author:                       # author list, each item is a group of authors
    - Author 1, Author 2      # these go with institute 1
    - Author 3                # these go with institute 2
institute:                    # institute list
    - Institute 1             # for Authors 1 and 2
    - Institute 2             # for Author 3
twogroups: true               # since authors span two universities, using twogroups
                              #   other fields: threegroups, ..., sixgroups
bibliography:
    - references.bib          # delete bibliography field if not citing
date: "Last updated: \\today" # data is optional, can delete if not needed
keywords:                     # enter as many keywords as needed
    - sublime text
    - vscode
    - pandoc
    - apa6
authornote: |                 # author notes (optional) are multiline text
    \noindent Correspondence:

    Joseph M. Burling

    Department of Psychology

    6538 Franz Hall, UCLA

    Los Angeles, CA 90095-1563

    Email: jmburling@ucla.edu
abstract: |                   # abstract text on next few lines, always indented.
    This is just an example of using pandoc (with the help of some build systems) to write in pandoc's markdown syntax for APA manuscripts.
    The output will be rendered in APA 6 format according to some commands and class options provided by the LaTeX `apa6` package.
    I also make use of a few pandoc filters downloaded as python modules to get cross-referencing to work.
    Lastly, I provide a .DOCX version of the build system, though a lot may not translate and will require some additional tweaking.
---



# Quick pandoc overview

Words go here, also here is a citation [@someArticle]. According to @anotherArticle, something bad happened. See Figure @fig:myplot. This is a bold statement... **WOW!**, and here's _some _emphasis for you_ too. Sometimes you need some typewrite-like font, like when writing code: `my_answer = 1 + 1`. Other types you may need to write blocks of code, like this:

```{latex}
\begin{table}
\centering
\begin{tabular}{|l|l|}\hline
Age & Frequency \\ \hline
18--25  & 15 \\
26--35  & 33 \\
36--45  & 22 \\ \hline
\end{tabular}
\end{table}
```


![Your figure caption goes here.](plot.png "A title"){#fig:myplot height=3.333in width=3.333in}


See Table {@tbl:mytable} for an example on making tables using the default extension. In APA man mode, Tables are sent to the end of the document unless the following is used in the YAML header at the top of this document:

```{yaml}
classoption:
    - floatsintext
```


 Right Left  Default  Center
------ ----- ------- --------
12     12    12      12
123    123   123     123
1      1     1       1

Table: A table. {#tbl:mytable}

<!-- This is a comment -->

- This is another type of pandoc table (@tbl:anotherone). It should look the same.[^1]

| Right | Left | Default | Center |
|------:|:-----|---------|:------:|
|   12  |  12  |    12   |    12  |
|  123  |  123 |   123   |   123  |
|    1  |    1 |     1   |     1  |

Table: Another one {#tbl:anotherone}

[^1]: Sometimes docx files will have tables that are squished. Autofit the document width to fix.

<!--
This is
another
comment
-->

\newpage

+---------------+---------------+--------------------+
| Fruit         | Price         | Advantages         |
+===============+===============+====================+
| Bananas       | $1.34         | - built-in wrapper |
|               |               | - bright color     |
+---------------+---------------+--------------------+
| Oranges       | $2.10         | - cures scurvy     |
|               |               | - tasty            |
+---------------+---------------+--------------------+

Table: And another multi-line table which is more complicated to make. It may requires a pagebreak in two-column (jou) mode because pandoc uses `longtable` which doesn't work in two-column mode.Some additional latex hacks are added to the template to allow it to work (at the risk of losing content or bleeding off the page. Blame pandoc for using `longtable`).

- Here's some raw latex code. It won't be recognized unless the output is LaTeX/pdf and you have to proper parse-raw option set. It's the same LaTeX code block from above rendered as an actual Table \ref{tbl:rawtex}. The position may shift because it's a floating environment.

\begin{table}
\centering
\caption{Using raw latex code}
\label{tbl:rawtex}
\begin{tabular}{|l|l|}\hline
Age & Frequency \\ \hline
18--25  & 15 \\
26--35  & 33 \\
36--45  & 22 \\ \hline
\end{tabular}
\end{table}

- Here's an example of inline LaTeX math, $p=.0499$.

- Here's a an example of using LaTeX syntax for displaying equations.

$$
\hat{y} = \beta_0 + \beta_1 x
$$

Pandoc doesn't know how to make inline headings when converting to Word. If you put the cursor at the end of the heading, press Ctrl+Alt+Enter and it will move it down.

## Subsection heading

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue sapien turpis et justo. Suspendisse potenti.

Duis viverra aliquet metus, eget aliquam tellus mollis imperdiet. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec egestas sit amet, convallis a felis.

### Subsubsection heading

Nullam nec est ut mauris eleifend pulvinar ac in nisl. In eleifend, velit et rhoncus pretium, justo lectus viverra enim, nec feugiat ante mauris vitae magna. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi felis nulla, iaculis dapibus sapien quis, pretium laoreet est. Mauris vel sapien tempor, dapibus ipsum sit amet, sagittis tellus. Aliquam ipsum metus, ultricies eleifend dolor nec, ultricies mollis sapien. Integer placerat ante condimentum sagittis elementum. Fusce aliquam, libero a iaculis eleifend, ipsum ante tincidunt ante, ut bibendum dolor risus ut nibh. Sed fermentum tellus id ligula sodales, ut condimentum tortor tempus. Phasellus suscipit dapibus est sed consectetur.

Nullam nec est ut mauris eleifend pulvinar ac in nisl. In eleifend, velit et rhoncus pretium, justo lectus viverra enim, nec feugiat ante mauris vitae magna. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi felis nulla, iaculis dapibus sapien quis, pretium laoreet est. Mauris vel sapien tempor, dapibus ipsum sit amet, sagittis tellus. Aliquam ipsum metus, ultricies eleifend dolor nec, ultricies mollis sapien. Integer placerat ante condimentum sagittis elementum. Fusce aliquam, libero a iaculis eleifend, ipsum ante tincidunt ante, ut bibendum dolor risus ut nibh. Sed fermentum tellus id ligula sodales, ut condimentum tortor tempus. Phasellus suscipit dapibus est sed consectetur.

#### Paragraph heading

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at molestie lectus felis ut nunc.
Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue sapien turpis et justo. Suspendisse potenti. Duis viverra aliquet metus, eget aliquam tellus mollis imperdiet.

##### Subparagraph heading

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at molestie lectus felis ut nunc.
Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue sapien turpis et justo. Suspendisse potenti. Duis viverra aliquet metus, eget aliquam tellus mollis imperdiet.

###### Getting silly with the amount of subheadings

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue sapien turpis et justo. Suspendisse potenti. Duis viverra aliquet metus, eget aliquam tellus mollis imperdiet.

Nullam nec est ut mauris eleifend pulvinar ac in nisl. In eleifend, velit et rhoncus pretium, justo lectus viverra enim, nec feugiat ante mauris vitae magna. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi felis nulla, iaculis dapibus sapien quis, pretium laoreet est. Mauris vel sapien tempor, dapibus ipsum sit amet, sagittis tellus. Aliquam ipsum metus, ultricies eleifend dolor nec, ultricies mollis sapien. Integer placerat ante condimentum sagittis elementum. Fusce aliquam, libero a iaculis eleifend, ipsum ante tincidunt ante, ut bibendum dolor risus ut nibh. Sed fermentum tellus id ligula sodales, ut condimentum tortor tempus. Phasellus suscipit dapibus est sed consectetur.

####### Heading 7

Lorem ipsum dolor sit amet, consectetur adipiscing elit.

######## Heading 8

Lorem ipsum dolor sit amet, consectetur adipiscing elit.

\newpage

# References
