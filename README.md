## Что это такое

- `template.tex` -- шаблон LaTeX с титульным листом и основными разделами,
- `preamble.tex` -- преамбула LaTeX для оформления контрольных,
лабораторных и курсовых работ.

Для работы требуется какой-либо дистрибутив LaTeX, например:

- [texlive](https://tug.org) для linux или для windows.
- [MiKTeX](https://miktex.org/) на windows

Шаблоны вдохновлены [ОС ТУСУР 01-2021](https://regulations.tusur.ru/system/document_files/files/000/000/094/original/OS_TUSUR_01-2021_(soglasovano).pdf?1735368202&ysclid=mfoafj1c5i655723067).

## Как использовать

### Символическая ссылка

**Клонируйте** себе данный репозиторий

```sh
mkdir repos
cd repos
git clone https://gitverse.ru/asorbus/tusurlatex.git
```

**Перейдите** в папку с работой и
**Скопируйте** файл шаблона `template.tex` в эту папку:

```sh
cp ~/repos/tusurlatex/template.tex lab1.tex
```

**Создайте** символическую ссылку на файл преамбулы:

```sh
ln -s ~/repos/preamble.tex preamble.tex
```

### Подмодуль

Если проект вашей работы планируется размещать в git репозитории,
то подключите этот проект к вашему как подмодуль:

```sh
git submodule add https://gitverse.ru/asorbus/tusurlatex.git
```

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
