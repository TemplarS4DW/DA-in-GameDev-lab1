# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил:
- Савватеев Даниил Владимирович 
- РИ-210910
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
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
### Реализовать совместную работу и передачу данных в связке Python - Google-Sheets – Unity.
1. Я подключил API для работы с Google Sheets и Google Drive.
![image](https://user-images.githubusercontent.com/104576932/195158521-5e05fc42-5c32-47bc-8ff1-5cfbd1ab35c8.png)

2. Также реализована запись данных из скрипта на Python в Google таблицу.
![image](https://user-images.githubusercontent.com/104576932/195159016-c766e2e4-e198-4cbd-b225-0ea759ed0b5c.png)
![image](https://user-images.githubusercontent.com/104576932/195159099-97adf91f-fd4a-49e0-885e-762f61e12784.png)

3. Также для дальнейшего полученя данных из Google таблицы в Unity был создан, как ни странно или странно, проект на Unity.
Это Unity. Красивое...
![image](https://user-images.githubusercontent.com/104576932/195159527-b4669844-a410-4f9c-8da4-9ef940210208.png)

4. А так же создан функционал, благодаря которому оно умеет теперь понимать, какой файл воспроизвести, исходя из полученных данных. 
![image](https://user-images.githubusercontent.com/104576932/195160201-92ede5f5-34c8-4534-b9e2-f744e4e020c3.png)
![image](https://user-images.githubusercontent.com/104576932/195160312-84868de3-8c98-4be9-bc25-a4dcf5ef9e97.png)
![image](https://user-images.githubusercontent.com/104576932/195160388-183b035d-37ff-4574-b85d-d3670207fa51.png)

Первая задача выполнена.

## Задание 2
### Реализовать запись в Google таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы №1
Здесь мы воспользуемся кодом из 1-ой лабораторной работы для решения второго задания. Ниже тут картиночки с кодом.
![image](https://user-images.githubusercontent.com/104576932/195166057-d7f7494c-68ec-4bf1-9e3a-6c8bba780188.png)
![image](https://user-images.githubusercontent.com/104576932/195166094-98a47cc8-1672-4ca7-b804-9e29a8f5654e.png)

Соответственно и поменялись числа в таблице, а значит и новые данные на обед для Unity.
![image](https://user-images.githubusercontent.com/104576932/195166219-027bc0fb-94d4-438e-8632-85ff3e27b469.png)

Вторая задача выполнена.

## Выводы
Я познакомился с программными средствами для организции передачи данных между инструментами Google, Python и Unity.

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
