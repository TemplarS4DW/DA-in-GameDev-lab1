# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнил:
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
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.

## Задание 1
### Вывести "Hello World!" на Unity и Python.
- Для воспроизведения "Hello World!" на языке Python выбран google.colab, где писалась программа. Всё это выглядит так: 
![python1](https://user-images.githubusercontent.com/104576932/192353227-ba0123df-de86-4150-b724-7ffd3dc107df.jpg)
![python2](https://user-images.githubusercontent.com/104576932/192353243-090a2612-1c51-49b7-adbe-e347d6e4f1bb.jpg)

- На Unity был создан проект, где был создан Empty Object. Далее в assets создан C# Script, который позже был связан с Empty Object. При запуске снизу слева был выведен "Hello World!", весь код C# Script находится справа: 
![HelloWorld-Unity](https://user-images.githubusercontent.com/104576932/192353595-6504fd63-4a30-41a2-8235-14e092986a3f.jpg)
```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class NewBehaviourScript : MonoBehaviour
{
    void Start()
    {
        Debug.Log("Hello World!");
    }
}
```


## Задание 2
### В разделе "Ход работы" пошагово выполнить каждый пункт с описанием и примером реализации задачи по теме лабораторной работы
Ход работы:
- 1. Произвести подготовку данных для работы с алгоритмом линейной регрессии. 10 видов данных были установлены случайным образом, и данные находились в линейной зависимости. Данные преобразуются в формат массива, чтобы их можно было вычислить напрямую при использовании умножения и сложения.

```py
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
x = [3,21,22,34,54,34,55,67,89,99]
x = np.array(x)
y = [2,22,24,65,79,82,55,130,150,199]
y = np.array(y)

plt.scatter(x,y)
```
- Для решения данной задачи также использован google.colab
![image](https://user-images.githubusercontent.com/104576932/192355041-14d1afe6-a3ed-4216-b14c-8ca2a2cd7a19.png)

- 2. Теперь определим следующие связанные функции: 1) Функция модели: определяет модель линейной регрессии wx+b. 2) Функция потерь: функция потерь среднеквадратичной ошибки. 3) Функция оптимизации: метод градиентного спуска для нахождения частных производных w и b.
- Функция модели: определяет модель линейной регрессии wx+b.
```py
def model(a, b, x):
    return a*x + b
```
- Функция потерь: функция потерь среднеквадратичной ошибки.
```py
def loss_function(a, b, x, y):
    num = len(x)
    prediction = model(a,b,x)
    return (0.5/num) * (np.square(prediction - y)).sum()
```
- Функция оптимизации: метод градиентного спуска для нахождения частных производных w и b.
```py
def optimize(a, b, x, y):
    num = len(x)
    prediction = model(a, b, x)
    da = (1.0/num) * ((prediction - y) * x).sum()
    db = (1.0/num) * ((prediction - y).sum())
    a = a - Lr * da
    b = b - Lr * db
    return a, b
```
![image](https://user-images.githubusercontent.com/104576932/192357522-e8cd0782-cecb-48c1-9166-570682cc24e9.png)

- 3. Итерация
![image](https://user-images.githubusercontent.com/104576932/192359852-bb9d2388-4c02-43a6-8a77-649e27286f4c.png)

## Задание 3
### Должна ли величина loss стремиться к нулю при изменении исходных данных? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ.
- Значение loss будет стремиться к нулю при изменении исходных данных, ведь при увеличении количества итераций loss уменьшается. 

При 1 итерации loss = 4633.537149299337
![task3](https://user-images.githubusercontent.com/104576932/192366064-f513f22f-3682-40a4-8024-9f324440286f.png)

При 100 итераций loss = 1870.9544863091703
![task3(1)](https://user-images.githubusercontent.com/104576932/192365809-436e7354-c5b1-497b-90b4-2b44901493cc.png)

При 100000 итераций loss = 190.47390666194988
![task3(2)](https://user-images.githubusercontent.com/104576932/192365855-28c11959-7c1d-4734-afa2-4efdeec747ff.png)

### Какова роль параметра Lr? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ. В качестве эксперимента можете изменить значение параметра.

- Роль параметра Lr заключается в том, что чем больше параметр Lr, тем больше угол наклона графика больше. 

При Lr = 0.000001
![task3(Lr-1)](https://user-images.githubusercontent.com/104576932/192367487-c1fc7b64-90c2-4e2c-953f-64d67c309f9b.png)

При Lr = 0.001
![task3(Lr-2)](https://user-images.githubusercontent.com/104576932/192367503-c7ffd399-61f5-4068-835b-f8100fbc9a00.png)

## Выводы

Я ознакомился с основными операторами языка Python на примере реализации линейной регрессии. В ходе проведённой лабораторной работы были написаны программы с выводом "Hello World!" в Unity и Google.Colab. Познакомившись с алгоритмом линейной регрессии, я определил связанные функции: функции модели, функции потерь, функции оптимизации. Также мною были проведены небольшие опыты с исходными данными и выявлены их зависимости, например у loss, Lr.

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
