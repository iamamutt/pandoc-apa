# pandoc-apa

A Sublime Text build system / Visual Studio Code task runner for writing APA manuscripts with pandoc markdown

# Installation

## Pandoc

You need Pandoc to use the pandoc templates. You can find it here: <http://www.pandoc.org/>

## LaTex / Word

You'll need a LaTeX distribution to build the pdf files (e.g., MikTex or MacTex), or Microsoft Word to build .docx files.

## Filters

Pandoc doesn't yet support cross referencing figures and tables. You'll need a Python distribution to install two filters to be able to do this. The filters are `pandoc-fignos` and `pandoc-tablenos`. You can find links and installation instructions here <https://github.com/tomduck/pandoc-fignos>

# Usage

## Sublime Text

Just copy the `pandoc` and `sublime` directories from this repository wherever your Packages folder is located in Sublime Text. For example, if the contents are not already in a folder called `pandoc-apa`, make a folder called `pandoc-apa` and copy contents here if on Windows: `C:\Users\username\AppData\Roaming\Sublime Text 3\Packages\User\pandoc-apa`.

- Press `ctrl + b` to build to pdf (or `cmd+b`)

- Press `ctrl + shift + b` to build to docx (or `cmd+shift+b`)

- You can also go to `Tools > Build System > Pandoc APA`, then if you select `Tools > Build Width` you can see the different options. Default is .pdf. `Markdown to LaTeX` will convert a pandoc markdown document to a .tex file. `Run` will convert to .docx.

- In a document, type `apayaml`, then press Tab. It will generate a YAML header. Or you can do this from `Tools > Snippets > "Insert Pandoc ..."`

## Visual Studio Code


Copy the `.vscode` and `pandoc` directories to where your main markdown file is located. 
Open the folder containing your markdown file as a vscode workspace. 
Press `Ctrl+Shift+B` to run the build task or press `F1` then type `task`, select "run task", then choose one of the Pandoc options.


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
