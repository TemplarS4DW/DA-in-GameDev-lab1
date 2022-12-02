# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #5 выполнил:
- Савватеев Даниил Владимирович
- РИ-210910
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 80 |
| Задание 2 | # | 20 |

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
Работа с ML Agents

## Задание 1
### 
Для начала пришлось восстанавливать ML Agents в пакетиках, а также доставать Анаконду и подготовить виртуальную среду для работы.
![image](https://user-images.githubusercontent.com/104576932/205335472-ad832cb1-8396-4fcf-94b8-3d0405a40a0d.png)

Все результаты записаны в Economic.yaml. Но далее нужно будет поставить TensorBoard для вывода результатов в красивых графиках. 
![image](https://user-images.githubusercontent.com/104576932/205338484-066206cd-2a2f-47f9-a1fd-44dccf6048c3.png)

Ну теперь он скачен, копируем выданную ссылку и вставляем в браузер. 
![image](https://user-images.githubusercontent.com/104576932/205350362-a703ad07-78bc-498b-8589-7d270faaf91e.png)


А теперь наша задача заключается в смене параметров yaml-агента и определение параметров, а так же как они влияют на обучение, чтобы вот всё было хорошо.

1) Поменяем epsilon с 0.2 на 0.1
![image](https://user-images.githubusercontent.com/104576932/205353561-97f504ea-255b-4c36-9662-3348b29fa32b.png)

Epsilon нужен для расчёта скорости развития политики в процессе обучения.

2) Попробуем ещё поменять batch_size с 1024 на 512
![image](https://user-images.githubusercontent.com/104576932/205354096-f1838620-7e00-4917-9479-d030878a8b2d.png)

Batch_size отвечает за количество опытов в каждой итерации градиентного спуска.

3) Теперь поменяем значение lambd с 0.95 до 0.9 
![image](https://user-images.githubusercontent.com/104576932/205354616-39790290-9351-4054-8935-a5e63e8b6010.png)

lambd используется для расчётов общей оценки преимущества GAE.

4) num_epoch увеличим с 3 до 5
![image](https://user-images.githubusercontent.com/104576932/205355157-a9e4ae76-df67-4d3c-aa75-3b4457a9607c.png)


num_epoch показывает количество проходов через буфер опыта при оптимизации градиентного спуска.


## Задание 2
### 

## Задание 3
### 

## Выводы
Пока ничего

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
