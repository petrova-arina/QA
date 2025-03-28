# Тестирование методом белого и черного ящика

При проектировании системы класса LIMS по метрологическому обеспечению необходимо заложить бизнес-логику согласно ГОСТ Р 8.932-2022: Рекомендуются следующие правила округления: 

Числовое значение характеристик погрешности, выраженных в абсолютной форме, округляют до одной или двух значащих цифр. Если первая значащая цифра характеристики погрешности 1 или 2, то должна присутствовать и вторая значащая цифра от 0 до 9, например 0,20 г/см ; 0,0014 мм. Если первая значащая цифра характеристики погрешности 3 или 4, то должна присутствовать и вторая значащая цифра - 0 или 5, например 0,35 г/см ; 0,0040 мм. Если первая значащая цифра характеристики погрешности более 4, то вторая значащая цифра должна отсутствовать, например 0,5 г/см ; 6 мг/дм .

Полученное при аттестации значение характеристики погрешности округляют в большую сторону, например: 0,31 г/см  0,35 г/см , а не 0,31 г/см  0,30 г/см ; 0,61 мг/дм  0,7 мг/дм ; 2,72 мм 2,8 мм. 

В числовом значении характеристики погрешности измерений, выраженной в относительной форме, а также в значениях коэффициентов, определяющих функциональную зависимость характеристики погрешности измерений (6.4.2), число значащих цифр может быть равно двум, вне зависимости от их первой значащей цифры. 

Значащие цифры числа — это все цифры от первой слева, не равной нулю, до последней записанной цифры справа. При этом нули, следующие из множителя 10n, не учитываются. Числовое значение характеристик погрешности, выраженных в абсолютной форме, округляют до одной или двух значащих цифр. 

Если первая значащая цифра характеристики погрешности 1 или 2, то должна присутствовать и вторая значащая цифра от 0 до 9, например 0,20 г/куб.см; 0,0014 мм. 
Если первая значащая цифра характеристики погрешности 3 или 4, то должна присутствовать и вторая значащая цифра - 0 или 5, например 0,35 г/куб.см; 0,0040 мм. 
Если первая значащая цифра характеристики погрешности более 4, то вторая значащая цифра должна отсутствовать, например 0,5 г/куб.см; 6 мг/куб.дм.

## Черный ящик

round_error(0.31) = 0.35, ожидалось 0.35 -> Пройдено  
round_error(0.61) = 0.7, ожидалось 0.7 -> Пройдено  
round_error(2.72) = 2.8, ожидалось 2.8 -> Пройдено  
round_error(0.0046) = 0.005, ожидалось 0.005 -> Пройдено  
round_error(0.0031) = 0.0035, ожидалось 0.0035 -> Пройдено  
round_error(0.0009) = 0.0009, ожидалось 0.0009 -> Пройдено  
round_error(6.8) = 7.0, ожидалось 7.0 -> Пройдено  

- Тестирование проводилось без знания кода, только по спецификации.

- Проверялись входные данные и ожидаемые результаты.

- Позволяет легко протестировать соответствие требованиям.

- Недостаток: не покрывает возможные ошибки в логике кода.

## Белый ящик

Ran 7 tests in 0.001s

OK

- Проверялись все возможные ветки кода, обеспечивая полное покрытие.

- Использовались юнит-тесты для проверки логики работы функций.

- Обнаруживает ошибки внутри кода, даже если внешне всё работает правильно.

- Недостаток: требует знания внутренней структуры программы.

## Общий вывод
Оба метода тестирования важны и дополняют друг друга. Черный ящик проверяет соответствие требованиям, а белый помогает выявить логические ошибки в коде. Оптимальный подход – комбинировать оба метода для максимального качества тестирования.
