Quick pandoc overview
=====================

::: {custom-style="First Paragraph"}
The YAML metadata block is at the top of the document and take on key-value pairs like so:
:::

::: {custom-style="Source Code"}
    ---
    # string field with other characters should be quoted
    title: "Some specials: Characters in the title?!?"

    # toggle values
    twogroups: true

    # nested fields with text
    joucommands:
        leftheader: some ascii text
        journal: other text

    # lists
    bibliography:
        - references.bib
        - other_references.bib

    # multiline text
    abstract: |
        lines go here
        and here.
    ---
:::

::: {custom-style="First Paragraph"}
Words go here, also here is a citation (Lastname & Someone, 2016). According to Burling (2016),
something bad happened. See Figure [[1]{custom-style="Hyperlink"}](#fig:myplot). This is a bold
statement... **WOW!**, and here's \_some *emphasis for you* too. Sometimes you need some
typewriter-like font, like when writing code: `my_answer = 1 + 1`. Other types you may need to
write blocks of code, like this:
:::

::: {custom-style="Source Code"}
    \begin{table}
    \centering
    \begin{tabular}{|l|l|}\hline
    Age & Frequency \\ \hline
    18--25  & 15 \\
    26--35  & 33 \\
    36--45  & 22 \\ \hline
    \end{tabular}
    \end{table}
:::

::: {custom-style="Captioned Figure"}
[]{#fig:myplot .anchor}![Figure 1: Your figure caption goes
here.](C:\Users\Joseph\Dropbox\appdata\pandoc\pandoc-apa\example\media\docx\media\rId20.png){width="3.33299978127734in"
height="3.33299978127734in"}
:::

::: {custom-style="Image Caption"}
Figure 1: Your figure caption goes here.
:::

::: {custom-style="Body Text"}
See Table [[1]{custom-style="Hyperlink"}](#tbl:mytable) for an example on making tables using the
default extension. If tables are not referenced, then they are not given table numbers and
arranged with other tables. In APA man mode, Tables are sent to the end of the document unless the
following is used in the YAML header at the top of this document:
:::

::: {custom-style="Source Code"}
    floatsintext: true
:::

::: {custom-style="Table Caption"}
Table 1: A table.
:::

  Right   Left   Default   Center
  ------- ------ --------- --------
  12      12     12        12
  123     123    123       123
  1       1      1         1

  : Table 1: A table.

-   This is another type of pandoc table ([[2]{custom-style="Hyperlink"}](#tbl:anotherone)). It
    should look the same.[^1]

::: {custom-style="Table Caption"}
Table 2: Another one
:::

  Right   Left   Default   Center
  ------- ------ --------- --------
  12      12     12        12
  123     123    123       123
  1       1      1         1

  : Table 2: Another one

::: {custom-style="Table Caption"}
And another multi-line table which is more complicated to make. It may require a pagebreak in
two-column (jou) mode because pandoc uses `longtable` which doesn't work in two-column mode. It
has no reference so it doesn't start with "Table x." Some additional latex hacks are added to the
template to allow it to work (at the risk of losing content or bleeding off the page. Blame pandoc
for using `longtable`).
:::

+---------+--------+----------------------+
| Fruit   | Price  | Advantages           |
+=========+========+======================+
| Bananas | \$1.34 | -   built-in wrapper |
|         |        | -   bright color     |
+---------+--------+----------------------+
| Oranges | \$2.10 | -   cures scurvy     |
|         |        | -   tasty            |
+---------+--------+----------------------+

: And another multi-line table which is more complicated to make. It may require a pagebreak in
two-column (jou) mode because pandoc uses longtable which doesn't work in two-column mode. It has
no reference so it doesn't start with "Table x." Some additional latex hacks are added to the
template to allow it to work (at the risk of losing content or bleeding off the page. Blame pandoc
for using longtable).

::: {custom-style="First Paragraph"}
Here's some raw latex code. It won't be recognized unless the output is LaTeX/pdf and you have to
proper parse-raw option set. It's the same LaTeX code block from above rendered as an actual Table
. The position may shift because it's a floating environment.
:::

::: {custom-style="Body Text"}
Checking rendering of Table [[3]{custom-style="Hyperlink"}](#tbl:tbllong).
:::

::: {custom-style="Table Caption"}
Table 3: Testing a longtable.
:::

  id    sess      cond   rep       trial      age         demographic   gender   maturation
  ----- --------- ------ --------- ---------- ----------- ------------- -------- ------------
  S01   -0.1706   -B     -0.2317   -0.3189    -0.004132   1.103         -m       -pre
  S01   -0.1706   -A     -0.2317   -0.2226    -0.004132   1.103         -m       -pre
  S01   -0.1706   -C     -0.2317   -0.1262    -0.004132   1.103         -m       -pre
  S01   -0.1706   -C     0.061     -0.02987   -0.004132   1.103         -m       -pre
  S01   -0.1706   -A     0.061     0.06647    -0.004132   1.103         -m       -pre
  S01   -0.1706   -A     0.3537    0.1628     -0.004132   1.103         -m       -pre
  S01   -0.1706   -C     0.3537    0.2591     -0.004132   1.103         -m       -pre
  S01   -0.1706   -B     0.061     0.3555     -0.004132   1.103         -m       -pre
  S01   -0.1706   -B     0.3537    0.4518     -0.004132   1.103         -m       -pre
  S01   -0.1706   -C     0.6463    0.5482     -0.004132   1.103         -m       -pre
  S01   -0.1706   -C     0.939     0.6445     -0.004132   1.103         -m       -pre
  S01   -0.1706   -B     0.6463    0.7409     -0.004132   1.103         -m       -pre
  S01   -0.1706   -A     0.6463    0.8372     -0.004132   1.103         -m       -pre
  S01   -0.1706   -B     0.939     0.9335     -0.004132   1.103         -m       -pre
  S01   -0.1706   -B     1.232     1.03       -0.004132   1.103         -m       -pre
  S01   -0.1706   -A     0.939     1.126      -0.004132   1.103         -m       -pre
  S01   -0.1706   -A     1.232     1.223      -0.004132   1.103         -m       -pre
  S01   -0.1706   -C     1.232     1.319      -0.004132   1.103         -m       -pre
  S02   -0.1706   -B     -0.2317   -0.3189    0.01387     0.2929        -m       -pre
  S02   -0.1706   -A     -0.2317   -0.2226    0.01387     0.2929        -m       -pre
  S02   -0.1706   -C     -0.2317   -0.1262    0.01387     0.2929        -m       -pre
  S02   -0.1706   -A     0.061     -0.02987   0.01387     0.2929        -m       -pre
  S02   -0.1706   -A     0.3537    0.06647    0.01387     0.2929        -m       -pre
  S02   -0.1706   -C     0.061     0.1628     0.01387     0.2929        -m       -pre
  S02   -0.1706   -C     0.3537    0.2591     0.01387     0.2929        -m       -pre
  S02   -0.1706   -A     0.6463    0.3555     0.01387     0.2929        -m       -pre
  S02   -0.1706   -B     0.061     0.4518     0.01387     0.2929        -m       -pre
  S02   -0.1706   -B     0.3537    0.5482     0.01387     0.2929        -m       -pre
  S02   -0.1706   -B     0.6463    0.6445     0.01387     0.2929        -m       -pre
  S02   -0.1706   -A     0.939     0.7409     0.01387     0.2929        -m       -pre
  S02   -0.1706   -A     1.232     0.8372     0.01387     0.2929        -m       -pre
  S02   -0.1706   -C     0.6463    0.9335     0.01387     0.2929        -m       -pre
  S02   -0.1706   -C     0.939     1.03       0.01387     0.2929        -m       -pre
  S02   -0.1706   -B     0.939     1.126      0.01387     0.2929        -m       -pre
  S02   -0.1706   -C     1.232     1.223      0.01387     0.2929        -m       -pre
  S02   -0.1706   -B     1.232     1.319      0.01387     0.2929        -m       -pre
  S03   -0.1706   -A     -0.2317   -0.3189    -0.2321     1.464         -m       -pre
  S03   -0.1706   -B     -0.2317   -0.2226    -0.2321     1.464         -m       -pre
  S03   -0.1706   -A     0.061     -0.1262    -0.2321     1.464         -m       -pre
  S03   -0.1706   -C     -0.2317   -0.02987   -0.2321     1.464         -m       -pre
  S03   -0.1706   -B     0.061     0.06647    -0.2321     1.464         -m       -pre
  S03   -0.1706   -A     0.3537    0.1628     -0.2321     1.464         -m       -pre
  S03   -0.1706   -A     0.6463    0.2591     -0.2321     1.464         -m       -pre
  S03   -0.1706   -B     0.3537    0.3555     -0.2321     1.464         -m       -pre
  S03   -0.1706   -C     0.061     0.4518     -0.2321     1.464         -m       -pre
  S03   -0.1706   -C     0.3537    0.5482     -0.2321     1.464         -m       -pre
  S03   -0.1706   -A     0.939     0.6445     -0.2321     1.464         -m       -pre
  S03   -0.1706   -C     0.6463    0.7409     -0.2321     1.464         -m       -pre
  S03   -0.1706   -B     0.6463    0.8372     -0.2321     1.464         -m       -pre
  S03   -0.1706   -C     0.939     0.9335     -0.2321     1.464         -m       -pre

  : Table 3: Testing a longtable.

-   Here's an example of inline LaTeX math, $p = .0499$.

-   Here's a an example of using LaTeX syntax for displaying equations.

$$\widehat{y} = \beta_{0} + \beta_{1}x$$

::: {custom-style="First Paragraph"}
Pandoc doesn't know how to make inline headings when converting to Word. If you put the cursor at
the end of the heading, press Ctrl+Alt+Enter and it will move it down.
:::

Subsection heading
------------------

::: {custom-style="First Paragraph"}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue
eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut
lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem
libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur
diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis
molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue
sapien turpis et justo. Suspendisse potenti.
:::

::: {custom-style="Body Text"}
Duis viverra aliquet metus, eget aliquam tellus mollis imperdiet. Lorem ipsum dolor sit amet,
consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum
venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper,
consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at
molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec
egestas sit amet, convallis a felis.
:::

### Subsubsection heading

::: {custom-style="First Paragraph"}
Nullam nec est ut mauris eleifend pulvinar ac in nisl. In eleifend, velit et rhoncus pretium,
justo lectus viverra enim, nec feugiat ante mauris vitae magna. Lorem ipsum dolor sit amet,
consectetur adipiscing elit. Morbi felis nulla, iaculis dapibus sapien quis, pretium laoreet est.
Mauris vel sapien tempor, dapibus ipsum sit amet, sagittis tellus. Aliquam ipsum metus, ultricies
eleifend dolor nec, ultricies mollis sapien. Integer placerat ante condimentum sagittis elementum.
Fusce aliquam, libero a iaculis eleifend, ipsum ante tincidunt ante, ut bibendum dolor risus ut
nibh. Sed fermentum tellus id ligula sodales, ut condimentum tortor tempus. Phasellus suscipit
dapibus est sed consectetur.
:::

::: {custom-style="Body Text"}
Nullam nec est ut mauris eleifend pulvinar ac in nisl. In eleifend, velit et rhoncus pretium,
justo lectus viverra enim, nec feugiat ante mauris vitae magna. Lorem ipsum dolor sit amet,
consectetur adipiscing elit. Morbi felis nulla, iaculis dapibus sapien quis, pretium laoreet est.
Mauris vel sapien tempor, dapibus ipsum sit amet, sagittis tellus. Aliquam ipsum metus, ultricies
eleifend dolor nec, ultricies mollis sapien. Integer placerat ante condimentum sagittis elementum.
Fusce aliquam, libero a iaculis eleifend, ipsum ante tincidunt ante, ut bibendum dolor risus ut
nibh. Sed fermentum tellus id ligula sodales, ut condimentum tortor tempus. Phasellus suscipit
dapibus est sed consectetur.
:::

#### Paragraph heading

::: {custom-style="First Paragraph"}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue
eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut
lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem
libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur
diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis
molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue
sapien turpis et justo. Suspendisse potenti. Duis viverra aliquet metus, eget aliquam tellus
mollis imperdiet.
:::

##### Subparagraph heading

::: {custom-style="First Paragraph"}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue
eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut
lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem
libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur
diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis
molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue
sapien turpis et justo. Suspendisse potenti. Duis viverra aliquet metus, eget aliquam tellus
mollis imperdiet.
:::

###### Getting silly with the amount of subheadings

::: {custom-style="First Paragraph"}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue
eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut
lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem
libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur
diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis
molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue
sapien turpis et justo. Suspendisse potenti. Duis viverra aliquet metus, eget aliquam tellus
mollis imperdiet.
:::

::: {custom-style="Body Text"}
Nullam nec est ut mauris eleifend pulvinar ac in nisl. In eleifend, velit et rhoncus pretium,
justo lectus viverra enim, nec feugiat ante mauris vitae magna. Lorem ipsum dolor sit amet,
consectetur adipiscing elit. Morbi felis nulla, iaculis dapibus sapien quis, pretium laoreet est.
Mauris vel sapien tempor, dapibus ipsum sit amet, sagittis tellus. Aliquam ipsum metus, ultricies
eleifend dolor nec, ultricies mollis sapien. Integer placerat ante condimentum sagittis elementum.
Fusce aliquam, libero a iaculis eleifend, ipsum ante tincidunt ante, ut bibendum dolor risus ut
nibh. Sed fermentum tellus id ligula sodales, ut condimentum tortor tempus. Phasellus suscipit
dapibus est sed consectetur.
:::

####### Heading 7

::: {custom-style="First Paragraph"}
Lorem ipsum dolor sit amet, consectetur adipiscing elit.
:::

######## Heading 8

::: {custom-style="First Paragraph"}
Lorem ipsum dolor sit amet, consectetur adipiscing elit.
:::

References
==========

::: {custom-style="Bibliography"}
Burling, J. M. (2016). Hi: A title about stuff. *Bottom Tier*, *1*, 1--2.
[[https://doi.org/10.1016/j.cogdev.2013.10.001]{custom-style="Hyperlink"}](https://doi.org/10.1016/j.cogdev.2013.10.001)
:::

::: {custom-style="Bibliography"}
Lastname, F., & Someone, E. (2016). Article title. *Journal Name*, *1*, 1--50.
:::

[^1]: ::: {custom-style="footnote text"}
    []{custom-style="footnote reference"} Sometimes docx files will have tables that are squished.
    Autofit the document width to fix.
    :::
