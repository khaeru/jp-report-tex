MIT Joint Program on the Science &amp; Policy of Global Change — LaTeX style
============================================================================

This repository contains:
* `jp-report.sty` — a LaTeX style file
* `jpreport.bst` — a BibTeX style file
* `jp-report.module` — a LyX module

Together, these allow the formatting of a report in the style of the
[report series][1] of the
[MIT Joint Program on the Science & Policy of Global Change][2].

[1]: globalchange.mit.edu
[2]: globalchange.mit.edu/research/publications/reports/all


Installation
------------
Use of the style files and modules requires that they be correctly installed, so
they can be located by LyX, `latex`, `pdflatex`, `bibtex` and other programs
which transform LyX/LaTeX source into output (usually a PDF document). Because
the files have different roles, each must be installed in a distinct location.


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

It should be placed in the LyX user directory, the location of which is
documented [on the LyX Wiki][3].

[3]: http://wiki.lyx.org/LyX/UserDir


Usage
-----
Some requirements of the JP Report style are met by loading the module:
* *Document → Settings… → Modules*
* Choose "MIT Joint Program report" and click "Add".

In addition: **TODO**


TODOs
-----
* Document paths for Windows users.
* Document additional required steps to apply the style.
* Enhance `jp-report.module` to obviate the manual settings under "Usage".


Authors
-------
Erwan Monier <emonier@MIT.EDU>

Paul Natsuo Kishimoto <pnk@MIT.EDU>
