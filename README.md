# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнил(а):
- Азеев Борис Михайлович
- hb-210950
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
Познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.

## Задание 1
### Реализовать систему машинного обучения в связке Python - Google-Sheets – Unity. При выполнении задания можно использовать видео-материалы и исходные данные, предоставленные преподавателями курса.
- Используя терминал anaconda создаем изолированное пространство TestAgentб в котором устанавливаем пакеты thorch версии 1.7.1 и mlagents 0.28.0 соотвественно.
![Снимок экрана 2022-11-07 094127](https://user-images.githubusercontent.com/114149527/200232737-a025528c-fd02-4ac5-a30f-df8344945740.png)
- После этего создаем новые проект в Unity к которому через Windows Package Manager подключаем mlagents и формируем базовые обьекты - цель, за которой будет следовать RollerAgent и самого RollerAgent. К RollerAgent подключаем компаненты физики (Rigidbody), Behavior Requester и Behavior Parmeters. Создаем новый скрипт.
 
#code
    
    public class RollerAgent : Agent
    {
        private Rigidbody rBody;
        void Start()
        {
            rBody = GetComponent<Rigidbody>();
        }

        public Transform Target; // Положение цели

        public override void OnEpisodeBegin()
        {
            if (this.transform.localPosition.y < 0)
            {
                this.rBody.angularVelocity = Vector3.zero; // Сброс текущего движения
                this.rBody.velocity = Vector3.zero; // Вектор скорости
                this.transform.localPosition = new Vector3(0, 0.5f, 0); // Изначальная позиция
            }

            Target.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4); // Расположение кубика
        }

        public override void CollectObservations(VectorSensor sensor) // Сбор параметровм при обучение
        {
            sensor.AddObservation(Target.localPosition); // Передача позиции куба
            sensor.AddObservation(this.transform.localPosition); // Передача нашей позиции
            sensor.AddObservation(rBody.velocity.x); // Вектор скорости x
            sensor.AddObservation(rBody.velocity.z); // Вектор скорости z
        }

        public float forceMultipler = 10;
        public override void OnActionReceived(ActionBuffers actionsBuffer)
        {
            Vector3 controlSignal = Vector3.zero;
            controlSignal.x = actionsBuffer.ContinuousActions[0];
            controlSignal.z = actionsBuffer.ContinuousActions[1];
            rBody.AddForce(controlSignal * forceMultipler);
            float distanceToTaget = Vector3.Distance(this.transform.localPosition, Target.localPosition);

            if (distanceToTaget < 1.42f)
            {
                SetReward(1.0f);
                EndEpisode();
            }
            else if (this.transform.localPosition.y < 0)
            {
                EndEpisode();
            }
        }
    }

#code
- Скрипт состоит из трех основных переназныченных методов. Метод OnEpisodeBegin() содержит в себе инструкции при страте первого эпизода (устанавливает положение RollerAgenta и его характеристики скорости, создает случайную локацию цели). Во втором методе CollectObservations(VectorSensor sensor) мы отслеживаем получемыех параметры в процессе нашего обучения. А третий метод отвечает за перемецение RollerAgenta к цели с последующим перезапуском эпизода с возможным вознагрождением. После, проводим серию обучений.
![image](https://user-images.githubusercontent.com/114149527/200236039-42c8769f-6afb-4fba-8acf-efef5ae45dc6.png)
- Для ускорения, созданную платформу с целью и агентом помещаем в prefab и кланируем несколько раз.
![image](https://user-images.githubusercontent.com/114149527/200236329-6b881b09-4688-4714-ad84-8a6b6ff04c33.png)
- После учпешного обучения, в папке с configom создается обученая сетка передвжения RollerAgenta, которую мы переносим в Unity прокет и помещаем в поле Model.
![image](https://user-images.githubusercontent.com/114149527/200236642-7b8f7175-e463-4a94-8a39-761ad73164ab.png)


## Выводы


## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
