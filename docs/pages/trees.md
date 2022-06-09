---
layout: default
---

## Trees

### Don't use qtree.

Qtree takes more space, has fewer options and is generally a tad more clumsy. It's a personal choice, but for the sake of style and space, forest is more advisable.

### Instead, use forest.

Forest ([here](https://ctan.org/pkg/forest?lang=en), links to CTAN) is very flexible. So that you don't have to read the documentation (which you should), here's a sample tree:

* * *
#### Disclaimer: do not copy the examples below directly, the comments separated by // below will not be recognized as such in LaTeX. LaTeX uses % for comments. Delete the comments, load the packages in the preamble and then use the examples.
* * *

```tex
% a simple forest tree; Java coloring actually works nice here; requires \usepackage[linguistics]{forest}
\begin{forest}
sn edges
[S [NP [N [Matthew]]] [VP [V [kissed]] [NP [N [John]]] ]]
\end{forest}
```

The parameter _sn edges_ sets, trivially, edges, to a conventionally linguistic format. Include it with every tree right after the _begin_ bit. Somewhat more involved examples will include combining forest with _expex_ and _multicols_ in order to get a numbered example that has _a._ and _b._ parts to it, and those parts are next to each other. An example would be this:

```tex
% a more involved tree; requires \usepackage[linguistics]{forest}, \usepackage{multicols}, \usepackage{expex}
\pex
% this \pex bit is from expex; it starts a numered example; the parts of the example will be given by \a..\a..\a..
\begin{multicols}{2}
% trivially, this is multicols; {2} at the end indicates the number of columns you need -- {2} is the default setting if you forget to specify; but LaTeX will likely be grumpy and throw something like "Missing number, treated as zero" at you
% \scriptsize
% trees can get large, like these X-bar ones, so descreasing font size with \scriptsize, \footnotesize, \tiny, etc. can be useful
\a Tree 1
\begin{forest}
sn edges
[S [NP\\Mary] [S' [S\\is] [VP [V\\thinking] [CP [C\\that] [S [NP\\John] [S' [S\\is] [VP [V\\reading] [NP [D\\the] [N\\book]]]]]]]]]
% note "\\" between, e.g. NP and Mary; in the previous example [NP [Mary]] would create a line going from NP to Mary; but since this was pretty much abandoned for the reasons Carnie explains in "Constituent Structure", "\\" just creates a line break
\end{forest}
\columnbreak
%\scriptsize
\a Tree 2
\begin{forest}
sn edges
[S [NP\\Mary-ga] [S' [VP [CP [S [NP\\John-ga] [S' [VP [NP\\ hon-o] [V\\yom-]] [S\\ -da]]] [C\\-to]] [V\\omotte-]] [S\\ -iru]]]
\end{forest}
\end{multicols}
\xe
```

If you need arrows to and fro, _tikz_ can be effectively combined with _forest_.

```tex
% almost as involved as it gets; requires \usepackage[linguistics]{forest}, \usepackage[tikz]
\begin{forest}
sn edges
[CP
[D\\Who,name=1]
% name=1 will be used later to anchor arrows
[C' [C\\did ] [IP [NP [N' [N\\you ] ] ] [I' [I\\$t_{did}$ ] [ VP [$\varnothing$,name=2 ] [VP [ ]
[V'
% note the use of \varnothing, which is mathematical, and so is enclosed in $...$; do not use \{\} or (particularly) \[\] for in-line math
[V' [V\\hear ] [NP [D\\the] [N' [N\\{rumour} ] ] ] ]
[CP
[ ]
[C' [C\\that ] [IP [NP [N' [N\\Mary ] ] ] [I' [I ]
[VP [$\varnothing$,name=3 ] [VP [] [V' [V\\loves ]
[NP\\$t_{who}$,name=x]
] ] ] ] ] ] ] ] ] ] ] ] ] ]
\begin{pgfinterruptboundingbox}
% this is TikZ time
\draw[->,dotted,looseness=1,overlay] (x) to[out=south,in=west] (1);
% all arrows will start with \draw[->], the parameters could be dotted, dashdotted, dotted, looseness (to experiment with)
% (x) is the from where, and (1) is to where; the names in the example are very creative: (x) and (1)
% [out=__,in=__] are direction where arrow comes out and comes in respectively; south is bottom, west is left, and so on
\draw[->,dashed,looseness=2] (x) to[out=south,in=south west] (3);
\draw[->,dashed,looseness=1.5] (3) to[out=south west,in=west] (2);
% looseness is useful when an arrow from a lower node to an upper node crosses the tree -- loosing it leads it out of the tree; there are other more elegant options not to be explored here
\draw[->,dashed,looseness=2] (2) to[out=south west,in=west] (1);
\end{pgfinterruptboundingbox}
\end{forest}
```

Finally, multidominance. There are multiple ways to do this, but the most straigthforward and simple (albeit perhaps less stylistically appealing) one is still rudimentary TikZ. For two kinds of parallel merge respectively:

```tex
% from Citko 2011:119 (adapted), which was in turn from Citko 2005 (and same below);
% requires \usepackage[linguistics]{forest} and \usepackage{tikz}
\begin{forest}
sn edges
[L,name=L [,name=D] [ [$\beta$] [K [$\gamma$,name=G] [$\alpha$]]] ]
\begin{pgfinterruptboundingbox}
\draw[-,looseness=1] (G) to [out=west,in=south] (D);
\end{pgfinterruptboundingbox}
\end{forest}
```

```tex
% a slightly different one; requires same packages as the example immediately above
\begin{forest}where n children=0{tier=T}{}
[,phantom [K,name=A [$\alpha$, ][,phantom]][,phantom [$\beta$,name=C ]][L,name=D [,phantom][$\gamma$]]]
\draw[dotted] (C.north) -- (A.south);
\draw[dotted] (C.north) -- (D.south);
\end{forest}
```
* * *

[go back](./index.md)
