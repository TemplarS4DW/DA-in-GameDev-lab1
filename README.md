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
### Какова роль параметра Lr? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ. В качестве эксперимента можете изменить значение параметра.

- Перечисленные в этом туториале действия могут быть выполнены запуском на исполнение скрипт-файла, доступного [в репозитории](https://github.com/Den1sovDm1triy/hfss-scripting/blob/main/ScreatingSphereInAEDT.py).
- Для запуска скрипт-файла откройте Ansys Electronics Desktop. Перейдите во вкладку [Automation] - [Run Script] - [Выберите файл с именем ScreatingSphereInAEDT.py из репозитория].

```py

import ScriptEnv
ScriptEnv.Initialize("Ansoft.ElectronicsDesktop")
oDesktop.RestoreWindow()
oProject = oDesktop.NewProject()
oProject.Rename("C:/Users/denisov.dv/Documents/Ansoft/SphereDIffraction.aedt", True)
oProject.InsertDesign("HFSS", "HFSSDesign1", "HFSS Terminal Network", "")
oDesign = oProject.SetActiveDesign("HFSSDesign1")
oEditor = oDesign.SetActiveEditor("3D Modeler")
oEditor.CreateSphere(
	[
		"NAME:SphereParameters",
		"XCenter:="		, "0mm",
		"YCenter:="		, "0mm",
		"ZCenter:="		, "0mm",
		"Radius:="		, "1.0770329614269mm"
	], 
)

```

## Выводы

Абзац умных слов о том, что было сделано и что было узнано.

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
