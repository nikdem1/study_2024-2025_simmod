---
## Front matter
lang: ru-RU
title: Лабораторная работа №14
subtitle: Модель оформления заказов
author:
  - Демидович Н. М.
institute:
  - РУДН
date: 10 мая 2024

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

## Постановка задачи

Реализовать несколько моделей оформления заказов

# Модель 1: Один оператор

## Постановка задачи

В интернет-магазине заказы принимает один оператор. Интервалы поступления заказов распределены равномерно с интервалом 15 +/- 4 мин. Время оформления заказа также распределено равномерно на интервале 10 +/- 2 мин. Обработка поступивших заказов происходит в порядке очереди (FIFO). Требуется разработать модель обработки заказов в течение 8 часов.

## Схема модели

- Реализация и отчет модели

## Схема модели

![Код модели](image/1.png){#fig:001 width=70%}

## Схема модели

![Отчет модели](image/2.png){#fig:002 width=70%}

## Результаты модели

- блоков: 9;
- модель отработала 480 минут;
- кол-во одноканальных устройств: 1;
- общее количество заявок: 33;
- количество обслуженных заявок: 33;
- отработанных заявок: 32;
- среднее время обработки заявки: 0.021;
- максимум в очереди находились: 1 заявка;
- среднее время в очереди: 0.067.

# Упражнение 1

## Описание упражнения

Интервал поступление 3.14 +/- 1/7, интервал оформления - 6.66 +/- 1/7.

## Схема модели

![Код упражнения](image/3.png){#fig:003 width=70%}

## Схема модели

![Отчет упражнения](image/4.png){#fig:004 width=70%}

## Результаты упражнения

- блоков: 9;
- модель отработала 480 минут;
- кол-во одноканальных устройств: 1;
- общее количество заявок: 152;
- количество обслуженных заявок: 70;
- отработанных заявок: 69;
- среднее время обработки заявки: 6.796;
- максимум в очереди находились: 2 заявки;
- среднее время в очереди: 10.628.
- среднее время в очереди: 123.461.

# Гистограмма заявок

## Построение гистограммы

Распределение заявок в очереди

## Схема модели

![Гистограмма](image/5.png){#fig:005 width=70%}

## Схема модели

![Отчет 1](image/6.png){#fig:006 width=70%}

## Схема модели

![Отчет 2](image/7.png){#fig:007 width=70%}

## Анализ гистограммы

- блоков: 10;
- модель отработала 353.895 минут.
- кол-во одноканальных устройств: 1;
- общее количество заявок: 102;
- количество обслуженных заявок: 55;
- отработанных заявок: 53;
- среднее время обработки заявки: 6.470;
- максимум в очереди находились: 2 заявки;
- среднее время в очереди: 10.627.

# Модель 2: Два типа заказов

## Постановка задачи

В интернет-магазин к одному оператору поступают два типа заявок от клиентов - обычный заказ и заказ с оформление дополнительного пакета услуг. Заявки первого типа поступают каждые 15 +/- 4 мин. Заявки второго типа - каждые 30 +/- 8 мин. Оператор обрабатывает заявки по принципу FIFO ("первым пришел — первым обслужился"). Время, затраченное на оформление обычного заказа, составляет 10 +/- 2 мин, а на оформление дополнительного пакета услуг - 5 +/- 2 мин. Требуется
разработать модель обработки заказов в течение 8 часов, обеспечив сбор данных об очереди заявок от клиентов.

## Схема модели

![Код модели](image/9.png){#fig:009 width=70%}

## Схема модели

![Отчет модели](image/10.png){#fig:010 width=70%}

## Результаты модели

- блоков: 17;
- модель отработала 480 минут.
- кол-во одноканальных устройств: 1;
- общее количество заявок: 48;
- количество обслуженных заявок: 39;
- отработанных заявок: 1-го типа - 12, 2-го типа - 27;
- среднее время обработки заявки: 6.470;
- максимум в очереди находились: 8 заявок.
- среднее время в очереди: 34.261.

# Упражнение 2

## Описание упражнения

Модифицированная модель двух типов заказов

## Схема модели

![Код упражнения](image/11.png){#fig:011 width=70%}

## Схема модели

![Отчет упражнения](image/12.png){#fig:012 width=70%}

## Результаты упражнения

- блоков: 11;
- модель отработала 480 минут.
- кол-во одноканальных устройств: 1;
- общее количество заявок: 33;
- количество обслуженных заявок: 33;
- отработанных заявок: 32;
- среднее время обработки заявки: 11.146;
- максимум в очереди находились: 1 заявка;
- среднее время в очереди: 0.781;
- среднее количество заявок в очереди: 0.054.

# Модель 3: Четыре оператора

## Постановка задачи

В интернет-магазине заказы принимают 4 оператора. Интервалы поступления заказов распределены равномерно с интервалом 5 +/- 2 мин. Время оформления заказа каждым оператором также распределено равномерно на интервале 10 +/- 2 мин. Обработка поступивших заказов происходит в порядке очереди (FIFO). Требуется определить характеристики очереди заявок на оформление заказов при условии, что заявка может обрабатываться одним из 4-х операторов в течение восьмичасового рабочего дня.

## Схема модели

![Код модели](image/13.png){#fig:013 width=70%}

## Схема модели

![Отчет модели](image/14.png){#fig:014 width=70%}

## Результаты модели

- блоков: 9;
- модель отработала 480 минут.
- кол-во одноканальных устройств: 1;
- общее количество заявок: 93;
- количество обслуженных заявок: 91;
- отработанных заявок: 91;
- среднее время обработки заявки: 1.926;
- максимум в очереди находились: 1 заявка;
- среднее время в очереди: 0;
- среднее количество заявок в очереди: 0.

Следовательно, с 4-мя операторами очереди не было и заявки обрабатывались моментально.

# Упражнение 3

## Описание упражнения

Модифицированная модель с 4 операторами

## Схема модели

![Код упражнения](image/15.png){#fig:015 width=70%}

## Схема модели

![Отчет упражнения](image/16.png){#fig:016 width=70%}

## Результаты упражнения

- блоков: 10;
- модель отработала 480 минут.
- кол-во одноканальных устройств: 1;
- общее количество заявок: 97;
- количество обслуженных заявок: 51;
- отработанных заявок: 44;
- среднее время обработки заявки: 3.885;
- максимум в очереди находились: 3 заявки;
- среднее время в очереди: 26.253;
- среднее количество заявок в очереди: 2.789.

# Выводы

В процессе выполнения данной лабораторной работы я реализовал модель обработки заказов.

# Список источников

1. Jensen, K., Kristensen, L. M. — Lecture Notes, 2009
2. Электронная библиотека БГУ - Модели обслуживания, 2009