# Школа Программистов HeadHunter

##1. Медиана
Даны два отсортированных числовых массива одинаковой длины N. Найдите медиану числового массива длины 2N, содержащего все числа из двух данных массивов.

```
Пример входных данных:
1 2 3 4
1 4 5 6
```

```
Пример выходных данных:
3.5
```

##2. Бесконечная последовательность
Возьмём бесконечную цифровую последовательность, образованную склеиванием последовательных положительных чисел: S = 123456789101112131415...
Определите первое вхождение заданной последовательности A в бесконечной последовательности S (нумерация начинается с 1).

```
Пример входных данных:
6789
111
```

```
Пример выходных данных:
6
12
```

## Решения

###1. Медиана (t1_median.py)

Основная идея решения заключается в том, что медиана отсортированного массива не изменится, если массив
укоротить слева и справа на одинаковое количество элементов.

Для двух отсортированных массивов одинакового размера проверяется соотношение их левых медиан, и затем массивы 
соответствующим образом укорачиваются, пока массивы не будут состоять из двух элементов.
Например, для массивов `a` и `b`, медиана первого массива `a_m`, медиана второго `b_m`:
если `a_m >= b_m `, то можно из массива `a` вычеркнуть все элементы правее медианы, а из массива `b`
столько же элементов с начала массива.

Когда в массивах останется по два элемента, то находится медиана массива из 4-х элементов, которая равна полусумме
вторго и третьего элементов.

####Использование

*python t1_median.py filename*

В нечетной строке файла (начиная с 1) должны располагаться элементы массива `a` (разделенные пробелом) 
до конца строки.
В четной строке файла элементы для массива `b`.
Количество элементов должно быть одинаково. Пример входных данных: `data1.txt`.

Результат работы программы: вывод на печать  n - медиан, вычисленных для 2n валидных строк входного файла.
Если имя файла не указано, программа пытается открыть файл `data1.txt`, лежащий в той же папке.
В случае ошибок чтения файла будет выведена медиана массивов из условия:
```
1 2 3 4
1 4 5 6
```



###2. Бесконечная последовательность (t2_sequence.py)

Основная идея решения заключается в том, что заданная последовательность чисел `A` встречается в 
 последовательности `S` бесконечное количество раз, а также в том, что  позицию вхождения можно вычислить
  из самой последовательности `A` без генерации последовательности `S`.

Поиск вхождения начинается с однозначного числа равного `A[1]`, если последовательность `A`  не начинается
 с числа `A[1]`, то поиск продолжается среди двухзначных чисел и так далее пока не будет найдено 
 вхождение или количество знаков превысит количество знаков заданной последовательности `A`.
 Особенность расположения первого символа `A[1]` такова, что он может располагаться не только в начале 
 стартовой позиции, но и может быть сдвинут, поэтому также проверяется сдвинутая стартовая позиция. 
 Из всех найденных позиций выбирается минимальная.
 Например, для 3-х значного числа 223 алгоритм такой:

 - Проверка по одной цифре (2 2 3) ['2' '3' '4'] не проходит.
 - Проверка по двум цифрам (22 3) ['22 2'3] не проходит.
 - Сдвиг на 1 символ (2 23) [2'2 23'] проверка успешная.
 - Завершение. Позиция последовательности `A = 223` равна позиции числа 22 (34)
 плюс сдвиг (1). Результат: 35.

####Использование

*python t2_sequence.py*

После запуска программа попросит ввести число (последовательность цифр) для нахождения 
его позиции в бесконечной последовательности '123456789101112...'. Введите число и нажмите "Enter".

Результат работы программы: вывод на печать найденного первого вхождения заданого числа в бесконечной
 последовательности.
 Для завершения программы нажмите CTRL-C или введите не число.
