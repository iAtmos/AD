# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #5 выполнил(а):
- Азеев Борис Михайлович
- АТ210950
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | # | 20 |
| Задание 3 | # | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.

## Задание 1
### Измените параметры файла. yaml-агента и определить какие параметры и как влияют на обучение модели.
- Изначально была осуществелна настройка среды, в которой будет происходить дальнейшее изучение экономической модели, основанной на алгоритме mlagenta, который учитывает ряд параметров при обучение. А так же осуществленно обучение с первичными параметрами (1/5) на основе 50.000 итераций.
![image](https://user-images.githubusercontent.com/114149527/205102984-26d466af-605c-4b8c-ad6d-5167c52e3052.png)
![image](https://user-images.githubusercontent.com/114149527/205111409-7a0c6ec8-1fff-4174-8e10-7f9edf5b829c.png)

- Изменение 1 (замедление персонажа относительно добычи руды и уменшьение разброса показателей). Предположение: возникнет обратная корреляция графиков в пользу Economicy, поскольку игрок будет добыватьи доставлять золото с меньшей эффективностью. Осуществленно 50.000 итераций.

      speedMove = Mathf.Clamp(actionBuffers.ContinuousActions[0], 1.5f, 6f);
      Debug.Log("SpeedMove: " + speedMove);
      timeMining = Mathf.Clamp(actionBuffers.ContinuousActions[1], 1f, 4f);



## Выводы

Данная работа наглядно демонстрирует, что при построение линейной регресси для увеличения точности результата, крайне важно колличество иттераций (опытов) с приминением алгоритмов (в нашем случае методов) выравнивающих показатели и приводящих их к общему значению путем математически-физических преобразований.

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
