# Тема 6. Базовые коллекции: словари, кортежи
Отчет по Теме #6 выполнил:
- Наговицын Дмитрий
- АИС-22-1

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |


знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
### В школе, где вы учились, узнали, что вы крутой программист и попросили написать программу для учителей, которая будет при вводе кабинета писать для него ключ доступа и статус, занят кабинет или нет. При написании программы необходимо использовать словарь (dict), который на вход получает номер кабинета, а выводит необходимую информацию. Если кабинета, который вы ввели нет в словаре, то в консоль в виде значения ключа нужно вывести "None" и виде статуса вывести "False". 

```python
request = int(input('Введите номеркабинета: '))

dictionary = {
    101: {'key': 1234, 'access': True},
    102: {'key': 1337, 'access': True},
    103: {'key': 8943, 'access': True},
    104: {'key': 5555, 'access': False},
    None: {'key': None, 'access': False},
}

response = dictionary.get(request)
if not response:
    response = dictionary[None]
key = response.get('key')
access = response.get('access')
print(key,access)
```
### Результат.
![](pic/5лр_1.png)


## Лабораторная работа №2
### Алексей решил создать самый большой словарь в мире. Для этого он придумал функцию dict_maker (**kwargs), которая принимает неограниченное количество параметров «ключ: значение» и обновляет Михаил А. Панов созданный им словарь my_dict, состоящий всего из одного элемента «first» со значением «so easy». Помогите Алексею создать данную функцию.

```python
from pprint import pprint

my_dict = {'first': 'so easy'}

def dict_market(**kwargs):
    my_dict.update(**kwargs)

dict_market(a1=1, a2=20, a3=54, a4=13)
dict_market(name='Михаил', age=31, weight=70, eyes_color='blue')
pprint(my_dict)
```
### Результат.
![](pic/5лр_2.png)


## Лабораторная работа №3
### Для решения некоторых задач бывает необходимо разложить строку на отдельные символы. Мы знаем что это можно сделать при помощи split(), у которого более гибкая настройка для разделения для этого, но если нам нужно посимвольно разделить строку без всяких условий, то для этого мы можем использовать кортежи (tuple). Для этого напишем любую строку, которую будем делить и “обвернем” ее в tuple и дальше мы можем как нам угодно с ней работать, например, сделать ее списком (тогда получится полный аналог split()) или же работать с ним дальше, как с кортежем. 

```python
input_string = 'HelloWorld'
result = tuple(input_string)
print(result)
print(list(result))
```
### Результат.
![](pic/5лр_3.png)


## Лабораторная работа №4
### Вовочка решил написать крутую функцию, которая будет писать имя, возраст и место работы, но при этом на вход этой функции будет поступать кортеж. Помогите Вовочке написать эту программу. 

```python
def personal_info(name, age, company='unnamed'):
    print(f"Имя: {name} Возраст: {age} Компания: {company}")

tom = ("Григорий", 22)
personal_info(*tom)

bob = ("Георгий", 41, "Yandex")
personal_info(*bob)
```
### Результат.
![](pic/5лр_4.png)


## Лабораторная работа №5
### Для сопровождения первых лиц государства X нужен кортеж, но никто не может определиться с порядком машин, поэтому вам нужно написать функцию, которая будет сортировать кортеж, состоящий из целых чисел по возрастанию, и возвращает его. Если хотя бы один элемент не является целым числом, то функция возвращает исходный кортеж.

```python
def tuple_sort(tpl):
    for elm in tpl:
        if not isinstance(elm, int):
            return tpl
    return tuple(sorted(tpl))

if __name__ == '__main__':
    print(tuple_sort((5, 5, 3, 1, 9)))
    print(tuple_sort((5, 5, 2.1, '1', 9)))
```
### Результат.
![](pic/5лр_5.png)

## Самостоятельная работа №1
### При создании сайта у вас возникла потребность обрабатывать данные пользователя в странной форме, а потом переводить их в нужные вам форматы. Вы хотите принимать от пользователя последовательность чисел, разделенных пробелом, а после переформатировать эти данные в список и кортеж. Реализуйте вашу задумку.

```python
x = input().split()
my_tuple = tuple(x)
print(f"Список = {x}\nКортеж = {my_tuple}")
```
### Результат.
![](pic/5ср_1.png)

