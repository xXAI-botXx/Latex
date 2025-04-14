# Latex
Helper Project for using Latex

Contents:
- [General](#general)
- [Quick Start](#quick-start)
- [Write a Thesis](#write-a-thesis)
- [Write a Book](#write-a-book)
- [Write a Presentation](#write-a-presentation)


<br><br>

---
### General

LaTeX is a language for defining the appearance of text and images. Pronounced as "latech". There are many formats to create, for example thesis, books, presentations, curriculum vitae and much more.<br>In comparison to Word and other modern writing software, LaTeX does not provide any graphical interface but shines with much customizability and flexiblity. And Latex is textbased, so it can be versionated via git or other programs, which is very important when writing a book or a huge thesis, to make the process save and without sorries and worries.<br>
Another reason why Latex is so famous are the extensions. There are extensions for the base file which defines your frame (document class), for styling (packages), for blueprints/templates which can be customized and used and for other things (like bundles). Most LaTeX distributions/compilers comes with many useful extensions, like common class types.

Next let's talk about the **installation**.<br>
The Latex compiler is most likely [TeX Live](https://tug.org/texlive) or [MiKTeX](https://miktex.org). Just follow the instructions on the website. On Ubuntu systems there are commonly easy to use apt commands which you can use.<br>
With a compiler, we have the most important part, but most likely we also want a **IDE**. There are many editors for LaTeX which come with more or less features. For example the local IDE [TexStudio](https://www.texstudio.org/) or the online web IDE [Overleaf](https://www.overleaf.com/). Those are 2 of the most common and my personal favor IDEs for writing and compiling Latex, just click on the names/links and follow the instruction on the website (Overleaf runs in your webbrower and so does not need an installation). Another very simple but yet very stable Latex IDE is [TeXworks](https://tug.org/texworks/).<br>
Of course you can also write Latex code inside of any editor and compile it with the installed Latex compiler to a PDF or what your wishes output is, but using one of these IDEs is recommended.<br>Take your time and play around with your choosen IDE, they often have more features then used. For example TexStudio have many Latex commands choosable in the menu, which is very comfortable, so you don't have to remember or search for them everytime.

On Ubuntu you can for example easily install texlive and texstudio:
```bash
sudo apt update
sudo apt install texlive-full
sudo apt install texstudio
```

On Windows you also have the option to compile your latex with a docker container mounted to your real local memory and code latex in windows and compile it under linux docker container. For that you need to [install docker](https://docs.docker.com/desktop/setup/install/windows-install/). Now pull the official texlive image:
```bash
docker pull texlive/texlive
```

And now you can edit your local latex project inisde of a docker linux container:
```bash
docker run --rm -v C:/Users/YourUsername/Documents/latexfiles:/files texlive/texlive pdflatex /files/your-file.tex
```

To make this more comfortable you also can open the setting on you TexStudio go to `Options > Configure TeXstudio > Build` and in the *PDFLaTeX* field you type: `docker run --rm -v C:/Users/YourUsername/Documents/latexfiles:/files texlive/texlive pdflatex /files/your-file.tex`. In that way TexStudio will use TexLive via your docker to compile your latex code. This might be a more complicated way, but sometimes it is hard to get to work on windows and in this way it should always work also under "windows".

<br><br>

Lastly lets talk about **compiling your work** into a pdf or whatever you want. First make sure that your latex compiler is setup right:
```bash
pdflatex --version
```

<br><br>

Next lets compile your work into a **PDF**:
Open your shell (bash, cmd, powershell) and naviagte to your project folder. Next you can call the command from your compiler.
```bash
D: && cd D:/Informatik/Projekte/AI
pdflatex ai.tex
```
Most IDEs already include such commands inside and you most likely just have to click on the green run button.

If you use BibTex you should compile like that:
```bash
pdflatex myfile.tex
bibtex myfile
pdflatex myfile.tex
pdflatex myfile.tex
```

Or if you use BibTex with Biber, you have to compile like that:
```bash
pdflatex myfile.tex
biber myfile
pdflatex myfile.tex
pdflatex myfile.tex
```

<br><br>

Next lets compile your work into a **E-Book**:
Standard latex compiler does not provide an ebook conversion, but you can use other software like pandoc.
1. Download and install pandoc from: https://pandoc.org/installing.html
2. Now you have to open your command terminal (bash, cmd, powershell) and navigate to your project and type the command to convert your tex into an epub file:
    ```bash
    D: && cd D:/Informatik/Projekte/AI
    pandoc ai.tex -o ai.epub
    ```
    Change the tex and epub file name as you wish.


<br><br>

Next lets compile your work into a **Word**:
Standard latex compiler does not provide an word conversion, but you can use other software like pandoc.
1. Download and install pandoc from: https://pandoc.org/installing.html
2. Now you have to open your command terminal (bash, cmd, powershell) and navigate to your project and type the command to convert your tex into an epub file:
    ```bash
    D: && cd D:/Informatik/Projekte/AI
    pandoc ai.tex -o ai.docx
    ```
    Change the tex and docx file name as you wish.


<br><br>

Next lets compile your work into a **HTML**:
Standard latex compiler does not provide an html conversion, but you can use other software like pandoc.
1. Download and install pandoc from: https://pandoc.org/installing.html
2. Now you have to open your command terminal (bash, cmd, powershell) and navigate to your project and type the command to convert your tex into an epub file:
    ```bash
    D: && cd D:/Informatik/Projekte/AI
    pandoc ai.tex -o ai.html
    ```
    Change the tex and html file name as you wish.


<br><br>

Next lets compile your work into a **Markdown**:
Standard latex compiler does not provide an markdown conversion, but you can use other software like pandoc.
1. Download and install pandoc from: https://pandoc.org/installing.html
2. Now you have to open your command terminal (bash, cmd, powershell) and navigate to your project and type the command to convert your tex into an epub file:
    ```bash
    D: && cd D:/Informatik/Projekte/AI
    pandoc ai.tex -o ai.md
    ```
    Change the tex and md file name as you wish.


<br><br>

---
### Quick Start

For modern and feature-rich class-types the bundle **KOMA-Script** is the perfect choice and does provide you all the need for a quick document (but of cause also for large documents). Classes from the KOMA-Scripts bundle starts with *scr* (which stands for Script, the orignal name of the bundle). For example the class type **scrartcl** for a modern article class type.

The basics of latex can best be understood by looking an simple example:

```latex
% start of 'preambel' part
% defining document class -> the frame of your writing
\documentclass[paper=a4,oneside,fontsize=11pt,parskip=full][scrartcl]

% beginning your document & end of preambel
\begin{document}

    % write the table of contents
    \tableofcontents

    % add a non-numbered section
    % you can also use \section* -> but this will not add a entry in the table of contents
    \addsec{Introduction}
        This is my awesome Introduction with much text. And there is even more text and latex is really awesome. This text is just for filling this introduction a little bit, else it would be too small and you couldn't see something interesting.

    % add a numbered section
    \section{The first numbered Section}
        This is the awesome first section, of many which will follow! And this text will be here to show all the power of latex.
        \\
        \\
        Lets make a bulletpoint list:
        \begin{itemize}
            \item one apple
            \item two bananas
            \item and no coconut
        \end{itemize} 

        Or even better, we use a numbered list!
        \begin{enumerate}
            \item pizza
            \item pancakes
            \item and still no coconut
        \end{enumerate} 

        We also can make \ref{sec:sec:second}[references to labels].

    \section{The next awesome Section in a row}
    \label{sec:second}
        Latex loves math and here is why: \( f(x) \) or \(w_i\).\\
        Or make a multiline latex command:
        \begin{equation}
            \int_a^b f(x)\,\mathrm[d]x \approx(b-a)
            \sum_{i=0}^n w_i f(x_i)
        \end{equation}

\end{document}


```

This basic document already covers some of the most important latex features. For example one or multiple math. At the beginning we define our document and a bit cryptic is parskip -> this defines how much space between paragraphs should be (remove the argument to see the difference).<br>
Also at the begiining we define with *oneside* that we want to have only one writing tex column. We also could have 2 columns with *twoside*.<br>
Making a simple line break you can use *\\\\*.<br>
For labels it is recommended to use common sense, lowered and short prefixes: cha, sec, eq/func, fig, tab.<br>
For inline math you can use `\(...\)` or the old and a bit simpler version `$...$`.

You have to compile your latex code most likely 2 times, because links (with labels or other) have to be created before they can be referenced. Or said simple: When you only compile your latex code once, it is possible, that some references are not working.


<br><br>

---
### Write a Thesis

You always have the choice if you want to build your own latex code from ground up or use a template. Both ways are valid and sometimes one is better sometimes the other other apporach.<br>
When coding your own code, you should inform yourself and if you use a template, you should choose wisely.<br>
For a thesis the **ClassicThesis** package/template can be very useful. It is modern. You can download it [here](https://ctan.org/pkg/classicthesis) or from this repo under *templates* ([click me](./templates/ClassicThesis/)). Just download the zip file and extract its content. Now you can open the folder with your IDE and start your thesis! The ClassicThesis.tex file is your main file.

> There are many templates, you can also use this bachelor thesis https://github.com/xXAI-botXx/Bachelor-Exam/, just remove the content and place your content over it.

You can rename **ClassicThesis.tex** to your project name. You also can look and change the properties in the *ClassicThesis.tex* and *classicthesis-config.tex*.

It is smart to use a well-known template for your thesis. And you can modify it as you wish.

In this template we can see a simple but very good coding, because all elements get seperated from each other. Like the preambel is declared in an extra file and each writing is declared in an extra file with the **\\include** keyword.

Make a break and go to a new page with *\\clearpage* or when using *twoside* then *\\cleardoublepage*.

The *\\pagenumbering[arabic]* sets the numbering style and resets the numbering to 0.

A document have following areas:
- \\part
    - \\chapter
        - \\section
            - \\subsection

For appendix you should use the *\\appendix* command, which resets the chapter numbering and change to alphabetic counting.

For custom spacing/marging use the geometry package in the preambel:
```latex
\usepackage[inner=1.5cm,outer=3cm,top=2cm,bottom=2cm,  bindingoffset=5mm]{geometry}
```

Or for onesided:
```latex
\usepackage[left=1.5cm,right=1.5cm,top=2cm,bottom=2cm,  bindingoffset=5mm]{geometry}
```

And if you want to use a package you call `\usepackage` or `\RequirePackage` if you call it before the `\documentclass` command.


To summarize these little details in the big picture. You can start your thesis from scratch, I will show you a very simple template/starting-point in a minute. But for a thesis it is more recommended to use a well-known template from the internet or from your university.<br>
Another important aspect is the **citation**. Here latex provide a extension called BibTex which is very powerfull and easy to use. Just create a .bib file where you pass all your citation references:

For example:
```bib
@book{knuth1984texbook,
  author    = {Donald E. Knuth},
  title     = {The TeXbook},
  year      = {1984},
  publisher = {Addison-Wesley}
}

@article{yann1989backprop,
  author  = {Yann LeCun and Léon Bottou and Yoshua Bengio and Patrick Haffner},
  title   = {Gradient-Based Learning Applied to Document Recognition},
  journal = {Proceedings of the IEEE},
  year    = {1998},
  volume  = {86},
  number  = {11},
  pages   = {2278--2324}
}
```

Now you can set your citation style inside of latex and import your citations:
```latex
\usepackage[style=apa, backend=bibtex]{biblatex} % or style=numeric, authoryear, etc.
\addbibresource{your_bib_file_name.bib} % Link to your .bib file
```

or with biber:
```latex
\usepackage[style=apa, backend=biber]{biblatex} % or style=numeric, authoryear, etc.
\addbibresource{your_bib_file_name.bib} % Link to your .bib file
```

And use your citiation as:
```latex
\begin{document}

As shown by \cite{mueller2020}, the model is quite accurate. 
In a similar study, \citeauthor{mueller2020} (2020) demonstrated...

\printbibliography

\end{document}
```

There are many ways to cite:

| Command                | Output (for `numeric` style)            |
|------------------------|----------------------------------------|
| `\cite{key}`            | [1]                                    |
| `\textcite{key}`        | [1] — like `\cite{}` but as inline text |
| `\parencite{key}`       | [1] — same as `\cite{}`                |
| `\footcite{key}`        | Footnote with full citation            |
| `\citeauthor{key}`      | Author's name (Müller)                 |
| `\citeyear{key}`        | Year (2020)                            |
| `\citetitle{key}`       | *Title of the work*                    |
| `\citeurl{key}`         | URL (if available in the entry)        |



If you use BibTex with Biber, you have to compile like that:
```bash
pdflatex myfile.tex
biber myfile
pdflatex myfile.tex
pdflatex myfile.tex
```

Or if you use BibTex, you have to compile like that:
```bash
pdflatex myfile.tex
bibtex myfile
pdflatex myfile.tex
pdflatex myfile.tex
```

<br><br>

Here is a very very simple template for a thesis, you might want to adjust things like the cover page, oneside or twoside...

Structure:
```
thesis/
├── thesis.tex          % Main file
├── preamble.tex        % All settings & packages
├── content/
│   ├── titlepage.tex
│   ├── abstract.tex
│   ├── chapter1.tex
│   ├── chapter2.tex
│   └── appendix.tex
├── references.bib
```

./preambel.tex
```latex
% Preamble for thesis
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[english]{babel}
\usepackage{csquotes}
\usepackage[a4paper,margin=2.5cm]{geometry}
\usepackage{graphicx}
\usepackage{amsmath, amssymb}
\usepackage{hyperref}
\hypersetup{
    colorlinks=true,
    linkcolor=black,
    citecolor=blue,
    urlcolor=blue
}

% For bibliography
\usepackage[style=numeric,backend=biber]{biblatex}
\addbibresource{references.bib}

% Optional: Nicer header/footer
\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhf{}
\fancyhead[L]{\leftmark}
\fancyfoot[C]{\thepage}
```

./content/titlepage.tex
```latex
\begin{titlepage}
    \centering
    {\scshape\LARGE University Name \par}
    \vspace{1.5cm}
    {\scshape\Large Bachelor's Thesis \par}
    \vspace{2cm}
    {\huge\bfseries Title of Your Thesis\par}
    \vspace{2cm}
    {\Large Author: Tobia Ippolito\par}
    \vspace{0.5cm}
    {\large Supervisor: Prof. Dr. XYZ\par}
    \vfill
    {\large \today\par}
\end{titlepage}
```

./content/abstract.tex
```latex
\chapter*{Abstract}
\label{abstract}
\addcontentsline{toc}{chapter}{Abstract}
This thesis investigates the role of...
```

./content/chapter1.tex
```latex
\chapter{Introduction}
This is the introduction. See work by \cite{mueller2020} for more details.
```

./references.bib
```latex
@book{mueller2020,
  author    = {Max Müller},
  title     = {Introduction to AI},
  year      = {2020},
  publisher = {Tech Press}
}
```

And you can compile your work with:
1. Open your bash/cmd
2. Navigate to your project
3. Run:
    ```bash
    pdflatex thesis.tex
    biber thesis
    pdflatex thesis.tex
    pdflatex thesis.tex
    ```


<br><br>

---
### Write a Book

A book is different from a thesis, other spacings, other page size and much more. The KOMA-Script documentclass **scrbook** is perfect for this subject.

I show a simple but good template for a book. Feel free to customize it for your need!

./ai.tex (your main file)
```latex
% Main Document %

% Check Compiler: pdflatex --version

% PDF:
%    Open cmd/powershell + Run: 
%    		D: && cd D:/Informatik/Projekte/AI
%    		pdflatex ai.tex
% EBOOK: 
%    Download: https://pandoc.org/installing.html
%    Open cmd/powershell + Run: 
% 			D: && cd D:/Informatik/Projekte/AI
%    		pandoc ai.tex -o ai.epub

% Load + Define document
\documentclass[fontsize=11pt,paper=a5,pagesize=auto]{scrbook}

\include{preambel}

% Start Document
\begin{document}

% First pages
\maketitle
\tableofcontents

% Add Content
\include{content/preface}
\part{Basics}
\include{content/part_basics/introduction}
\include{content/part_basics/machine_learning}
\include{content/part_basics/neural_networks}
\include{content/part_basics/foundation_models}
\part{Neural Networks}
\include{content/part_neural_networks/architectures}
\include{content/part_neural_networks/learning_methods}
% FIXME ...

% \appendix
% \include{}

\end{document}
```

./preamble.tex (your preambel file)
```latex

% === === ===
% Extensions
% === === ===
% Set margins
\usepackage[
	a5paper,
	top=2cm,
	bottom=2cm,
	left=2cm,
	right=2cm
]{geometry}

% Font encoding & Font Style
\usepackage[T1]{fontenc}
\usepackage{lmodern}

% Dummy Texts
\usepackage[english]{babel}  % required from blindtext
\usepackage{blindtext}

% Better text justification
\usepackage{microtype}

% Turn-Off additional space after a sentence
\frenchspacing

% Make hpyer links and references and table-of-content clickable
\usepackage[
	colorlinks=true,
	linkcolor=black,      % for table-of-content & ref
	urlcolor=blue,       % for URL links
	citecolor=blue       % for \cite
]{hyperref}


% === === ===
% General Book Information
% === === ===
\title{Artificial Intelligence}
\subtitle{Naked and ready for Use}
\author{Tobia Ippolito}
\date{}
```

./content/preface.tex (your preface file)
```latex
\chapter{Preface}
\label{cha:preface}



    \section{Foreword}
    \label{sec:foreword}
        Why the book got created? Why is it relevant for anyone? \\
        \\
        \Blindtext



    \section{What to Expect}
    \label{sec:what-to-expect}
        Expectations are important\dots \\
        \blindtext


        
    \section{The Author}
    \label{sec:the-author}
        Why should you read a book from the author? What are the sources of the autor? Experience? Books? AI? \\
        \\
        \blindtext
```

./content/part_basics/introduction.tex (one of your content file)
```latex
\chapter{Introduction}
\label{cha:introduction}

	\Blindtext
```

And like that you can more content.

<br><br>

---
### Write a Presentation

Coming soon...











