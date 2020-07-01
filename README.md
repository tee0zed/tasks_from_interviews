# tasks_from_interviews

## and solving

### max_subarray

Найдите непрерывный подмассив в массиве (содержащем как минимум 1 элемент), который имеет максимальную сумму элементов.
Пример: [-1, -13, -2, 1, -3, 4, -1, 2, 1, -5, 4] должно вернуть [4, -1, 2, 1].

```
def max_subarray(array)
  (2..array.size-1).map { |window_size|
    array.each_cons(window_size).inject { |a, b| a.sum > b.sum ? a : b }
  }.max_by(&:sum)
end 
```
