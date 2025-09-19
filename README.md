## Что это такое

- `template.tex` -- шаблон LaTeX с титульным листом и основными разделами,
- `preamble.tex` -- преамбула LaTeX для оформления контрольных,
лабораторных и курсовых работ.

Для работы требуется какой-либо дистрибутив LaTeX, например:

- [texlive](https://tug.org) для linux или для windows.
- [MiKTeX](https://miktex.org/) на windows

Шаблоны вдохновлены [ОС ТУСУР 01-2021](https://regulations.tusur.ru/system/document_files/files/000/000/094/original/OS_TUSUR_01-2021_(soglasovano).pdf?1735368202&ysclid=mfoafj1c5i655723067).

## Как использовать

**Клонируйте** себе данный репозиторий

```sh
mkdir repos
cd repos
git clone https://gitflic.ru/project/salixsorbus/tusurlatex.git
```

**Перейдите** в папку с работой и
**Скопируйте** файл шаблона `template.tex` в эту папку:

```sh
cp ~/repos/tusurlatex/template.tex lab1.tex
```

**Создайте** символическую ссылку на файл преамбулы:

```sh
ln -s ~/repos/tusurlp.tex tusurlp.tex
```
