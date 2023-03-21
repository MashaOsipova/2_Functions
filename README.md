Домашнее задание к лекции. «2. Функции»

Задача № 1

Напишите функцию getArrayParams(arr), которая получает на вход массив чисел от -100 до 100 и возвращает минимальное, максимальное и среднее арифметическое значения массива.

Создайте функцию, которая принимает на ввод массив.
Внутри функции задайте 3 переменных min, max, sum, присвоив им некоторые первоначальные значения.

Подсказка, какие значения присвоить:
Пройдите по массиву циклом for либо while и для каждого элемента определите:
если элемент больше предыдущего максимума, то максимум становится равен элементу;
если элемент меньше предыдущего минимума, то минимум становится равен элементу;
добавляем элемент к сумме sum для вычисления среднего.

После прохождения цикла функция должна возвращать объект вида: {max:..., min: ..., avg:...}, то есть минимальное, максимальное и среднее значения. Чтобы вычислить среднее, нужно сумму элементов поделить на их количество. Среднее значение нужно округлить до двух знаков после запятой. Для округления воспользуйтесь toFixed. Заметьте, toFixed возвращает string. Так как вам необходимо вернуть число (number), то потребуется дополнительное преобразование значения к числу.

Пример
getArrayParams([-99, 99, 10]) // { min: -99, max: 99, avg: 3.33 }
getArrayParams([1, 2, 3, -100, 10])  // { min: -100, max: 10, avg: -16.80 }

Задача № 2

Представьте, что у нас есть мясорубка с разными насадками. Мясорубка запускает процесс. Он зависит от того, какая будет насадка. Затем мясорубка применяет насадку ко всему мясу, которое в неё поступает, и выдаёт на выход только самый лучший кусок.

Пусть дан массив, каждый элемент которого в свою очередь является массивом чисел, например arrOfArr=[[1, 2, 3, 4], [10, 20, -10, -20]]. Нужно среди всех массивов найти такой, сумма элементов которого максимальна, и вывести сумму.

Задачу можно разбить на части:

написать функцию, которая будет считать сумму элементов массива — это «насадка мясорубки»;

написать функцию, которая применит «насадку» ко всем массивам, которые поступили нам на вход, — это «мясорубка». Тогда входные данные, массив массивов, являются «мясом».

Итак, напишем две функции: makeWork(arrOfArr,func) — в наших терминах это мясорубка и worker(arr) — это насадка.

Напишите функцию worker, которая должна находить сумму элементов массива и возвращать её.
Функция makeWork принимает входные данные — массив массивов и функцию worker. То есть makeWork — функция высшего порядка.
Затем makeWork применяет функцию worker к каждому из массивов worker(arrOfArr[i]), вычисляя сумму элементов.
Если сумма больше предыдущего максимума, то меняем максимум. Его следует хранить в отдельной переменной и задавать в начале функции makeWork.
Таким образом наша мясорубка не только перемалывает (находит сумму чисел каждого массива), но и возвращает самый жирный кусок (с максимальной суммой).

Совет: Напишите функцию worker, которая должна находить сумму элементов массива и возвращать её. Протестируйте функцию отдельно на своих примерах, например на (https://jsbin.com). Убедитесь, что она работает. Затем передайте её в makeWork. Обратите внимание, что внутри она попадет в переменную func и мы сможем вызывать её func(arr). Итерируйтесь по массиву arrOfArr с помощью цикла, выполняя worker для каждого элемента, то есть находя сумму. Если сумма больше ранее найденного максимума, присваивайте max = sum.

Задача №3

Попробуем реализовать другую насадку для нашей мясорубки. Для этого напишем функцию worker2 которая должна находить разность максимального и минимального значения внутри массива. Это можно интерпретировать как расстояние между минимумом и максимумом. Заметьте, что данная разность — всегда неотрицательное число. Используйте Math.abs() для вычисления модуля числа. Затем используйте данную насадку как аргумент для функции makeWork.
