---
## Front matter
lang: ru-RU
title: Лабораторная работа №8
subtitle: Модель TCP/AQM
author:
  - Демидович Н. М.
institute:
  - РУДН
date: 29 марта 2024

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Демидович Никита Михайлович
  * Студент группы НКНбд-01-22
  * Студ. билет: 1132221550
  * РУДН
  * [1132221550@rudn.ru](mailto:1132221550@rudn.ru)
  * <https://github.com/nikdem1>

:::
::: {.column width="30%"}

![](./image/kulyabov.jpg)

:::
::::::::::::::

# Цели и задачи

## Цель

Реализовать модель TCP/AQM в xcos и OpenModelica.

## Задачи

1. Построить модель TCP/AQM в xcos.
2. Построить графики динамики изменения размера TCP окна $W(t)$ и размера очереди $Q(t)$.
3. Построить модель TCP/AQM в OpenModelica.

# Ход выполнения работы

## Модель TCP/AQM в xcos

Построим схему xcos, моделирующую нашу систему, с начальными значениями параметров $N = 1, R = 1, K = 5.3, C = 1, W(0) = 0.1, Q(0) = 1$.
Для этого сначала зададим переменные окружения.
Затем реализуем модель TCP/AQM, разместив блоки интегрирования, суммирования, произведения, констант, а также регистрирующие устройства.

## Вид модели TCP/AQM в xcos

Общий итоговый вид модели (рис. [-@fig:001]):

![Модель TCP/AQM в xcos](image/1.png){#fig:001 width=70%}

## Изменения размера и очереди

В результате получим динамику изменения размера TCP окна W(t) (зеленая линия) и размера очереди Q(t) (черная линия), а также фазовый портрет, который показывает наличие автоколебаний параметров системы — фазовая траектория осциллирует вокруг своей стационарной точки.

## График и фазовый портрет

Получим следующий график и фазовый портрет (рис. [-@fig:002]) - (рис. [-@fig:003]):

![Динамика изменения размера TCP окна W (t) и размера очереди Q(t)](image/2.png){#fig:002 width=70%}

![Фазовый портрет (W, Q)](image/3.png){#fig:003 width=70%}

## Реализация в OpenModelica

Перейдем к реализации модели в OpenModelica. Зададим параметры, начальные значения и систему уравнений.

```
parameter Real N=1;
parameter Real R=1;
parameter Real K=5.3;
parameter Real C=1;

Real W(start=0.1);
Real Q(start=1);

equation

der(W)= 1/R - W*delay(W, R)/(2*R)*K*delay(Q, R);
der(Q)= if (Q==0) then max(N*W/R-C,0) else (N*W/R-C);
```

Выполнив симуляцию, получим динамику изменения размера TCP окна W(t) (зеленая линия) и размера очереди Q(t)(черная линия), а также слпдующий фазовый портрет, который показывает наличие автоколебаний параметров системы — фазовая траектория осциллирует вокруг своей стационарной точки.

## Фазовый портрет

Он имел следующий вид (рис. [-@fig:003]):

![Фазовый портрет (W, Q). OpenModelica](image/4.png){#fig:004 width=70%}

# Результаты

## Выводы

В результате выполнения данной лабораторной работы я научился строить математическую модель TCP/AQM в xcos и OpenModelica.

# Список источников

## Список литературы

1. Братусь А. С., Новожилов Артем Сергеевич abd Платонов А. П. Динамические
системы и модели биологии. — М. : ФИЗМАТЛИТ, 2010. — 400 с.
2. OM overall User’s Guide. — 2020. — URL: https://www.openmodelica.org/
useresresources/userdocumentation.
3. Modelica Language. — URL: https : / / www . modelica . org /
modelicalanguage.
4. OpenModelica. — URL: https://www.openmodelica.org/.
5. Xcos. — URL: https://www.scilab.org/software/xcos.