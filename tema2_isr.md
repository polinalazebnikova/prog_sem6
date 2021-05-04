# Инвариантная самостоятельная работа

### [2.1 На основе кода, предоставленного преподавателем, реализовать генератор чисел ряда Фибоначчи. Генератор требуется создать двумя вариантами: с помощью генератора списков, с помощью функции, внутри которой yield.](https://replit.com/@PolinaLazebniko/sem6-Tema2-ISR-21#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 3 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 2.1: На основе кода, предоставленного преподавателем, реализовать генератор чисел 
    ряда Фибоначчи. Генератор требуется создать двумя вариантами: с помощью генератора списков, с помощью функции, внутри которой yield.
"""
def fib(n):
    value = 1
    if n == 0:
        value = 0
    if n > 2:
        value = fib(n - 1) + fib(n - 2)
    return value

def fib_yield(n):
    a, b = 1, 1
    for i in range(n):
        yield a
        a, b = b, a + b

if __name__ == '__main__':
    # генератор списков
    n = 20
    gen_list = [fib(i) for i in range(n + 1)]
    print(gen_list)

    # с помощью функции, внутри которой yield.
    fib_func_yield = fib_yield(n)
    for i in range(n):
        print(fib_func_yield.__next__())
```
### [2.2 Разработать программу, позволяющую генерировать уникальные идентификаторы: UUID (universally unique identifier). Структура UUID — на усмотрение студента.](https://replit.com/@PolinaLazebniko/sem6-Tema2-ISR-22#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 3 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 2.2: Разработать программу, позволяющую генерировать уникальные идентификаторы: UUID (universally unique identifier). Структура UUID — на усмотрение студента
"""
from datetime import datetime

def uniqid():
    time_parts = ['%Y', '%m%d', '%H%M%S', '%f']
    while True:
        uniq_id = ''
        time_now = datetime.utcnow()
        for part in time_parts:
            if part == time_parts[0]:
                uniq_id += (str(hex(int(time_now.strftime(part))))[2::])
            else:
                uniq_id += ('-' + str(hex(int(time_now.strftime(part))))[2::])
        yield uniq_id

if __name__ == '__main__':
    uniqid = uniqid()
    n = 40
    for i in range(n):
        print(uniqid.__next__())
```
### [2.3 На основе кода, предоставленного преподавателем, реализовать корутину, позволяющую использовав метод send() для возврата генерируемой сущности. В основе корутины должен использоваться принцип блокчейна (цепочки блоков). Кроме механизма возврата нового блока требуется создать механизм, позволяющий вернуть историю сгенерированных блоков.](https://replit.com/@PolinaLazebniko/sem6-Tema2-ISR-23#main.py)
```python

```
