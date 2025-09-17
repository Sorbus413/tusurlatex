## Что это такое

Файл `tusurLP.tex` [Tusur LaTeX Preamble] -- преамбула LaTeX для оформления контрольных,
лабораторных и курсовых работ.

Преамбула работает как и с [MiKTeX](https://miktex.org/) на windows, так и с
[texlive](https://tug.org) на linux или windows.

Преамбула вдохновлена [ОС ТУСУР 01-2021](https://regulations.tusur.ru/system/document_files/files/000/000/094/original/OS_TUSUR_01-2021_(soglasovano).pdf?1735368202&ysclid=mfoafj1c5i655723067).

## Как использовать

Клонируйте себе данный репозиторий

```sh
mkdir repos
cd repos
git clone https://gitflic.ru/project/salixsorbus/tusurlp.git
```

В папке с файлом основного документа `*.tex` создайте символическую ссылку на файл
преамбулы из репозитория.


**windows**

```cmd
mklink tusurlp.tex %userprofile%\repos\tururlp\tusurlp.tex
```

**linux**

```sh
ln -s tusurlp ~/repos/tusurlp.tex
```

Включите преамбулу в основной документ командой `\input{tusurlp}`:

```tex
\input{preamble}
\begin{document}
    ...
\end{document}
```
