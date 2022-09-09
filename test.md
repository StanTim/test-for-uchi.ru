##Станислав Тиманов. Тестовое задание.для uchi.ru

###1) Есть массив
   [1, 2, 12, 34, 35, 6, 0, 34, 122, 124, 789, 999, 33, 54, 763, 893 ]
   ####a) напишите функцию, которая получает на вход исходный массив и возвращает 2 максимальных значения

```
   # возвращает массив из двух максимальных значений
   
   # массива чисел в порядке по убыванию
   def two_max_values_from(array_of_numbers)
   max = 0
   pre_max = 0
   
   array_of_numbers.each do |number|
   if number >= max
   pre_max = max
   max = number
   elsif number >= pre_max
   pre_max = number
   end
   end
   
   [max, pre_max]
   end
```

####b) напишите функцию, которая получает на вход исходный массив и возвращает 2 минимальных значения

```
   # возвращает массив из двух минимальных значений
   
   # массива чисел в порядке по возрастанию
   
   def two_min_values_from(array_of_numbers)
   
   # приравняем искомые числа к бесконечности
   
   min = 1.0 / 0.0
   pre_min = min
   
   array_of_numbers.each do |number|
   if number <= min
   pre_min = min
   min = number
   elsif number <= pre_min
   pre_min = number
   end
   end
   
   [min, pre_min]
   end
```

###2) Есть массив arr = [{a: 1, b: 2, c: 45}, {d: 123, c: 12}, {e: 87}]

####a) напишите выражение, которое получает массив всех ключей
```
   # Возвращает массив ключей массива хешей
   def get_keys(hashes_array)
   
   # массив ключей
   keys = []
   
   hashes_array.each do |hash|
   hash.each_key { |key| keys << key }
   end
   
   keys
   end
```

####b) напишите выражение, которое получает массив всех значений

```
   # Возвращает массив значений массива хешей
   def get_values(hashes_array)
   
   # массив значений
   values = []
   
   hashes_array.each do |hash|
   hash.each_value { |value| values << value }
   end
   
   values
   end
```

####с) напишите выражение, которое получает сумму всех значений

```
   # Возвращает массив значений массива хешей
   def get_values_sum(hashes_array)
   
   # сумма значений
   sum = 0
   
   hashes_array.each do |hash|
   
   hash.each_value { |value| sum += value }
   end
   
   sum
   end
```

###3) Найдите вхождения каждого элемента в массив
   [ nil, 2, :foo, “bar”, “foo”, “apple”, “orange”, :orange, 45, nil,
   :foo, :bar, 25, 45, :apple, “bar”, nil]
   чтобы на выходе получился Hash по типу { элемент => количество вхождений в массив}

```
   # Возвращает количество вхождений элементов в массив
   def get_each_element_quantity(array)
   
   result = Hash.new
   
   array.each { |element| result[element] = array.count(element) }
   
   result
   end
```

###4) Напишите функцию 
####a) которая переводит градусы по Цельсию в градусы по Фаренгейту (формулу нужно найти в интернете)

```
   def convert_cels_to_fahr(deg)
   (deg*1.8 + 32).round(2)
   end
```

####b) напишите консольную программу, которая просит юзера ввести число (градусы по Цельсию) и переводит его в Фаренгейты

```
   def convert_cels_to_fahr(deg)
   (deg*1.8 + 32.0).round(2)
   end
   
   puts "Введите температуру в градусах"
   
   c = STDIN.gets.chomp.to_f
   
   puts "#{c} град. Цельсия это #{convert_cels_to_fahr(c)} Фаренгейт"
```

####с) необязательно, но будет плюсом Напишите обработку ошибок, если юзер ввел неправильные данные (программа должна просить ввести число заново и сообщать об ошибке, но не прерываться)

```
   # Программа-конвертер градусов Цельсия в Фаренгейт.
   
   puts "Введите температуру в градусах"
   
   # Температура в градусах
   c = nil
   
   while c.nil?
   
   c = Float(STDIN.gets.gsub(/,/, '.').chomp) rescue nil
   
   puts "Введите число!" if c.nil?
   end
   
   def convert_cels_to_fahr(deg)
   (deg * 1.8 + 32.0).round(2)
   end
   
   puts "#{c} град. Цельсия это #{convert_cels_to_fahr(c)} Фаренгейт"
```

###Напишите функцию, которая имитирует работу светофора 
####a) на вход она получает один из цветов в виде строки (‘red’, ‘green’, ‘yellow’ ), на выходе будет результат (идти, стоять или ждать)

```
   def traffic_ligt(color)
   {'red' => 'stay!', 'green' => 'go!', 'yellow' => 'ready!'}[color]
   end
```

####b) напишите это в виде консольной программы, которая не прекращает работу после однократного вызова, а ждет следующих запросов

```
   # Программа-имитатор светофора
   puts 'Type color: red, green or yellow'
   
   def traffic_ligt(color)
   {'red' => 'stay', 'green' => 'go!', 'yellow' => 'ready!'}[color]
   end
   
   loop do
   
   color = STDIN.gets.chomp.downcase
   
   puts traffic_ligt(color)
   end
```

####c) необязательно, но будет плюсом напишите обработку некорректных данных и добавьте возможность юзеру завершить работу программы

```
   # Программа-имитатор светофора с обработкой некорректных данных
   options = ['red', 'green', 'yellow', 'end']
   
   def traffic_ligt(color)
   {'red' => 'stay', 'green' => 'go!', 'yellow' => 'ready!'}[color]
   end
   
   loop do
   
   puts 'Type color: red, green, or yellow'
   puts 'Type end for exit'
   
   input = STDIN.gets.chomp.downcase
   
   puts 'Wrong input!' unless options.include?(input)
   
   if input == 'end'
   exit
   else
   puts traffic_ligt(input)
   end
   end
```

###5) Обязательное задание Есть таблица students с колонками 
 - id int
 - name varchar 
 - created_at datetime 
 - parent_id int

####a) посчитайте количество всех студентов 
   `Student.count`

####b) посчитайте количество студентов с именем Иван
`Student.where(name: "Иван").count`

####c) посчитайте количество студентов созданных после 1 сентября 2020 года
`Student.where(created_at: ("2020-9-2"..DateTime.now)).count`

###6) Необязательное задание, но его выполнение будет плюсом. Также есть таблица parents (см задание 5)
   - id int 
   - name varchar
   - created_at datetime 

####a) посчитайте количество студентов с родителями
   `Student.where.not(parent_id: nil).count`

####b) посчитайте количество студентов с родителями при том что имя родителя Марина
`Parent.left_joins(:students).where(name: "Марина").count`

####c) посчитайте количество студентов без родителя
`Student.where(parent_id: nil).count`

###7) Необязательная, но выполнение будет очень большим плюсом 
####a)Напишите простой блог на рельсе с минимальным функционалом (один автор, который выкладывает посты. Комментарии, сортировки, фильтры и основные рюшечки не обязательны, но остаются на ваше усмотрение и желание. Как и стилизация) Heroku:
   *https://easy-blog-st.herokuapp.com/*
   

