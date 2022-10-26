# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнил:
- Савватеев Даниил Владимирович
- РИ-210910
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

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
познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.

## Задание 1
### Реализовать систему машинного обучения в связке Python - Google-Sheets – Unity. При выполнении задания можно использовать видео-материалы и исходные данные, предоставленные преподавателями курса.

1) Создан проект 3D Unity, скачана папка с ML агентом, в будущем которая будет импортирована в проект.
![3 1](https://user-images.githubusercontent.com/104576932/198135263-f34fa4d6-b898-4efc-aab2-f5ce8cae0a98.png)

2) Казалось бы, на этом лабораторная работа завершена, да вот нет. Далее нужно запустить Anaconda Prompt через права администратора и произвести парочку команд для скачивании библиотеки и не только. После установки библиотек, активации и настройки пути наша строчка теперь выглядит так:
![image](https://user-images.githubusercontent.com/104576932/198135578-6a8385d8-71d3-461f-aed4-6043d6220c0c.png)

3) Размещаем на нашей сцене Plane, Sphere и Cube, а так же создаём C#-скрипт для нашей сферы, добавляя ей компоненты Rigidbody, Decision Requester,
Behavior Parameters.

C#-скрипт:
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody;
    void Start()
    {
        rBody = GetComponent<Rigidbody>();
    }

    public Transform Target;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }

        Target.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
    }
    public override void CollectObservations(VectorSensor sensor)
    {
        sensor.AddObservation(Target.localPosition);
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(rBody.velocity.x);
        sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        Vector3 controlSignal = Vector3.zero;
        controlSignal.x = actionBuffers.ContinuousActions[0];
        controlSignal.z = actionBuffers.ContinuousActions[1];
        rBody.AddForce(controlSignal * forceMultiplier);

        float distanceToTarget = Vector3.Distance(this.transform.localPosition, Target.localPosition);

        if(distanceToTarget < 1.42f)
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
```
Наша абстракция выглядит теперь таким образом:
![image](https://user-images.githubusercontent.com/104576932/198136396-3bc22cbf-2466-40bb-a5d2-81546a6be81b.png)


4) Теперь мы запускаем ML-агента и возвращаемся в юнити, чтобы посмотреть на наш результат. Шарик чуть ли не летает и не улетает с нашей плоскости.
![image](https://user-images.githubusercontent.com/104576932/198137383-40a45edb-5f1e-456c-89b4-e4f4e6d481cc.png)

5) Теперь же создадим копии нашего изобретения в 3, 9, 27, а то и более штук:
![image](https://user-images.githubusercontent.com/104576932/198138124-7b8ca912-5c2e-4382-95d1-28c66f1d8395.png)
![image](https://user-images.githubusercontent.com/104576932/198138424-04677b83-ec41-44ba-8378-d41399650783.png)

6) Теперь же мы добавим полученную RollerBall-модель в Behavior Parameters и посмотрим на наш результат:
![image](https://user-images.githubusercontent.com/104576932/198138924-de33d58e-8ff5-4f1e-9ac5-508e16999b9b.png)
** Он двигается плавно и аккуратно **

Вывод по первому заданию: Наша модель обучается куда быстрее, когда стоит как можно больше моделей нашей конструкции для достижения нашей моделькой куба.


## Задание 2
### 

## Задание 3
### 

## Выводы

Пока без них.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
