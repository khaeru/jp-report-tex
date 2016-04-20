MIT Joint Program on the Science &amp; Policy of Global Change — LaTeX package
==============================================================================

This repository contains the following key files:

- `jp-report.sty` — a LaTeX package.
- `jpreport.bst` — a BibTeX style file.
- `jp-report.module` — a LyX module.

Together, these allow the formatting a document according to the Style Guide for the [report series][1] of the [MIT Joint Program on the Science & Policy of Global Change][2] ("Joint Program," or "JP"). Since academic journals often require manuscripts in LaTeX format, using this package can obviate the need to reformat an entire paper in a word processor like Microsoft Word.

> Note: Although the LaTeX code in these templates has been assembled from publicly-available snippets and is likewise publicly available, *only* documents published on the JP website or MIT DSpace are official Joint Program Reports.

The repository also contains:

- `template/`
  - `figure/` — graphics files.
  - `references.bib` — bibliography entries, in [BibTeX][3] format.
  - `template-12.pdf` — a reference document, from version 1.2 of the package.
  - `tex/template.tex` — template for a LaTeX document, containing some documentation of how to format various parts of the document to meet the style requirements.
  - `lyx/template.lyx` — template for a LyX document, with the same contents.
- `jp-report-12.sty` — version 1.2 of the LaTeX style file.

Joint Program researchers preparing reports should consult the full instructions on the ["Report Series Info"][4] page (MIT certificates required) of the JP wiki.


Installation
------------
The package and other files must be installed where they can be located by LyX, `latex`, `pdflatex`, `bibtex` and other programs which transform LyX/LaTeX documents into output (usually a PDF document). Because the files have different roles, each must be installed in a distinct location.

To get a copy of the files, clone this Github repository, or use the *Download ZIP* link in the right sidebar.


### jp-report.sty
This LaTeX package contains code to load other LaTeX packages and change the document appearance to match the style guide.

On Linux or Mac OS, install the package in the directories indicated by the environment variables `$TEXINPUTS` or `$TEXMFHOME/tex/latex/`. Typical values are:
- Linux: `~/texmf/latex/`
- Mac OS: `~/Library/texmf/latex/`
- Windows: **TODO**

To locate these directories:
- On the command line, run `kpsepath tex`; or
- Within LyX, use the menu item *Tools → TeX Information*, select *LaTeX styles* from the drop-down menu, and toggle the checkbox labelled *Show path*. If the file is correctly installed, it should appear in this list after the "Rescan" button is clicked.


### jpreport.bst
This BibTeX style file causes bibliography entries to be formatted according to the JP Report style guide.

On Linux or Mac OS, install the package in the directory indicated by the environment variable `$BIBINPUTS`. Typical values are:
- Linux: `~/texmf/bibtex/bst/`
- Mac OS: `~/Library/texmf/bibtex/bst/`
- Windows: **TODO**

To locate this directory:
- On the command line, run `kpsepath bst`; or
- Within LyX, use the same &TeX Information* dialog indicated above, but select *BibTeX styles* from the drop-down menu.


### jp-report.module
This LyX module, when loaded for a LyX document, causes `jp-report.sty` to be applied to that document. Install it in the LyX *user directory*, the location of which is documented [on the LyX Wiki][5].

Basic usage
-----

Refer to the template files for more complete examples.

### LaTeX
The style files are invoked with following LaTeX code in the document preamble:

```
% Note: the document class option '12pt' is required to set the font size
\documentclass[12pt]{article}
\usepackage{jp-report}
\begin{document}
…
```

### LyX

Load the module:
- *Document → Settings… → Modules*
- Choose "MIT Joint Program report" and click "Add".

### Bibliographies using BibTeX & `natbib`

In LaTeX, pass the option `natbib` to the `jp-report` package:
```
\usepackage[natbib]{jp-report}
```
Then, select the `jpreport` BibTeX style before including BibTeX entries:
```
\bibliographystyle{jpreport}
\bibliography{bibfile}
```

In LyX, enter "jpreport" into the *Style* entry of the dialog box when inserting a bibliography.

### Bibliographies using BibLaTeX

In LaTeX, pass the option `biblatex` to the `jp-report` package:
```
\usepackage[biblatex]{jp-report}
```

### Producing pre-preprints

Pre-print versions of JP Reports are provided in the sponsors-only area of the JP website. These contain watermarks reading "DRAFT: Please do not cite, quote or distribute" across the top and bottom, and "DRAFT" in the middle, of every page.

In LaTeX, pass the option `preprint` to the `jp-report` package:
```
\usepackage[preprint]{jp-report}
```

Caveats
-------
Issues sometimes encountered when using these style files (or LaTeX generally) are listed here, for convenience.

### Incorrect table of contents entries for sections
**Symptom:** If a new ((sub)sub)section begins at the start of a new page, and there is a figure at the bottom of the preceding page, the page number for the section in the table of contents is incorrect.

**Fix:** Insert a `\clearpage` (LyX: *Insert → Formatting → Clear Page*) command before the new section.

### Unexpected figure placement
**Symptom:** Figures appear in unexpected places.

**Fix:** Read [this section of the LaTeX Wikibook][6] to understand the built-in LaTeX rules that determining the placement of "floats" (the `figure` environment is one kind of float) and the use of *placement specifiers*.

One technique for getting the desired output is:

1. *Remove all placement specifiers*. In LaTeX, replace e.g. `\begin{figure}[h!tp]` with `\begin{figure}`. In LyX: *Document → Settings… → Float Placement → Use default placement*—and for each `float: Figure` block: *\[Right click\] → Settings… → Use default placement*. This step makes it easier to understand the effect of changes in the following two steps.
2. *Move* the actual figure codes to different locations in the text, roughly before or after the paragraphs where you wish the figures to appear.
3. *Add placement specifiers*, only where necessary, to fine-tune the location of figures in the output.

Bugs
---
See the [issue tracker on Github](https://github.com/mit-jp/jp-report-tex/issues).

Authors
-------
- Erwan Monier <<emonier@MIT.EDU>>
- Paul Natsuo Kishimoto <<pnk@MIT.EDU>>
- Qudsia Ejaz <<ejazqj@MIT.EDU>>

[1]: http://globalchange.mit.edu
[2]: http://globalchange.mit.edu/research/publications/reports/all
[3]: http://en.wikibooks.org/wiki/LaTeX/Bibliography_Management#BibTeX
[4]: https://wikis.mit.edu/confluence/display/globalchange/Report+Series
[5]: http://wiki.lyx.org/LyX/UserDir
[6]: http://en.wikibooks.org/wiki/LaTeX/Floats,_Figures_and_Captions#Floats
