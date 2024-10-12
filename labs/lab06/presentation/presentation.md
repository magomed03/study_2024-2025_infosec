---
## Front matter
lang: ru-RU
title: Презентация по лабораторной работе №5
subtitle: Основы информационной безопасности
author:
  - Мажитов М. А.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 28 сентября 2024

## i18n babel
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

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Мажитов Магомед Асхабович
  * студент группы НКНбд-01-21
  * Российский университет дружбы народов

:::
::: {.column width="30%"}

![](./image/ava.jpeg)

:::
::::::::::::::

## Цель

Изучение механизмов изменения идентификаторов, применения SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

## Выполнение лабораторной работы. 

Проверил установлен ли компилятор *gcc* и *g++*.

![Компилятор](image/1.png){ #fig:001 width=70% }

##

Вошел в систему от имени пользователя guest и создал программу simpleid.c.

![Создание simpleid.c](image/2.png){ #fig:002 width=50% }

![Код программы simpleid.c](image/3.png){ #fig:002 width=50% }

##

Скомплилировал программу и убедился, что файл программы создан. Далее запустил исполнительный файл, а также ввел системную программу *id* для дальнейшего сравнения выводов. 

![Компиляция simpleid.c](image/4.png){ #fig:003 width=70% }

Результаты идентичны.

##

Создал программу *simpleid2.c*.

![Создание simpleid2.c](image/5.png){ #fig:005 width=70% }

![Код программы simpleid2.c](image/6.png){ #fig:002 width=50% }


##

Скомпилоровал программу и сравнил выводы прошлой и новой программ.

![Сравнение](image/7.png){ #fig:006 width=70% }

##

Далее я поменял владельца файла *simpleid2* и изменил права доступа к нему.

![Манипуляции simpleid2](image/8.png){ #fig:007 width=70% }

##

Запустил *simpleid2* и *id*.

![Сравнение](image/18.png){ #fig:008 width=70% }

Как мы видим после изменения владельца *simpleid2*, вывод программы изменился.

##

Создал программу *readfile.c*. Скомпилировал файл и далее также изменил владельца *readfile* и права доступа к нему, так, чтобы только суперпользователь(root) мог прочитать его, a guest не мог.

![Изменение владельца readfile](image/9.png){ #fig:009 width=70% }

##

 Попробовал прочитать файл от имени *guest*. 

![Попытка прочитать readfile](image/10.png){ #fig:010 width=70% }

Попытка не увенчалась успехом.


##

Проверил, может ли программа readfile прочитать файл *readfile.c* и */etc/shadow*.

![Попытка запустить readfile](image/11.png){ #fig:010 width=70% }

##

Проверил, установлен ли атрибут *Sticky* на директории /tmp. 

![Проверка наличия Sticky атрибута](image/12.png){ #fig:010 width=70% }

##

От имени пользователя *guest* создал файл *file01.txt* в директории */tmp* со словом test и изменил права доступа к нему. 

![Создание file01.txt](image/19.png){ #fig:010 width=70% }

##

От пользователя guest2 (не являющегося владельцем) попробовал прочитать файл, переписать содержимое файла, а также дописать в файл новые данные. 

![Манипуляции с file01.txt](image/13.png){ #fig:010 width=70% }

##

Попробовал удалить файл. 

![Попытка удалить file01.txt](image/15.png){ #fig:010 width=70% }

##

Повысив права до суперпользователя, снял атрибут *t*. 

![Снятие атрибута t](image/16.png){ #fig:010 width=70% }

##

Повторил действия из пунктов **13-14**. 

![Манипуляции с file01.txt](image/17.png){ #fig:010 width=70% }

В этот раз получилось удалить *file01.txt*.

##

Попробовал удалить файл. 

![Попытка удалить file01.txt](image/15.png){ #fig:010 width=70% }

## Вывод

Изучил механизм изменения идентификаторов, применил SetUID- и Sticky-биты. Получил практические навыки работы в консоли с дополнительными атрибутами. Рассмотрел работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

## Список литературы. Библиография

::: {#refs}
:::