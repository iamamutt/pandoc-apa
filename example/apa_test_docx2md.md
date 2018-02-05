Quick pandoc overview
=====================

Words go here, also here is a citation (Lastname & Someone, 2016). According to Burling (2016), something bad happened. See Figure [1](#fig:myplot). This is a bold statement... **WOW!**, and here's \_some *emphasis for you* too. Sometimes you need some typewrite-like font, like when writing code: `my_answer = 1 + 1`. Other types you may need to write blocks of code, like this:

    \begin{table}
    \centering
    \begin{tabular}{|l|l|}\hline
    Age & Frequency \\ \hline
    18--25  & 15 \\
    26--35  & 33 \\
    36--45  & 22 \\ \hline
    \end{tabular}
    \end{table}

[]{#fig:myplot .anchor}

![Figure 1: Your figure caption goes here.](media/rId22.png "A title"){width="3.33299978127734in" height="3.33299978127734in"}

Figure 1: Your figure caption goes here.

See Table [1](#tbl:mytable) for an example on making tables using the default extension. In APA man mode, Tables are sent to the end of the document unless the following is used in the YAML header at the top of this document:

    classoption:
        - floatsintext

[]{#tbl:mytable .anchor}

Table 1: A table.

  Right   Left   Default   Center
  ------- ------ --------- --------
  12      12     12        12
  123     123    123       123
  1       1      1         1

  : Table 1: A table.

-   This is another type of pandoc table ([2](#tbl:anotherone)). It should look the same.[^1]

[]{#tbl:anotherone .anchor}

Table 2: Another one

  Right   Left   Default   Center
  ------- ------ --------- --------
  12      12     12        12
  123     123    123       123
  1       1      1         1

  : Table 2: Another one

And another multi-line table which is more complicated to make. It may requires a pagebreak in two-column (jou) mode because pandoc uses `longtable` which doesn't work in two-column mode.Some additional latex hacks are added to the template to allow it to work (at the risk of losing content or bleeding off the page. Blame pandoc for using `longtable`).

  -----------------------------------------
  Fruit     Price    Advantages
  --------- -------- ----------------------
  Bananas   \$1.34   -   built-in wrapper
                     
                     -   bright color
                     

  Oranges   \$2.10   -   cures scurvy
                     
                     -   tasty
                     
  -----------------------------------------

  : And another multi-line table which is more complicated to make. It may requires a pagebreak in two-column (jou) mode because pandoc uses longtable which doesn't work in two-column mode.Some additional latex hacks are added to the template to allow it to work (at the risk of losing content or bleeding off the page. Blame pandoc for using longtable).

-   Here's some raw latex code. It won't be recognized unless the output is LaTeX/pdf and you have to proper parse-raw option set. It's the same LaTeX code block from above rendered as an actual Table . The position may shift because it's a floating environment.

<!-- -->

-   Here's an example of inline LaTeX math, $p = .0499$.

-   Here's a an example of using LaTeX syntax for displaying equations.

$$\hat{y} = \beta_{0} + \beta_{1}x$$

Pandoc doesn't know how to make inline headings when converting to Word. If you put the cursor at the end of the heading, press Ctrl+Alt+Enter and it will move it down.

Subsection heading
------------------

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue sapien turpis et justo. Suspendisse potenti.

Duis viverra aliquet metus, eget aliquam tellus mollis imperdiet. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec egestas sit amet, convallis a felis.

### Subsubsection heading

Nullam nec est ut mauris eleifend pulvinar ac in nisl. In eleifend, velit et rhoncus pretium, justo lectus viverra enim, nec feugiat ante mauris vitae magna. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi felis nulla, iaculis dapibus sapien quis, pretium laoreet est. Mauris vel sapien tempor, dapibus ipsum sit amet, sagittis tellus. Aliquam ipsum metus, ultricies eleifend dolor nec, ultricies mollis sapien. Integer placerat ante condimentum sagittis elementum. Fusce aliquam, libero a iaculis eleifend, ipsum ante tincidunt ante, ut bibendum dolor risus ut nibh. Sed fermentum tellus id ligula sodales, ut condimentum tortor tempus. Phasellus suscipit dapibus est sed consectetur.

Nullam nec est ut mauris eleifend pulvinar ac in nisl. In eleifend, velit et rhoncus pretium, justo lectus viverra enim, nec feugiat ante mauris vitae magna. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi felis nulla, iaculis dapibus sapien quis, pretium laoreet est. Mauris vel sapien tempor, dapibus ipsum sit amet, sagittis tellus. Aliquam ipsum metus, ultricies eleifend dolor nec, ultricies mollis sapien. Integer placerat ante condimentum sagittis elementum. Fusce aliquam, libero a iaculis eleifend, ipsum ante tincidunt ante, ut bibendum dolor risus ut nibh. Sed fermentum tellus id ligula sodales, ut condimentum tortor tempus. Phasellus suscipit dapibus est sed consectetur.

#### Paragraph heading

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue sapien turpis et justo. Suspendisse potenti. Duis viverra aliquet metus, eget aliquam tellus mollis imperdiet.

##### Subparagraph heading

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue sapien turpis et justo. Suspendisse potenti. Duis viverra aliquet metus, eget aliquam tellus mollis imperdiet.

###### Getting silly with the amount of subheadings

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et magna vitae ipsum rhoncus congue eu vehicula sem. Vestibulum venenatis mauris ac urna porta placerat. Ut ante neque, malesuada ut lobortis ullamcorper, consectetur vitae ipsum. Morbi sodales, justo eu pretium venenatis, sem libero dapibus sem, at molestie lectus felis ut nunc. Praesent ultrices sagittis porta. Curabitur diam elit, lacinia nec egestas sit amet, convallis a felis. Praesent dictum nec mauris quis molestie. Proin ullamcorper, mauris sed molestie aliquet, nisi sapien tempor risus, quis congue sapien turpis et justo. Suspendisse potenti. Duis viverra aliquet metus, eget aliquam tellus mollis imperdiet.

Nullam nec est ut mauris eleifend pulvinar ac in nisl. In eleifend, velit et rhoncus pretium, justo lectus viverra enim, nec feugiat ante mauris vitae magna. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi felis nulla, iaculis dapibus sapien quis, pretium laoreet est. Mauris vel sapien tempor, dapibus ipsum sit amet, sagittis tellus. Aliquam ipsum metus, ultricies eleifend dolor nec, ultricies mollis sapien. Integer placerat ante condimentum sagittis elementum. Fusce aliquam, libero a iaculis eleifend, ipsum ante tincidunt ante, ut bibendum dolor risus ut nibh. Sed fermentum tellus id ligula sodales, ut condimentum tortor tempus. Phasellus suscipit dapibus est sed consectetur.

####### Heading 7

Lorem ipsum dolor sit amet, consectetur adipiscing elit.

######## Heading 8

Lorem ipsum dolor sit amet, consectetur adipiscing elit.

References
==========

Burling, J. M. (2016). Hi: A title about stuff. *Bottom Tier*, *1*, 1–2. <https://doi.org/10.1016/j.cogdev.2013.10.001>

Lastname, F., & Someone, E. (2016). Article title. *Journal Name*, *1*, 1–50.

[^1]: Sometimes docx files will have tables that are squished. Autofit the document width to fix.