## Самостоятельная работа №2
### Николай знает, что кортежи являются неизменяемыми, но он очень упрямый и всегда хочет доказать, что он прав. Студент решил создать функцию, которая будет удалять первое появление определенного элемента из кортежа по значению и возвращать кортеж без него. Попробуйте повторить шедевр не признающего авторитеты начинающего программиста. Но учтите, что Николай не всегда уверен в наличии элемента в кортеже.

```python
def remove_tumple():
    x = input().split()
    my_tuple = set(map(int,x))
    b = int(input())
    if b in my_tuple:
        my_tuple.remove(b)
        return tuple(my_tuple)
    else:
        return tuple(my_tuple)

print(remove_tumple())
```
### Результат.
![](pic/5ср_2.png)

## Самостоятельная работа №3
### Ребята поспорили кто из них одним нажатием на numpad наберет больше повторяющихся цифр, но не понимают, как узнать победителя. Вам им нужно в этом помочь. Дана строка в виде случайной последовательности чисел от 0 до 9 (длина строки минимум 15 символов). Требуется создать словарь, который в качестве ключей будет принимать данные числа (т. е. ключи будут типом int), а в качестве значений – количество этих чисел в имеющейся последовательности.

```python
def numpad_winner(n):
  duplicate = []
  counter = {}
  new_array = []

  if len(n) < 15:
    print('Попробуйте ещё раз')
  else: 
    numbers = list(n)
    for item in numbers:
      if numbers.count(item) > 1:
        duplicate.append(item)
      else: 
        pass
    
    for item in duplicate:
      if item not in counter:
        counter[item] = 0
      counter[item] += 1

  new_array = sorted(counter.items(), key=lambda x: x[1], reverse=True)
  top_3 = new_array[:3]

  top_3_sorted = sorted(top_3, key=lambda x: (-x[1], x[0]))

  result = ', '.join([f"{key}: {value} раз(а)" for key, value in top_3_sorted])
  print(result)


numpad_winner(input())
```
### Результат.
![](pic/5ср_3.png)

## Самостоятельная работа №4
### Ваш хороший друг владеет офисом со входом по электронным картам, ему нужно чтобы вы написали программу, которая показывала в каком порядке сотрудники входили и выходили из офиса. Определение сотрудника происходит по id. Напишите функцию, которая на вход принимает кортеж и случайный элемент (id), его можно придумать самостоятельно. Требуется вернуть новый кортеж, начинающийся с первого появления элемента в нем и заканчивающийся вторым его появлением включительно

```python
def enters_inf(*args):
    info = input().split()
    enter_tuple = list(map(int, info))
    id = int(input())

    if id in enter_tuple and enter_tuple.count(id) == 1:
        enter_tuple = tuple(enter_tuple[enter_tuple.index(id):])
        print(enter_tuple)
    elif id in enter_tuple and enter_tuple.count(id) > 1:
        new_tuple = tuple(enter_tuple[enter_tuple.index(id)+1:])
        new_tuple = tuple(enter_tuple[enter_tuple.index(id):new_tuple.index(id) + enter_tuple.index(id) + 2])
        print(new_tuple)

    else:
        enter_tuple.clear()
        return print(tuple(enter_tuple))

enters_inf()
```
### Результат.
![](pic/5ср_4.png)

## Самостоятельная работа №5
### Самостоятельно придумайте и решите задачу, в которой будут обязательно использоваться кортеж или список. Проведите минимум три теста для проверки работоспособности вашей задачи.

```python
def week_info(*args):
  days_of_week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
  attendance = input().split()
  attendance = [int(item) for item in attendance]

  if len(attendance) != 7:
    print('Неверное количество дней, их должно быть 7')
  else:
    max_attendance = max(attendance)
    max_day = days_of_week[attendance.index(max_attendance)]

    min_attendance = min(attendance)
    min_day = days_of_week[attendance.index(min_attendance)]


    day_attendance = int(sum(attendance) / len(attendance))

    print(
    f"Максимальное количество посетителей: {max_attendance} в ({max_day})\n"
    f"Минмальное количество посетителей: {min_attendance} в ({min_day})\n"
    f"Среднее количество посетителей за всю неделю: {day_attendance}"
    )


week_info()
```
### Результат.
![](pic/5ср_5.png)
