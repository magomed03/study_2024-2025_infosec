---
## Front matter
title: "Отчет по лабораторной работе №4"
subtitle: "Основы информационной безопасности"
author: "Мажитов Магомед Асхабович, НКНбд-01-21"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение практических навыков работы в консоли с расширенными атрибутами файлов.

# Теоретическое введение

**Права доступа** определяют, какие действия конкретный пользователь может или не может совершать с определенным файлами и каталогами. С помощью разрешений можно создать надежную среду — такую, в которой никто не может поменять содержимое ваших документов или повредить системные файлы. [1]

**Расширенные атрибуты файлов Linux** представляют собой пары имя:значение, которые постоянно связаны с файлами и каталогами, подобно тому как строки окружения связаны с процессом. Атрибут может быть определён или не определён. Если он определён, то его значение может быть или пустым, или не пустым. [2]

Расширенные атрибуты дополняют обычные атрибуты, которые связаны со всеми inode в файловой системе (т. е., данные stat(2)). Часто они используются для предоставления дополнительных возможностей файловой системы, например, дополнительные возможности безопасности, такие как списки контроля доступа (ACL), могут быть реализованы через расширенные атрибуты. [3]

*Установить атрибуты:*

- chattr filename

*Значения:*

- chattr +a # только добавление. Удаление и переименование запрещено;

- chattr +A # не фиксировать данные об обращении к файлу

- chattr +c # сжатый файл

- chattr +d # неархивируемый файл

- chattr +i # неизменяемый файл

- chattr +S # синхронное обновление

- chattr +s # безопасное удаление, (после удаления место на диске переписывается нулями)

- chattr +u # неудаляемый файл

- chattr -R # рекурсия

*Просмотреть атрибуты:*

- lsattr filename

*Опции:*

- lsattr -R # рекурсия

- lsattr -a # вывести все файлы (включая скрытые)

- lsattr -d # не выводить содержимое директории

# Выполнение лабораторной работы

**1** От имени пользователя guest определил расширенные атрибуты файла *file1*.

![Атрибуты файла](image/1.png){ #fig:001 width=70% }

**2** Установил командой *chmod 600 file1* на файл *file1* права, разрешающие чтение и запись для владельца файла. Далее попробовал установить на файл *file1* расширенный атрибут *a* от имени пользователя *guest*.

![Изменение прав и попытка добавить расширенный атрибут](image/2.png){ #fig:002 width=70% }

**3** Открываю новую вкладку терминала и захожу с правами администратора. Пробую установить на файл *file1* расширенный атрибут *a*.

![Добавление расширенного атрибута](image/3.png){ #fig:003 width=70% }

**4** От пользователя *guest* проверяю правильность установления атрибута.

![Расширенные атрибуты file1](image/4.png){ #fig:005 width=70% }

**5** Выполнил дозапись в файл *file1* слова *test*.

![Дозапись](image/5.png){ #fig:006 width=70% }

**6** Попробовал стереть имеющуюся в нём информацию, переименовать файл, а также изменить права доступа к файлу.

![Попытка различных манипуляций с файлом](image/6.png){ #fig:007 width=70% }

Как мы видим по скриншоту, попытки не увенчались успехом.

**7** Снял расширенный атрибут *a* с файла *file1* от имени суперпользователя.

![РСнятие расширенного атрибута](image/7.png){ #fig:008 width=70% }

**8** Попробовал повторить операции из пункта **6**.

![Попытка различных манипуляций с файлом](image/8.png){ #fig:009 width=70% }

С измененными расширенными атрибутами все операции выполнились успешно.

**9** Повторил пункты **3-6** по шагам, заменив атрибут «a» атрибутом «i». 

![Добавление расширенного атрибута](image/9.png){ #fig:010 width=70% }

![Попытка манипуляций с файлом сновым атрибутом](image/10.png){ #fig:010 width=70% }

Как и в прошлый раз, попытки не увенчались успехом.

# Выводы

В результате выполнения работы мы повысили свои навыки использования интерфейса командой строки, познакомились на примерах с тем, как используются основные и расширенные атрибуты при разграничении доступа.

# Список литературы. Библиография

[0] Методические материалы курса

[1] Права доступа: https://codechick.io/tutorials/unix-linux/unix-linux-permissions

[2] Расширенные атрибуты: https://ru.manpages.org/xattr/7

[3] Операции с расширенными атрибутами: https://p-n-z-8-8.livejournal.com/64493.html