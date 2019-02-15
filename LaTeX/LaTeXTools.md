# LaTexTools
[LaTexTools](https://latextools.readthedocs.io/en/latest/) plugin provides several features that simplify working with LaTeX files.
## Keybindings
Most LaTexTools facilities are triggered using `Ctrl+l` followed by some other key or key combination.

|Keybinding | Description |
|:----:|:----:|
|`Ctrl+b`|Compiling LaTeX files (ST keybinding)|
|`Ctrl+shift+b`|Selecting build variant (ST keybinding)|
|`shift+escape`|Show the LaTeXTools build panel|
|`Ctrl+l`, `backspace`|Remove temporary files from build (PDF kept)|
|`Ctrl+l`, `j` | When working in an ST view, jump in PDF text location|
|`Ctrl+left-click` | Inverse search : from the PDF file back to the TeX doc in ST|
|`Ctrl+l`, `Ctrl+f` | Fill helper for commands such as `\usepackage`, `\include`, `\includegraphics`, `\input`|
|`Ctrl+l`, `Ctrl+j` | Open a file include using `\input` or `\include`, or an image included with `\includegraphics`|
|`Ctrl+l`, `Ctrl+o` | Open a file include using `\input` or `\include`. If the file does not exist, it will also create the missing file and add the magic root comment (`%!TEX root=`) to the new file|
|`Ctrl+l`, `w` | Word count |

|Keybinding | Description |
|:----:|:----:|
|`Ctrl+l`, `c` | Insert a LaTeX command |
|`Ctrl+l`, `e` | Insert a LaTeX environment |
|`Ctrl+l`, `Ctrl+c` | Iwrap the selected text in a LaTeX command structure |
|`Ctrl+l`, `Ctrl+e` | `\emph{blah}` |
|`Ctrl+l`, `Ctrl+b` | `\textbf{blah}` |
|`Ctrl+l`, `Ctrl+u` | `\underline{blah}` |
|`Ctrl+l`, `Ctrl+t` | `\texttt{blah}` |
|`Ctrl+l`, `Ctrl+n` | `\begin{env} blah \end{env}` |





---
## Configure LaTeXTools
To edit the LaTeXTools user settings, select **Preferences/Package Settings/LaTeXTools/Settings-User** from the ST menu.

### Multi-file documents
If the first line in the current consists of the following text, then the tex&friends are invoked on the sepcified master file, instead of the current one
```
%!TEX root = <master file name>.tex
```

### Project-Specific Settings
Any settings can be overriden on a project-specific basis if you are using ST's [project system](https://www.sublimetext.com/docs/3/projects.html) (create a `.sublime-project` file). To use project-specific settings, simply create a `"settings"` section in your project file. The structure and format is the same as for the `LaTeXTools.sublime-settings` file.

```JSON
{
    ... <folder-related options here> ...

    "settings" : {
        "TEXroot": "main.tex",
        "tex_file_exts": [".tex", ".tikz"],
        "builder_settings": {
            "program": "xelatex",
            "options": "--shell-escape"
        }
    }
}
```

### General Settings
* `output_directory` : specifies the output directory to sotre any file generated during a LaTeX build.
* `jobname` : specifies the jobname to use for the build
* `copy_output_on_build` : if `true` and you are using an `output_directory` (either set via the seting or the `%!TEX` directive) this instructs LaTeXTools to copy the resulting pdf to the same folder as the main tex file. (Can be also a list of extensions)
### Math-Live preview
* `preview_mat_mode` :
    * `"all"` : to show a phantom for each math environment
    * [`"selected"`] : to show a phatom only for the currently selected math environment
    * `"none"` : to disable math live preview
* `preview_math_template_packages` : an array containing the used packages for the template as latex code.
* `preview_math_template_preamble` : a string (or array) of the remaining preamble (not packages) for the file, which generates the math live preview.(Useful if you define math commands on your own)

### Preview Image
* `preview_image_mode`
    * `"all"` : to show a phantom for each `\includegraphics` command
    * `"selected"` : to show a phantom only for the currently selected `\includegraphics` command
    * [`"hover"`] : to show a popup if you hover an `\includegraphics` command
    * `"none"` : to disable image preview


---
## Installation (Linux)
### TeXLive
The ST build command (`Ctrl+B`) takes care of compiling your LaTeX source to PDF using `latexmk`.
You need to install TeXLive. Although it is highly recommended to install the version directly from TUG, it is possible to use the package manager included with the distribution.
```
apt-get install texlive
```
will get you a working but incomplete setup. You need to install `latexmk` via

```
apt-get install latexmk
```
You can use the **LaTeXTools: Check System** command to ensure that the expected binaries are found. You'll probably need a few extras.

```
apt-get install texlive-latex-extra
```

### ImageMagick & Ghostscript
To use the equation preview feature, Ghostscript 8g
 must be installed. (If you are using TeXLive, you should already have Ghostscript installed.)
```
apt-get install ghostscript
```
To use the image preview feature to view fie types not support by Sublime Text or Ghostscript (so anything other than PNGs, JPEGs, GIFs, PDFs, EPSs, and PSs), you will need to ensure than ImageMagick is installed.
```
apt-get install imagemagick
```

### Setup Viewer
LaTeXTools assumes you are using **Evince** Document Viewer as your PDF Viewer.
```
apt-get install evince
```

### Install a new package
Let's say we want to add the new `mhchem` LaTeX package. However, LaTeX pachages are not downloadable independently but are grouped into packages. We will then use the `apt-cache` command.
```
apt-cache search mhchem
```
So the `texlive-science` package contains the desired LaTeX package. To show all contained packages :
```
apt-cache show texlive-science
```
At last, to download the package :
```
apt-get install texlive-science
```