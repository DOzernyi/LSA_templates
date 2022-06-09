---
layout: default
---

## Compiling on Overleaf

1. Go to the page for LSA templates on Overleaf (here, that is; links to external website).
1. Choose the template you need (<em>ELM, PLSA, PDA</em>).
1. Choose _Open as Template_.
1. If Overleaf prompts you to log in (i.e., if you don't have an account), register or log in in whichever way is convenient.
1. Write your paper and make sure you have the proper .bib file.
1. Click _compile_ in the top menu.
1. Fix errors, if need be; and make sure the bibliography as well as the rest of the paper compiles properly.
1. Download .pdf using either the main menu in top left corner, or the pdf download option next to compile button.
1. Submit your .pdf to _PLSA_ website.  

## Compiling on desktop (mostly for those familiar with LaTeX)

Compiling on desktop is not really a good option unless you already have the requisite software installed and use LaTeX frequently. If the latter is the case, then there's nothing new to be told here. Overleaf is indeed strongly suggested for beginners; whether because TeXLive can take 12 hours to install, or because there's no space here to go over different editors, each of which requires individual approach. _Atom_, which I use, might not fit someone, and packages for _Atom_ trivially are no use for _Vim_, etc. So, start with Overleaf which is very straightforward.

The templates which are in the repo were compiled in _Atom_ (mainly) with _Atom_LaTeX_ package. The templates are far from perfect, this is especially true for the .bib files, where a lot of tweaking took place. Hopefully .bst will be updated at some point in the future to fit all the requirements. Pretty much in every case, .bib that was not created by hand (as it shouldn't be), but is output of some bibliography management system (e.g., Zotero) will need to be cleaned.

This is one of the reasons log files are included in the repo in each folder (PLSA and PDA). Logs contain more information about what's wrong with the templates, e.g.:

```
// from PDA_main.log, 725-725
LaTeX Font Info: Font shape 'OT1/phv/m/it' in size <9> not available
(Font)           Font shape 'OT1/phv/m/sl' tried instead on input line 206.
```

or

```
// from PLSA_template.blg, 46
warning$ -- 2
```

To the same effect, all the overfull and underfull are listed if you really want to fix them:

```
// from PLSA_template.log, 590-593
Underfull \hbox (badness 10000) in paragraph at lines 90--90
          [][][]\OT1/ptm/m/n/10 Both ac-knowl-edg-ments and au-thor af-fil-i-a-tion in-f
          or-ma-tion go in an ini-tial foot-note like...
```

> **Note** that in the GitHub repo, there is a file **PDA_preamble.tex** that happens to be empty. In the Overleaf template, it isn't empty. However, some local compilers have personal issues with **\include[path]**, so what was in the preamble on Overleaf is in root file locally. The empty preamble file was left just not to create an impression a file is missing -- and to use for those whose local compilers aren't misbehaved.

GitHub repo also contains .zip-s of the Overleaf sources, should that be of interest.

[back](./)
