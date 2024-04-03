# Домашнее задание 4

## Тема: использование основных статистических тестов и поправок на множественные сравнения

### Цель

Разберем использование основных параметрических и непараметрических статистических тестов, научимся вводить поправки на множественные сравнения и поймем, чем они отличаются.

### Описание ДЗ

Выполните перечисленные задания.

#### Задание 1 (2 балла)

Рассмотрите следующую статистическую гипотезу:

> Проводят некоторое исследование пациентов с артериальной гипертензией. Предположим, что внедрение нового препарата в среднем лучше снижает их давление по сравнению со стандартной терапией.

1. Задайте seed для воспроизводимости результатов (`set.seed()`).
2. Задайте размер выборки `sample_size <- 30`.
3. Задайте значение среднего артериального давления до приема нового препарата и после.

Затем:

- Сформулируйте нулевую и альтернативную гипотезы.
- Определите уровень значимости.
- Выберите статистический тест для проверки гипотезы и аргументируйте свой выбор.
- Определите наблюдаемое значение статистики, а также критическое значение статистики.
- Оцените и прокомментируйте статистическую значимость.

#### Задание 2 (2 балла)

Рассмотрите следующую статистическую гипотезу:

> Существует некоторая связь между курением и развитием рака легких. Пусть у курящих людей вероятность заболеть раком легких составляет 0.8, а у некурящих — 0.2.

Рассмотрите два случая: для выборки `sample_size1 <- 100` и выборки `sample_size2 <- 30`. Сгенерируйте данные по курению с помощью функции `rep()`, пусть отношение числа курящих к некурящим в каждой выборке составляет 1:1.

Затем:

- Сформулируйте нулевую и альтернативную гипотезы.
- Определите уровень значимости.
- Выберите статистический тест для проверки гипотезы и аргументируйте свой выбор.
- Определите наблюдаемое значение статистики, а также критическое значение статистики.
- Оцените и прокомментируйте статистическую значимость.

#### Задание 3 (3 балла)

Рассмотрите следующую статистическую гипотезу:

> Применение нового метода лечения синдрома раздраженного кишечника значимо меняет уровень болевых симптомов по сравнению с группой, прошедшей лечение диетотерапией.

Исследователь избегает любых допущений, кроме того, что выборки независимы и имеют одинаковое распределение.

Что нужно сделать:

- Сформулируйте нулевую и альтернативную гипотезы.
- Определите уровень значимости.
- Выберите статистический тест для проверки гипотезы и аргументируйте свой выбор.
- Определите наблюдаемое значение статистики, а также критическое значение статистики.
- Оцените и прокомментируйте статистическую значимость.

#### Задание 4 (4 балла)

Рассмотрите следующую гипотезу:

> Проводится исследование, в котором исследуются три противоопухолевые препарата A, B, и плацебо (0) на трех группах мышей. В каждой из трех групп по 10 мышей. Оценивается размер опухоли у мыши.

Сгенерируйте датасет следующим образом:

```R
tumor <- tibble(
  therapy = c(rep("0", 10), rep("A", 10), rep("B", 10)),
  value = c(rep(3213, 10), rep(2687, 10), rep(2423, 10))
) %>%
  mutate(therapy = factor(therapy, levels = c("0", "A", "B")))
tumor$value <- tumor$value + rnorm(30, 0, 760)
```

Постройте на одном графике три «ящика с усами» для наглядности.

- Проведите дисперсионный анализ, чтобы выяснить, есть ли разница между размером опухоли во всех группах. 
- Прокомментируйте получившийся результат.
- С помощью функции TukeyHSD() проведите попарные сравнения, используя критерий Тьюки.
- Прокомментируйте полученные результаты.