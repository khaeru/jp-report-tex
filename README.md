MIT Joint Program on the Science &amp; Policy of Global Change — LaTeX package
==============================================================================

This repository contains the following key files:

- `jp-report.sty` — a LaTeX style file
- `jpreport.bst` — a BibTeX style file
- `jp-report.module` — a LyX module

Together, these allow the formatting a document according to the Style Guideline for the
[report series][1] of the
[MIT Joint Program on the Science & Policy of Global Change][2].

> Note: Although the LaTeX code in these templates has been assembled from publicly-available snippets and is likewise publicly available, *only* PDF documents downloaded from the Joint Program website are official JP Reports.

It also contains:

- `template/`
  - `figure/` — graphics files
  - `references.bib` — bibliography entries, in [BibTeX][3] format.
  - `template-12.pdf` — a reference document, from version 1.2 of the package
  - `tex/template.tex` — template for a LaTeX document, containing some documentation of how to format various parts of the document to meet the 
  - `lyx/template.lyx` — template for a LyX document, with the same contents
- `jp-report-12.sty` — version 1.2 of the LaTeX style file

Installation
------------
Use of the style files and modules requires that they be correctly installed, so
they can be located by LyX, `latex`, `pdflatex`, `bibtex` and other programs
which transform LyX/LaTeX documents into output (usually a PDF document). Because
the files have different roles, each must be installed in a distinct location.

To get a copy of the files, clone this Github repository, or use the *Download ZIP* link in the right sidebar.


### jp-report.sty
This LaTeX style file contains TeX and LaTeX code that loads packages and
changes the document appearance to match the JP Report style guide.

On Linux or Mac OS, the directories indicated by the environment variables
`$TEXINPUTS` or `$TEXMFHOME/tex/latex/` may be used.

To locate these directories from within LyX, it may be helpful to use the menu
item *Tools > TeX Information*, select "LaTeX styles" from the drop-down menu,
and toggle the checkbox labelled *Show path*. If the file is correctly
installed, it should appear in this list after the "Rescan" button is clicked.

From the command line, the command
```kpsepath tex```
will provide similar information.

Typical values are:
* Linux: `~/texmf/latex/`
* Mac OS: `~/Library/texmf/latex/`
* Windows: **TODO**


### jpreport.bst
This BibTeX style file causes bibliography entries to be formatted according to
the JP Report style guide.

On Linux or Mac OS, the directory indicated by the environment variable
`$BIBINPUTS` may be used. To locate a directory from within LyX, use the same
"TeX Information" dialog indicated above, but select "BibTeX styles" from the
drop-down menu. From the command line, use the command ```kpsepath bst```.

Typical values are:
* Linux: `~/texmf/bibtex/bst/`
* Mac OS: `~/Library/texmf/bibtex/bst/`
* Windows: **TODO**


### jp-report.module
This LyX module, when loaded for a LyX document, causes `jp-report.sty` to be
applied to that document.

It should be placed in the LyX *user directory*, the location of which is
documented [on the LyX Wiki][4].

LaTeX usage
-----------
The style files are invoked with following LaTeX code in the document preamble:

```
\documentclass[12pt,fleqn]{article}
\usepackage{jp-report}
\begin{document}
…
```
The options to the `article` document class are necessary to give the proper font size ("12pt") and for displayed equations to be left-aligned ("fleqn").

Before including BibTeX entries from a file such as `bibfile.bib`, the following command invokes the JP Report BibTeX style:
```
\bibliographystyle{jpreport}
\bibliography{bibfile}
```

Refer to `template/tex/template.tex` for a complete example.


LyX usage
---------
Some requirements of the JP Report style are met by loading the module:

- *Document → Settings… → Modules*
- Choose "MIT Joint Program report" and click "Add".

When inserting a BibTeX Bibliography into a LyX document, enter "jpreport" into the *Style* entry of the dialog box.

Refer to `template/lyx/template.lyx` for a complete example.

Caveats
-------
Issues sometimes encountered when using these style files are listed here, for convenience.

### Incorrect table of contents entries for sections
**Symptom:** If a new ((sub)sub)section begins at the start of a new page, and there is a figure at the bottom of the preceding page, the page number for the section in the table of contents is incorrect.

**Fix:** Insert a `\clearpage` (LyX: *Insert → Formatting → Clear Page*) command before the new section. 

TODOs
-----
- Document paths for Windows users.
- Enhance `jp-report.module` to obviate more manual settings in LyX.
- Contents of the documents in `template` are slightly misleading, because they refer to version 1.2 of this template. Update.

Authors
-------
- Erwan Monier <<emonier@MIT.EDU>>
- Paul Natsuo Kishimoto <<pnk@MIT.EDU>>

[1]: http://globalchange.mit.edu
[2]: http://globalchange.mit.edu/research/publications/reports/all
[3]: http://en.wikibooks.org/wiki/LaTeX/Bibliography_Management#BibTeX
[4]: http://wiki.lyx.org/LyX/UserDir
