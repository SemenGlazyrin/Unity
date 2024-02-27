# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #5 выполнил(а):
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
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.

## Практическое задание 1
Поиск агентом объекта на сцене

Ход работы:
- Создаем новый 3Д проект в Unity и добавляем туда ML агента из данных файлов
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/emptyProject.png)

- Запускаем Anaconda Prompt

- Создаем ML-агента и устанавливаем библиотеки mlagents 0.28.0 и torch 1.7.1
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/%D1%81reateMlAgent.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/instalMlAgents.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/installTorch.png)

- В Unity создаем плоскость, куб и сферу. Также берем предложенный скрипт и подключаем его к сфере
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/RollerAgent.png)

- Также к сфере добавляем компоненты Rigidbody, Decision Requester, Behavior Parameters и настроим их так, как показано в примере
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/MoreComponents.png)

- В корень проекта добавляем yaml конфиг для нейронной сети и запускаем работу ml-агента

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/YamlConfig.png)

Выводы:
Проанализировав процесс обучения модели при использовании разного количества площадок, можно прийти к выводу, что увеличение числа копий способствует расширению возможностей модели для изучения большего количества вариантов за единицу времени, что, в свою очередь, ускоряет процесс обучения и повышает эффективность. Однако, несмотря на это, эффективность обучения модели непостоянна, важно определить, сколько времени потребуется для обучения модели при использовании 1, 3, 9 и 27 копий-площадок.

## Практическое задание 2
Симулятор добычи ресурсов

Ход работы:

- Скачиваем Unity ML-Agent_EconomicModel и запускаем проект Unity

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/economy.png)

- Изучаем проект.Как можно заметить, тут на сфере такие же компоненты, как и в практическом задании 1

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/EconomyScripts.png)

- Создаем Нового ml-агента и его виртуальное пространство

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/EconomyAgent.png)

- Запускаем и смотрим на процесс обучения

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/EconomyTest.png)

- Посмотрим в консоли результаты обучения, которые сохраняются в файле results

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/results.png)

Выводы: каждые 2000 шагов происходит удачная итерация,
на 110000 и 115000 итерация удачная, но Mean Rewards = -1.000

- Устанавливаем tensorflow

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/tensorflow.png)

- создае графики на локальном сервере с помощью специальной команды

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/graph.png)

## Задание 1
Найдите внутри C# скрипта “коэффициент корреляции” и сделать выводы о том, как он влияет на обучение модели.

коэффициент корреляции в C# скрипте

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/koeff.png)

- при коэффиценте корреляции равным 1.42, причем идеальным, так как средня награда всегда равна 1.000 и стандартное отклонение всегда равно 0, а эло начинается с 1200+ и увеличивается буквально на 0.032 эло примерно
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/results.png)

- при коэффиценте корреляции равным 5.0, средня награда всегда в диапазоне 0.75+ и до 1.0 и в среднем стандартное отклонение равно 0.512, а эло начинается около 1200 и немного уменьшается, но не слишком быстро
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/7101cbc65e832c426dab1fe3baebb0915384b21a/screens/lab5/5koef.png)

- при коэффиценте корреляции равным 10.0,средня награда уже значительно меньше, может быть равна 0.188(мин. зн.) и в среднем стандартное отклонение равно 0.8546, а эло начинается около 1200, также уменьшается, но немного быстрее
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/9a4adbb2ded2b194c4adb67675f03fc53e88f87a/screens/lab5/koef10.png)

Вывод:  коэффицент корреляции отвечает за точность обучения, также чем он меньше, тем дольше происходит обучение

## Задание 2
Изменить параметры файла yaml-агента и определить какие параметры и как влияют на обучение модели. Привести описание не менее трех параметров.

network_settings:
- normalize: Показывает, нужно ли нормализировать входные данные.(true, false)
normalize = true

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/normalize/Console.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/normalize/graph1.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/normalize/graph2.png)

