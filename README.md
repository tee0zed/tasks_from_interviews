# tasks_from_interviews

Disclaimer: Ознакомление приветствуется. Выдача за своё влечет долгий и нудный разговор с собственной совестью.  

## and solvings(mine)

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

### Самый короткий путь по треугольнику

Дан треугольник. Найдите минимальный путь от вершины до основания. На каждом шаге вы можете двигаться только на соседние цифры, находящиеся в ряду ниже.

Пример:

```
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
```


```
array.map { |subarr| subarr.min } 
```

### Строка

Имеется строка набранная в разном регистре, например: «ВотТакаяСтрока» требуется получить в результате строку где буквы меняют регистр, то есть: «вОТтАКАЯсТРОКА». Напишите, пожалуйста, код.

-_-
```
string.swapcase
```

без магии
```
def swapcase(string)
  string.split('')
    .map { |char| 
      char.match?(/[[:upper:]]/) ? char.downcase : char.upcase 
    }.join
end 
```

### FooBar

Тыры-пыры, она же FizzBuzz. Напишите программу, которая выводит на экран числа от 1 до 100. При этом вместо чисел, кратных 3, программа должна выводить слово «Fizz», а вместо чисел, кратных 5 — слово «Buzz». Если число кратно и 3, и 5, то программа должна выводить слово «FizzBuzz».

```
(1..100).map {|num| 
  if num % 15 == 0
    'FizzBuzz'
  elsif num % 3 == 0
    'Fizz'
  elsif num % 5 == 0 
    'Buzz'
  else 
    num
  end } 
``` 
### Consist of? 

Дана строка s и словарь dict , содержащий некие слова. Определите, можно ли строку s сегментировать в последовательность разделенных пробелом слов, содержащихся в словаре dict.

Пример: дано, s = «двадесятка», dict = [«два», «десятка», «девятка»]. Программа должна вернуть true, потому что «двадесятка» могут быть сементированы как «два десятка».

```
def consist_of?(string)
 arr.each { |chunk| string.delete!(chunk) }
 string.empty? 
end 
```

### Sqr_root 

Напишите метод который бы возвращал квадратный корень указанного числа. 

-_-

```
def sqrt(num)
  Math.sqrt(num)
end
```
без магии
```
def sqrt?(num, try)
  try**2 == num
end 

def sqrt(num, try = num)
  if sqrt?(num, try)
    return try
  elsif try**2 > num
    try /= 2
    try += 1
  else 
    try *= 2
  end 
  sqrt(num, try)
rescue SystemStackError
  abort "There's no rational root for this num!"
end

puts sqrt(2209)
```

### Consist of squares? 

Напишите метод который бы возвращал "true" если число состоит из квадратов двух чисел.

```
def sum_of_sq?(num, high = Math.sqrt(num).round(1), low = 1)
  
  try = [high**2, low**2].sum
  
  if try == num
    return true 
  elsif try > num 
    high -= 1
  else 
    low += 1
  end
  
  return false if high < 0 
  
  sum_of_sq?(high, low, num)
end 

num = gets.to_i

puts sum_of_sq?(num)
```
