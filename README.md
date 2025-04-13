# Latex
Helper Project for using Latex

- [Basics](#basics)
    - [General](#general)
    - [Quick Start](#quick-start)
    - [Write a Thesis](#write-a-thesis)
    - [Write a Book](#write-a-book)
- [Cite](#cite)


---
### Basics

---



#### General

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

---
#### Quick Start

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
#### Write a Thesis

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


<br><br>

---
#### Write a Book

A book is different from a thesis, other spacings, other page size and much more. The KOMA-Script documentclass **scrbook** is perfect for this subject.


<br><br>

---
### Cite

...








