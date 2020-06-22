# Домашние задания по курсу "Язык программирования Java"

# Домашнее задание 1. Обработка изображений

Ваша задача разработать реализации интерфейсов `ImageConverter` и `ConvolutionProvider` и
создать их в методах `impl.image.ImageConverterFactory.getInstance` и `impl.image.ConvolutionProviderFactory.getInstance` соответственно.

`ImageConverter` должен уметь превращать `Color[][]` в `int[][]` и обратно, где `int` будет хранить в себе данные о цвете в таком виде:
  * 0-7 биты хранят информацию о голубом цвете (`blue`), 
  * 8-15 биты хранят информацию о зеленом цвете (`green`), 
  * 16-23 биты хранят информацию о красном цвете (`red`),
  * 24-31 биты хранят информацию о прозрачности (`alpha`).

`ConvolutionProvider` должен уметь применять операцию [свертки](https://en.wikipedia.org/wiki/Kernel_(image_processing)) 
к данной картинке, используя ядро (гарантируется, что размерности ядра > 0).
  *  Применять операцию свертки следует к каждому цвету отдельно.
  *  Размер изображения меняться не должен.
  *  Если при применении свертки, элемент ядра выходит за пределы картинки, следует считать, что `red, green, blue = 0`.
  *  `alpha` всегда оставлять равной `255`.
  *  После каждого умножения значения цвета на элемент ядра следует производить округление к `0`.
  
В пакете `impl.image` представлен класс `ImageUtil` его методы `writeOutputImage`, `readOriginImage` можно использовать, чтобы
записывать картинки в папку `resources/image/output` и читать картинки из папки `resources/image/origin`. 
С их помощью можно смотреть, как операция свертки влияет на изображения. 
  *  Все картинки должны быть в формате `png`.
  *  При указании имени картинки, формат также должен указываться (например `pic1.png`).

# Домашнее задание 2. Исключения

Ваша задача разработать реализацию интерфейса `ExpressionParser` и создать её в методе `impl.expression.ExpressionParserFactory.getInstance`.

`ExpressionParser` должен уметь вычислять значение арифметического выражения `expression`.

`expression` состоит из целочисленных констант, `+`, `-` и пробельных символов.  
Все вычисления следует производить в `int`.
Пробельных символов внутри констант быть не может.
Несколько `+`, `-` подряд быть не может.
Парсинг выражения должен работать за линейное время.

Следует обратить внимание на обработку возможных ошибок разбора и вычисления выражений.

# Домашнее задание 3. Статистика погоды

Ваша задача разработать реализации интерфейсов `YearTemperatureStats` и `YearTemperatureStatsParser` и
создать их в методах `impl.weather.YearTemperatureStatsFactory.getInstance` и `impl.weather.YearTemperatureStatsParserFactory.getInstance` соответственно.

`YearTemperatureStats` должен уметь возвращать:
  * температуру за данный день месяца (или `null` если о дне ничего не известно); (константное время работы)
  * среднюю температуру за данный месяц (или `null` если о месяце ничего не известно); (константное время работы)
  * максимальную температуру для каждого месяца, о котором есть данные; (время работы `O(число известных месяцев)`)
  * список дней данного месяца, о которых есть данные.
    Список должен быть отсортирован по невозрастанию температуры. 
    Если в два дня температура была одинаковой, первым должен идти тот, данные о котором пришли первые.

`YearTemperatureStats` должен уметь обновлять свое состояние в зависимости от данного `DayTemperatureInfo` (за константное время).

`YearTemperatureStatsParser` должен уметь возвращать `YearTemperatureStats` из сырых данных - `Collection<String>`.
Каждая строка имеет вид `day.month temperature`.

# Домашнее задание 4. Очередь

Ваша задача разработать реализации интерфейса `java.util.Queue<Integer>` и 
создать в методах `queue.impl.ArrayQueueFactory.getInstance` и `queue.impl.LinkedQueueFactory.getInstance` 
реализации на массиве и связном списке соответственно.

Готовые решения использовать нельзя.
Можно пользоваться любыми абстрактными классами стандартной библиотеки.
Постарайтесь сделать так, чтобы при длинной цепочке действий `add(element), poll` 
программа не потребляла много памяти.

# Домашнее задание 5. Файлы и Кодировки

Ваша задача разработать реализации интерфейсов `api.file.FileEncodingReader` и `api.file.FileEncodingWriter` и 
создать их в методах `impl.file.FileEncodingReaderFactory.getInstance` и `impl.file.FileEncodingWriterFactory.getInstance` соответственно.

`FileEncodingReader` должен уметь возвращать `java.io.Reader` из файла в заданной кодировке.

`FileEncodingWriter` должен уметь создавать файл и записывать в него данные из `InputStream` с кодировкой `dataEncoding` в кодировке `fileEncoding` (`UTF-8`, если `fileEncoding` не передана).

# Домашнее задание 6. Пары

Ваша задача разработать реализации интерфейсов `api.pair.Pair` и `api.pair.NumberPair` и 
уметь создавать их в методах `impl.pair.PairFactory.of` и `impl.pair.NumberPairFactory.of` соответственно.
Пары хранят в себе два значения `first` и `second`.

# Домашнее задание 7. Студенты

1. Разработайте класс StudentDB, осуществляющий поиск по базе данных студентов.
   * Класс StudentDB должен реализовывать интерфейс StudentQuery.
   * Каждый метод должен состоять из ровно одного оператора. При этом длинные операторы надо разбивать на несколько строк.
2. При выполнении задания следует обратить внимание на:
   * Применение лямбда-выражений и потоков.
   * Избавление от повторяющегося кода.

Объект класса StudentDB должен быть создан в методе `info.kgeorgiy.java.advanced.student.StudentQueryFactory.getInstance`
