# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнил(а):
- Глазырин Семён Дмитриевич
- РИ220933
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

## Цель работы
Разработать оптимальный баланс для десяти уровней игры Dragon Picker

## Задание 1
### Предложите вариант изменения найденных переменных для 10 уровней в игре. Визуализируйте изменение уровня сложности в таблице.
Изучив прототип, можно заметить, что на движение дракона влияют скорость, диапазон значений в котором они движется и вероятность, что он поменяет направления,

На сбрасывание яиц влияет время, которое проходит между их сбрасыванием.
Следовательно, изменив эти перемнные, мы изменим уровень сложности игры.  
  
Например:  
- Увеличить скорость дракона
- Увеличить диапазон значений в пределах, которых передвигается дракон
- Увеличить вероятнсть изменения направления дракона
- Уменьшить время между сбрасыванием яиц


![Image alt](https://github.com/SemenGlazyrin/Unity/blob/4f59bcb7339f4af731d10254e3ca8d846713709f/screens/lab3/tabl.png)
https://docs.google.com/spreadsheets/d/1Hhs_GSceKCQYnqOy_on-FshoKJPP8UZ_4XC4_JgYafY/edit?usp=sharing

## Задание 2
### Создайте 10 сцен на Unity с изменяющимся уровнем сложности.
####Ход работы:
- Открываем проект DrakonPicker
- Добавляем новые сцены, меняя значения переменных

Создаем 10 копий первого уровня и меняем значения переменных на те, что представлены в таблице

https://github.com/SemenGlazyrin/DragonWith10Levels

## Задание 3
### Заполнить google-таблицу данными из Python. В Python данные также должны быть визуализированы.
####Ход работы:
- В Jupyter Notebook напишем код для подключения к гугл таблице
- Заполним и визуализируем её

```py
import numpy as np
import time
import gspread
import matplotlib.pyplot as plot

gc = gspread.service_account(filename='marine-defender-408211-2136c6471e80.json')
sh = gc.open("Game")

time.sleep(10)

speed = 4
time_between_egg_drops = 2
left_right_distance = 10
chance_direction = 0.01

list = []
list_of_speed = []
list_of_time = []
list_of_distance = []
list_of_chance = []

n = [i for i in range(1, 12)]

for i in range(11):
    sh.sheet1.update(('A' + str(i + 2)), i + 1)
    sh.sheet1.update(('B' + str(i + 2)), speed)
    sh.sheet1.update(('C' + str(i + 2)), time_between_egg_drops)
    sh.sheet1.update(('D' + str(i + 2)), left_right_distance)
    sh.sheet1.update(('E' + str(i + 2)), chance_direction)
    
    list.append([speed, time_between_egg_drops, left_right_distance, chance_direction])
    list_of_speed.append(speed)
    list_of_time.append(time_between_egg_drops)
    list_of_distance.append(left_right_distance)
    list_of_chance.append(chance_direction)
    
    speed += 3
    time_between_egg_drops -= 0.16
    left_right_distance += 2
    chance_direction += 0.001

plot.title('Скорость дракона', fontsize = 20)
plot.plot(n, list_of_speed)

plot.xlabel("Уровень")
plot.xticks(n)
plot.show()

plot.title('Время между сбрасыванием яиц', fontsize = 20)
plot.plot(n, list_of_time)

plot.xlabel("Уровень")
plot.xticks(n)
plot.show()

plot.title('Диапазон движения дракона', fontsize = 20)
plot.plot(n, list_of_distance)

plot.xlabel("Уровень")
plot.xticks(n)
plot.show()

plot.title('Вероятность поменять направление', fontsize = 20)
plot.plot(n, list_of_chance)

plot.xlabel("Уровень")
plot.xticks(n)
plot.show()

bw = 0.2
index = np.arange(1, 12)

plot.title('Динамика изменений уровней сложности', fontsize = 20)

plot.bar(index, list_of_time, bw, color = 'b')
plot.bar(index + bw, list_of_speed, bw, color = 'g')
plot.bar(index + 2 * bw, list_of_distance, bw, color = 'r')
plot.bar(index + 3 * bw, list_of_chance, bw, color = 'yellow')

plot.xticks(index + 1.5 * bw, np.arange(1, 12))
plot.xlabel("Уровень")

plot.show()
```

Графики:

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/480ddeb396ea80cb368ec026bdc7b13b9f53f6b2/screens/lab3/changeDir.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/480ddeb396ea80cb368ec026bdc7b13b9f53f6b2/screens/lab3/dir.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/480ddeb396ea80cb368ec026bdc7b13b9f53f6b2/screens/lab3/speed.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/480ddeb396ea80cb368ec026bdc7b13b9f53f6b2/screens/lab3/timeBtw.png)

## Выводы
Изучил прототип игры, выявил переменные, которые меняются. Создал таблицу, отражающую динамику изменений уровней сложности игры. Настроил оптимальный баланс для десяти уровней в игре "Dragon Picker".