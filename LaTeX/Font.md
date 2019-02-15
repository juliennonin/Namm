# Font Selection

The [LaTeX Font Catalogue](http://www.tug.dk/FontCatalogue/) displays *all* free fonts available for easy use with LaTeX, and how to use them.

### Basic commands
Font Families are grouped into three main categories. The following declarations let you choose between the three pre-defined font families :

|Switch|Font Family|Default|
|:---|:---|:---|
| `\rmfamily` | roman (serified)| Computer Modern Roman|
| `\sffamily` | sans serif | Computer Modern Sans Serif|
| `\ttfamily` | monospaced ("typewriter")| Computer Modern Typewriter |

Within each font family, the following declarations select the "series" (stroke width)

|Command|Switch|Description|
|:---|:---|:---|
|`\textmd{}`|`{\mdseries ...}`|regular (medium)|
|`\textbf{}`|`{\bfseries ...}`|bold|
|`\textlf{}`|`{\lfseries ...}`|light|

And the shape :

|Command|Switch|Description|
|:---|:---|:---|
|`\textup{}`|`{\upshape ...}`|upright|
|`\textsl{}`|`{\slshape ...}`|slanted|
|`\textit{}`|`{\itshape ...}`|italic|
|`\textsc{}`|`{\scshape ...}`|small caps|

### Change the default fonts for the whole document
The families selected by these declations are determined by the vamues of the related macros `\rmdefault`, `\sfdefault` and `\ttdefault`. To do thus you need to know the name of the desired font family.

```LaTeX
\renewcommand{\rmdefault}{<name>}
```

### Change the fonts to be used for certain parts
```LaTeX
{\fontfamily{<name>}\selectfont}
```
### How to know the name of a font family ?
The font family can be derived without analyzing the source code. The current family name is stored in macro `\f@family`. Thus, generate a short test document that uses the font as you need it : 

```LaTeX
\documentclass{article}
\usepackage[lining]{sourcesanspro}
\usepackage{color}
\begin{document}
    \makeatletter
    \textsf{Family of Source Sans Pro: \textcolor{red}{\f@family}}
\end{document}
```

> The value of `f@family` with the package `sourcesanspro` is `SourceSansPro-TLF` 
## Further reading

* [Font selection in LaTeX : The most FAQ](https://www.tug.org/pracjourn/2006-1/schmidt/schmidt.pdf), Walter Schmidt
