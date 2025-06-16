---
## Front matter
title: "Лабораторная работа №17"
subtitle: "Задания для самостоятельной работы"
author: "Демидович Никита Михайлович"

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
lot: false # List of tables
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

# Моделирование работы вычислительного центра

## Постановка задачи

На вычислительном центре в обработку принимаются три класса заданий А, В и С.
Исходя из наличия оперативной памяти ЭВМ задания классов А и В могут решаться
одновременно, а задания класса С монополизируют ЭВМ. Задания класса А поступают через 20 +/- 5 мин, класса В - через 20 +/- 10 мин, класса С - через 28 +/- 5 мин
и требуют для выполнения: класс А - 20 +/- 5 мин, класс В - 21 +/- 3 мин, класс
С - 28 +/- 5 мин. Задачи класса С загружаются в ЭВМ, если она полностью свободна.
Задачи классов А и В могут дозагружаться к решающей задаче.
Смоделировать работу ЭВМ за 80 ч. Определить её загрузку.

## Код модели

Ниже представлен код модели:

```
ram STORAGE 2

;класс A
GENERATE 20,5
QUEUE class_A
ENTER ram,1
DEPART class_A
ADVANCE 20,5
LEAVE ram,1
TERMINATE 0

;класс B
GENERATE 20,10
QUEUE class_A
ENTER ram,1
DEPART class_A
ADVANCE 21,3
LEAVE ram,1
TERMINATE 0

;класс C
GENERATE 28,5
QUEUE class_A
ENTER ram,2
DEPART class_A
ADVANCE 28,5
LEAVE ram,2
TERMINATE 0

;таймер
GENERATE 4800
TERMINATE 1
```

## Отчет модели

Ниже представлен отчет модели (рис. [-@fig:001]) - (рис. [-@fig:002]):

![Отчет модели работы вычислительного центра 1](image/1.png){#fig:001 width=70%}

![Отчет модели работы вычислительного центра 2](image/2.png){#fig:002 width=70%}

## Задание

Из отчета нетрудно видеть, что средняя загрузка составила 0.994.

# Модель работы аэропорта

## Постановка задачи

Самолеты прибывают для посадки в район аэропорта каждые 10 +/- 5 мин. Если
взлетно-посадочная полоса свободна, прибывший самолет получает разрешение на
посадку. Если полоса занята, самолет выполняет полет по кругу и возвращается
в аэропорт каждые 5 мин. Если после пятого круга самолет не получает разрешения
на посадку, он отправляется на запасной аэродром.
В аэропорту через каждые 10 +/- 2 мин к взлетно-посадочной полосе выруливают
готовые к взлету самолеты и получают разрешение на взлет, если полоса свободна.
Для взлета и посадки самолеты занимают полосу ровно на 2 мин. Если при свободной
полосе одновременно один самолет прибывает для посадки, а другой - для взлета,
то полоса предоставляется взлетающей машине.

Требуется:

- выполнить моделирование работы аэропорта в течение суток;
- подсчитать количество самолётов, которые взлетели, сели и были направлены на
запасной аэродром;
- определить коэффициент загрузки взлетно-посадочной полосы.

## Код модели

Ниже представлен код модели:

```
GENERATE 10,5,,,1
ASSIGN 1,0
QUEUE arrival
landing GATE NU runway,wait
SEIZE runway
DEPART arrival
ADVANCE 2
RELEASE runway
TERMINATE 0

;посадка
wait TEST L p1,5,goaway
ADVANCE 5
ASSIGN 1+,1
TRANSFER 0,landing
goaway SEIZE reserve
DEPART arrival
RELEASE reserve
TERMINATE 0

;взлет
GENERATE 10,2,,,2
QUEUE takeoff
SEIZE runway
DEPART takeoff
ADVANCE 2
RELEASE runway
TERMINATE 0

;таймер
GENERATE 1440
TERMINATE 1
```

## Отчет модели

Ниже представлен отчет модели (рис. [-@fig:003]) - (рис. [-@fig:004]):

![Отчет модели работы аэропорта 1](image/3.png){#fig:003 width=70%}

![Отчет модели работы аэропорта 2](image/4.png){#fig:004 width=70%}

## Задание

Из отчета нетрудно видеть, что:

- влетело 142 самолета;
- сели 146 самолетов;
- на запасной аэродром отправилось 0 самолетов.

Коэффициент загрузки взлетно-посадочной полосы составил 0.400.

# Модель морского порта

## Постановка задачи

Морские суда прибывают в порт каждые [a +/- b] часов. В порту имеется N причалов.
Каждый корабль по длине занимает M причалов и находится в порту [B +/- e] часов.
Требуется построить GPSS-модель для анализа работы морского порта в течение
полугода, определить оптимальное количество причалов для эффективной работы
порта.
Исходные данные:
1) a = 20 ч, b = 5 ч, B = 10 ч, e = 3 ч, N = 10, M = 3;
2) a = 30 ч, b = 10 ч, B = 8 ч, e = 4 ч, N = 6, M = 2.

## Код модели

Ниже представлен код модели для первых исходных данных:

```
pier STORAGE 10
GENERATE 20,5

;моделирование занятия причала
QUEUE arrive
ENTER pier,3
DEPART arrive
ADVANCE 10,3
LEAVE pier,3
TERMINATE 0

;таймер
GENERATE 24
TERMINATE 1
START 180
```

Для вторых:

```
pier STORAGE 6
GENERATE 30,10

;моделирование занятия причала
QUEUE arrive
ENTER pier,4
DEPART arrive
ADVANCE 8,4
LEAVE pier,4
TERMINATE 0

;таймер
GENERATE 24
TERMINATE 1
START 180
```

## Отчет модели

Ниже представлен отчет модели (рис. [-@fig:005]) - (рис. [-@fig:006]):

![Отчет модели работы морского порта (условие 1)](image/5.png){#fig:005 width=70%}

![Отчет модели работы морского порта (условие 2)](image/7.png){#fig:006 width=70%}

## Задание

Ниже представлен отчеты наиболее оптимальных моделей (рис. [-@fig:007]) - (рис. [-@fig:008]):

![Отчет модели работы морского порта (условия 1), опт](image/6.png){#fig:007 width=70%}

![Отчет модели работы морского порта (условиe 2), опт](image/8.png){#fig:008 width=70%}

Вычисленные мною наиболее оптимальные количества причалов для наиболее эффективной работы порта: 3 - для первого условия и 2 - для второго.

# Выводы

В процессе выполнения данной лабораторной работы я выполнил самостоятельное задание и реализовал три имитационное модели на GPSS.

# Список источников

1. Jensen, K., Kristensen, L. M. — Lecture Notes, 2009
2. Электронная библиотека БГУ - Модели обслуживания, 2009