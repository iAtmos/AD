# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил(а):
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
Познакомиться с программными средствами для организции передачи данных между инструментами google, Python и Unity

## Задание 1
### Реализовать совместную работу и передачу данных в связке Python - Google-Sheets – Unity. При выполнении задания используйте видео-материалы и исходные данные, предоставленные преподавателя курса.
 - Согласно последовательности методички и приложенных материалов было выполнено: создание новых проектов и установка связи между Google Sheet, Python и Unity
![image](https://user-images.githubusercontent.com/114149527/194495488-846ddf47-fb5e-45b8-ad24-9c3b504c40b3.png)
![image](https://user-images.githubusercontent.com/114149527/194495589-1920f35c-8398-438f-bd49-f8f53864be29.png)
![image](https://user-images.githubusercontent.com/114149527/194495676-391f1d15-fb8a-4138-a5a2-ee540b389bc5.png)
 - Реализован алгоритм изменения инфляции с выводом соответствующих звуковых дорожек
![image](https://user-images.githubusercontent.com/114149527/194496219-0b701ead-5d37-4c5f-8e7b-4639e4d21c0e.png)
![image](https://user-images.githubusercontent.com/114149527/194496311-428544ce-9939-4e4c-9ef8-6d489d54cb65.png)



## Задание 2
### В разделе "ход работы" пошагово выполнить каждый пункт с описанием и примером реализации задачи по теме лабараторной работы.
Описание работы:
 - Пошагово выполненны инструкции, приложенные к работе. Суть данного алгоритма заключается в построение графика(линии) с учетом различных отклонений по модели линейной регресии с учетом колличества итераций. Их колличество влияет на точность построения линейной фушкции wx+b. Чем больше осуществляется проходов по алгоритму, которые задаются в строке "a, b = iterate(a, b, x, y, 10)" (16) тем более случайные значения приближаются к заданным a, b -> x, y. А коэффициент Lr влияет на создаваеммое отклонение случайных переменных (a, b). Следовательно, при его увеличение сокращается и колличество требующихся итераций для выстраивания графика, приближенного к значениям x, y.
![image](https://user-images.githubusercontent.com/114149527/191891087-08ca4fcc-46b9-4024-90b5-272b4a1f3c2c.png)
![image](https://user-images.githubusercontent.com/114149527/194496297-77769e17-d666-4bb7-b43f-53843e22c637.png)

## Задание 3
### Изучите код на Python и ответть на вопросы:
 1. Должна ли величина loss стремиться к нулю при изменении исходных данных? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ.
 - В теории, значение колличества итераций, сллучайно генерируемые значение (a, b), коэффициент Lr, размерность массива x при своем увеличение значения приводят к уменьшению величины loss, но лишь до определенного момента. Если многократно увеличивать вышеизложенные значения - это приведет к невозможности построения линейного графика. Следовательно, наиболее разумное решение, для максимального уменьшения величины los - увеличить колличество элементов массива x ->  ∞. Но это так же разрушает принципы работы алгоритма. Следовательно, величину los нельзя приблизить к (≈0) не разрушив целостности данного алгоритма. Два скриншота показывающих все же возможное уменьшения значения los путем некритичного изменения величин переменных:
![Group 2](https://user-images.githubusercontent.com/114149527/191895359-277f492a-41f0-4cfb-be6b-2920ab7f1e0d.png)
![Group 3](https://user-images.githubusercontent.com/114149527/191895521-b83473e9-bf36-4d7b-9d9f-32dc2be87b12.png)
 2. Какова роль параметра Lr? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ. В качестве эксперимента можете изменить значение параметра.
 - Пармаетр Lr в данном алгоритме выступает в роли коэффициента, влияющего на значения (a, b) в зависимости от колличества итераций. Чем больше его значение, тем меньше итераций требуется для приближения строящейся линейной функции к значениям точек (x, y). Но, его многократное увеличение может привисти к выходу из строя всего алгоритма! Так же, изменение значений параметра Lr приводит к искажению значения функции los при фиксированном сравнение (a, b - не случайное число, а поястоянное). Скриншоты, показывающие изменение значения Lr с фиксированными итерациями и плавающими (a, b - согласно заданию изменять модно лишь Lr).
![Group 4](https://user-images.githubusercontent.com/114149527/191896676-a5efd1d5-2698-4e5e-b9d8-df56c0ddba90.png)
![Group 5](https://user-images.githubusercontent.com/114149527/191896682-39084e5a-a011-474e-b320-f244dcf16ba9.png)

## Выводы

Данная работа наглядно демонстрирует каким образом можно устанавливать взаимосвязь между различными сервисами, выгружать/изменять данные и использовать их уже на других платформах.

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
