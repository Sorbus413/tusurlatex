## Что это такое

- `template.tex` -- шаблон LaTeX с титульным листом и основными разделами,
- `preamble.tex` -- преамбула LaTeX для оформления контрольных,
лабораторных и курсовых работ.

Для работы требуется какой-либо дистрибутив LaTeX, например:

- [texlive](https://tug.org) для linux или для windows.
- [MiKTeX](https://miktex.org/) на windows

Шаблоны вдохновлены [ОС ТУСУР 01-2021](https://regulations.tusur.ru/system/document_files/files/000/000/094/original/OS_TUSUR_01-2021_(soglasovano).pdf?1735368202&ysclid=mfoafj1c5i655723067).

## Как использовать

### Если работа не в репозитории

1. **Клонируйте** себе данный репозиторий, например в папку `~/projects/`
1. **Перейдите** в папку с лабораторной или контрольной работой
1. **Скопируйте** файлы шаблона `template.tex` `preamble.tex` в эту папку:

```sh
cp ~/projects/tusurlatex/template.tex lab1.tex
cp ~/projects/tusurlatex/preamble.tex .
```

### Подмодуль

Если проект вашей работы планируется размещать в git репозитории,
то подключите этот проект к вашему как подмодуль при помощи
`git submodule add https://git...`

Затем добавьте его в `.gitignore`:

```.gitignore
tusurlatex/
```

При этом в основном документе ссылка на преамбулу тогда будет в виде:

```tex
\input{tusurlatex/preamble}
\begin{document}
    ...
```

## Что еще можно добавить

### Сети петри

В преамбулу:

```tex
\usetikzlibrary{petri, positioning, arrows.meta}

\tikzset{
	>={Stealth},
    place/.style={
        circle,
        draw,
        minimum size=12mm,
        inner sep=0pt
        },
    transition/.style={
        rectangle,
        draw,
        fill=black,
        minimum width=12mm,
        minimum height=1.5mm,
        inner sep=0pt,
        node distance=2cm,
        on grid
    }
}
```

В документ:

```tex
\begin{tikzpicture}
   \node[place, tokens=3, label=left:\texttt{pWait}] (pWait) {};
   \node[place, tokens=1, label=right:\texttt{pFree}] (pFree) [right=1.5cm of pWait] {};
   \node[transition, label=left:\texttt{tStart}] (tStart) [below=of pWait] {};
   \node[place, label=left:\texttt{pRun}] (pRun) [below=of tStart] {};
   \node[transition, label=right:\texttt{tFinish}] (tFinish) [below=of pFree] {};

   \path[->]
   (pWait) edge (tStart)
   (pFree) edge (tStart)
   (tStart) edge (pRun)
   (pRun) edge (tFinish)
   (tFinish) edge (pFree)
   (tFinish) edge (pWait);
\end{tikzpicture}
```

### Crow's Foot

Рисование вороньих лапок в тексте.
Полезно для ER-диаграмм.

```tex
% Команды для crow's foot нотации
\newcommand{\crowone}{%
    \tikz[baseline=-0.5ex, x=1.2ex, y=1.2ex]{
        \draw[thick] (0,0) -- (2,0);
        \draw[thick] (1,-.8) -- (1,.8);
        \draw[thick] (1.5,-.8) -- (1.5,.8);
    }%
}

\newcommand{\crowoneorzero}{%
    \tikz[baseline=-0.5ex, x=1.2ex, y=1.2ex]{
        \draw[thick] (0,0) -- (1,0);
        \draw[thick] (0.5,-0.8) -- (0.5,0.8);
        \draw[thick] (1.5,0) circle (0.5);
        \draw[thick] (2,0) -- (2.5,0);
    }%
}

\newcommand{\crowmany}{%
    \tikz[baseline=-0.5ex, x=1.2ex, y=1.2ex]{
        \draw[thick] (0,0) -- (2.5,0);
        \draw[thick] (1.5,0) -- (2.5,-.8);
        \draw[thick] (1.5,0) -- (2.5,.8);
    }%
}

\newcommand{\crowoneormany}{%
    \tikz[baseline=-0.5ex, x=1.2ex, y=1.2ex]{
        \draw[thick] (0,0) -- (2.5,0);
        \draw[thick] (1,-.8) -- (1,.8);
        \draw[thick] (1.5,0) -- (2.5,-.8);
        \draw[thick] (1.5,0) -- (2.5,.8);
    }%
}

\newcommand{\crowzeroormany}{%
    \tikz[baseline=-0.5ex, x=1.2ex, y=1.2ex]{
        \draw[thick] (0,0) -- (0.5,0);
        \draw[thick] (1,0) circle (0.5);
        \draw[thick] (1.5,0) -- (2.5,0);
        \draw[thick] (1.5,0) -- (2.5,-.8);
        \draw[thick] (1.5,0) -- (2.5,.8);
    }%
}
```
