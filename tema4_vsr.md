# Вариативная самостоятельная работа

### [4.2 Написать программу, в которой пользователь вводит число от 0 до 9 включительно, а программа выводит название введённого числа, а если второй входной аргумент type имеет значение bin, oct, hex, то функция преобразует это число в бинарную, восьмеричную или шестнадцатеричную форму. Предусмотреть проверку корректности введённого пользователем значения.](https://replit.com/@PolinaLazebniko/sem6-Tema4-VSR-42#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 3 курс
    группа 1.1

    Вариативная самостоятельная работа 
    Задание 4.2: Написать программу, в которой пользователь вводит число от 0 до 9 включительно, 
    а программа выводит название введённого числа, а если второй входной аргумент type имеет значение 
    bin, oct, hex, то функция преобразует это число в бинарную, восьмеричную или шестнадцатеричную форму. 
    Предусмотреть проверку корректности введённого пользователем значения.
"""

def verification(num):
    if len(num) == 1:
        return num.isdigit()
    else:
        return False

def read_num():
    num_operation = input('Введите цифру от 0 до 9 (при необходимости через пробел указать систему счисления (bin, oct, hex):\n')
    num_operation = num_operation.split(' ')

    number = None
    if verification(num_operation[0]):
        numbers = {
            '0': 'Ноль',
            '1': 'Один',
            '2': 'Два',
            '3': 'Три',
            '4': 'Четыре',
            '5': 'Пять',
            '6': 'Шесть',
            '7': 'Семь',
            '8': 'Восемь',
            '9': 'Девять',
        }
        number = numbers[num_operation[0]]
    else:
        print('Нужно ввести цифру.')
        return [False]

    number_operation = None

    if len(num_operation) == 2:
        number_int = int(num_operation[0])
        operations = {
            'bin': bin(number_int),
            'oct': oct(number_int),
            'hex': hex(number_int)
        }

        number_operation = operations[num_operation[1]]
    return [number, number_operation]

if __name__ == '__main__':
    res = read_num()
    for i in res:
        if i != None:
            print(i)
```