Вывод:
Скачет ошибка обучения, которая в процессе уменьшается.
Дополнительные вознаграждения сначала растут, достигают максимума и уменьшаются.
Оценка внешней ценности стабильна, но на низком уровне в сравнение со стартовыми настройками, где ценность повышается со временем.
Энтропия стабильно растет.

- hidden_units: (по умолчанию = 128)
Количество узлов в скрытых слоях нейронной сети. То есть каждый скрытый слой нейронной сети имеет такое количество узлов. Если задача простая. то необходимости в большем количестве узлов в каждом слое нейронной сети не требуется.(32 - 512)
hidden_units = 32

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/hiddenUnits/Console.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/hiddenUnits/graph1.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/hiddenUnits/graph2.png)

hidden_units = 512

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/hiddenUnits/Console512.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/hiddenUnits/Graph512_1.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/hiddenUnits/Graph512_2.png)

Вывод:
Из-за сужения количества узлов в каждом скрытом слое до 32, обучение стало более быстрым, но при этом точность страдает. Наблюдается значительные колебания в ошибке обучения (Value Loss), что делает процесс обучения менее стабильным. Графики по большей части схожи. Однако, использование 512 узлов в скрытом слое существенно увеличивает время обучения. На 20000 эпохе мы получаем среднюю награду (Mean Rewards) равную -1. Оценка внешней ценности (Extrinsic value estimate) начинает уменьшаться с 20000, в отличие от ситуации с hidden_units = 32.

num_layers: (по умолчанию = 2)
Количество скрытых слоев в нейронной сети. Для простых задач нет необходимости большого количества скрытых слоев - это может быть неэффективно и долго по времени.(1-3)

num_layers = 1

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/numLayers/Console.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/numLayers/Graph1.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/numLayers/graph2.png)

num_layers = 3

![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/numLayers/Console3.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/numLayers/Graph3_1.png)
![Image alt](https://github.com/SemenGlazyrin/Unity/blob/62abfcef5c38c9be08f3275c06bd282b31b60d64/screens/lab5/numLayers/Graph3_2.png)

Вывод:
Поскольку у нас только один скрытый слой, в начале обучения значение ошибки будет максимальным, однако, по мере обучения, ошибка будет стремиться к нулю. Время обучения немного уменьшилось. Точность немного ухудшилась, из-за чего на 20000 шаге мы получаем среднюю награду (mean rewards) < 0. Графики в целом похожи. При num_layers = 3 значительно увеличивается время обучения, при этом стандартное отклонение в среднем выше, чем при num_layers = 1. Дополнительные вознаграждения (Extrinsic Rewards) неустойчивы.

## Задание 3
Приведите примеры, для каких игровых задачи и ситуаций могут использоваться примеры 1 и 2 с ML-Agent’ом. В каких случаях проще использовать ML-агент, а не писать программную реализацию решения?

### Пример 1:
StarCraft II
- Игровая задача: Обучение искусственного интеллекта для игры в стратегическую игру StarCraft II.
- Ситуация: ML-Agent используются для обучения компьютерных противников или союзников в различных сценариях игры.

### Пример 2:
OpenAI Five в Dota 2:
- Игровая задача: Создание команды ботов, способных играть в Dota 2 против профессиональных команд.
- Ситуация: ML-Agent'ы обучались в рамках проекта OpenAI Five и участвовали в матчах против топовых профессиональных команд, демонстрируя высокий уровень игры.

ML-агента проще использовать тогда, когда игрок совершает много действий и к ним требуется адаптация. Также проще использовать уже готовый алгоритм, а не писать новый, что существенно сократит время разработку игры. Но есть случаи, когда ML-агент вовсе не требуется, и использовать более простые алгоритмы будет гораздо правильнее и логичнее.

## Выводы
Изучил программне средства для создания системы машинного обучения и ее интеграции в Unity
Освоил создание виртуальной среды для ML-Agent и интеграцию ML-Agent с Unity
Визуализировал данные с использованием библиотеки TensorFlow
