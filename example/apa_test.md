
---
# This is a comment, you may delete them and/or delete fields that you don't use
mode:                         # enter only one of three document types, defaults to man:
    doc: true                 # man:, jou:, or doc:
joucommands:                  # this field and subfields can be removed if not using jou
    leftheader:               # see apa6.pdf for details
    journal:
    volume:
    ccoppy:
    copnum:
title: Writing an APA manuscript from Pandoc markdown
subtitle: APA from markdown
author:                       # author list, each item is a group of authors
    - Author 1, Author 2      # these go with institute 1
    - Author 3                # these go with institute 2
institute:                    # institute list
    - Institute 1             # for Authors 1 and 2
    - Institute 2             # for Author 3
twogroups: true               # authors span two universities, other fields: threegroups, ..., sixgroups
bibliography: references.bib  # delete field if not using references!!!
date: "Last updated: \\today" # optional, can delete if not needed
keywords:                     # enter as many keywords as needed
    - sublime text
    - pandoc
    - apa6
authornote: |                 # author notes are multiline text (optional)
    \noindent Correspondence:

    Joseph M. Burling

    Department of Psychology

    6538 Franz Hall, UCLA

    Los Angeles, CA 90095-1563

    Email: jmburling@ucla.edu
abstract: |                   # abstract text on next few lines, always indented.
    This is just an example of using pandoc (with the help of sublime text build systems) to write in pandoc's markdown syntax for APA manuscripts.
    The output will be rendered in APA 6 format according to some commands and class options provided by the LaTeX `apa6` package.
    I also make use of a few pandoc filters downloaded as python modules to get cross-referencing to work.
    Lastly, I provide a .DOCX version of the build system, though a lot may not translate and will require some additional tweaking.
---

# Installation

## Pandoc

You need Pandoc to use the pandoc templates. You can find it here: <http://www.pandoc.org/>

## LaTex / Word

You'll need a LaTeX distribution to build the pdf files (e.g., MikTex or MacTex), or Microsoft Word to build only .docx files.

## Filters

Pandoc doesn't yet support cross referencing figures and tables. You'll need a Python distribution to install two filters to be able to do this. The filters are `pandoc-fignos` and `pandoc-tablenos`. You can find links and installation instructions here <https://github.com/tomduck/pandoc-fignos>

## APA Template

Just copy all the contents of this repository wherever your Packages folder is located in Sublime Text. For example, if the contents are not already in a folder called `pandoc-apa`, make a folder called `pandoc-apa` and copy contents here if on Windows: `C:\Users\username\AppData\Roaming\Sublime Text 3\Packages\User\pandoc-apa`. You should see this README.md, `.sublime-build` file, and others directly in `pandoc-apa`.

# Usage

## Sublime Text Usage

- Press `ctrl + b` to build to pdf (or `cmd+b`)

- Press `ctrl + shift + b` to build to docx (or `cmd+shift+b`)

- You can also go to `Tools > Build System > Pandoc APA`, then if you select `Tools > Build Width` you can see the different options. Default is .pdf. `Markdown to LaTeX` will convert a pandoc markdown document to a .tex file. `Run` will convert to .docx.

- In a document, type `apayaml`, then press Tab. It will generate a YAML header. Or you can do this from `Tools > Snippets > "Insert Pandoc ..."`


## Pandoc YAML Metadata Block

These templates makes heavy use of the pandoc metadata block at the beginning of your document. I've also provided a snippet you can use to insert the metadata and fill in what is needed (Tools > Snippets). Most of the commands used in the `apa6` package are fields that can be used in the YAML header. See documentation for more details: <https://www.ctan.org/pkg/apa6?lang=en>. Fields used in this template are:

- `mode`
    - Set to `man: true`, `doc: true`, or `jou: true`
- `classoption`
    - A list of options that the `apa6` package will understand. See manual. Don't use `jou`, `man`, or `doc` options here. Use the dedicated YAML field `mode` instead. If the field isn't used, it defaults to manuscript mode. Also the `longtable` option is already specified since it's necessary for pandoc to work with tables. Don't put it twice.
- `title`
    - Main title of the document. Consistent with the pandoc variable.
- `subtitle`
    - Running head title. Consistent with the pandoc variable.
- `author`
    - List of authors. Put multiple authors on one line to group by affiliation. Consistent with the pandoc variable.
- `institute`
    - List of affiliations. Won't work with docx. You have to add it manually.
- `twogroups`, `threegroups`, ... , `sixgroups`
    - Set one of these to true if grouping authors by different affiliations, as in the twogroup YAML example. If anyone of these options are not set, it will use the standard `\author{}` command.
- `authornote`
    - A note that will be placed at the bottom of the title page, or footnote if in `jou` mode.
- `bibliography`
    - Location of your bibtex references file, whatever pandoc-citeproc will read. Can add multiple fields for multiple files.
- `date`
    - Place anything typed here as you would in the `\note{}` apa6 latex command.
- `joucommands` (optional).
    - If you are in journal mode and want to use the other journal commands as seen in the example YAML header, add them here. See apa6 manual for list of commands.
- `keywords`
    - List of keywords that will show under the abstract. See YAML metadata example.
- `abstract`
    - The abstract text of the manuscript.


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


![Your figure caption goes here.](plot.png "A title"){#fig:myplot width=3in}


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

###### Getting silly with the amount of subheadings.

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue sapien turpis et justo. Suspendisse potenti. Duis viverra aliquet metus, eget aliquam tellus mollis imperdiet.

Nullam nec est ut mauris eleifend pulvinar ac in nisl. In eleifend, velit et rhoncus pretium, justo lectus viverra enim, nec feugiat ante mauris vitae magna. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi felis nulla, iaculis dapibus sapien quis, pretium laoreet est. Mauris vel sapien tempor, dapibus ipsum sit amet, sagittis tellus. Aliquam ipsum metus, ultricies eleifend dolor nec, ultricies mollis sapien. Integer placerat ante condimentum sagittis elementum. Fusce aliquam, libero a iaculis eleifend, ipsum ante tincidunt ante, ut bibendum dolor risus ut nibh. Sed fermentum tellus id ligula sodales, ut condimentum tortor tempus. Phasellus suscipit dapibus est sed consectetur.

\newpage

# References
