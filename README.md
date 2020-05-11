# Автоматическое распознавание рукописей: тестируем Transkribus

## Технологии распознавания текста (как работает OCR) 

OCR (англ. optical character recognition, оптическое распознавание символов) — это технология автоматического анализа текста и превращения его в данные, которые может обрабатывать компьютер.

Когда человек читает текст, он распознает символы с помощью глаз и мозга. У компьютера в роли глаз выступает камера сканера, которая создает графическое изображение текстовой страницы (например, в формате JPG).

#### Портативный сканер

![](https://github.com/alexdyul/Transkribus/blob/master/Portable_scanner.gif)

Для компьютера нет разницы между фотографией текста и фотографией дома: и то, и другое — набор пикселей.

#### Таким компьютер видит Авраама Линкольна 

![](https://github.com/alexdyul/Transkribus/blob/master/Lincoln.png)

#### А таким слона

![](https://github.com/alexdyul/Transkribus/blob/master/Elefant.png)

#### Так работает компьютерное зрение 

![](https://github.com/alexdyul/Transkribus/blob/master/Comp_vision.gif)


### Возвращаемся к OCR

Именно OCR превращает изображение текста в текст. А с текстом уже можно делать что угодно

#### Развитие OCR

#### Распознавание паттерна

В 1960-х годах был создан специальный шрифт OCR-A, который использовался в документах типа банковских чеков. Каждая буква в нем была одинаковой ширины (т.н. шрифт фиксированной ширины или моноширинный шрифт).

![](https://github.com/alexdyul/Transkribus/blob/master/OCR_old.png)

Принтеры для чеков работали с этим шрифтом, и для его распознавания было разработано программное обеспечение. Поскольку шрифт был стандартизирован, его распознавание стало относительно простой задачей. 

Следующим шагом стало обучение программ OCR распознавать символы еще в нескольких самых распространенных шрифтах (Times, Helvetica, Courier и т.д.)

##### И тут проблема

![](https://github.com/alexdyul/Transkribus/blob/master/A.png)

Оказалось, что буква "А" бывает разной

Появился второй способ - выявление признаков 

#### Выявление признаков

Этот способ еще называют интеллектуальным распознаванием символов (англ. intelligent character recognition, ICR). 

Можно использовать такое правило: если видишь две линии, сходящиеся наверху в центре под углом, а посередине между ними горизонтальная линия, то это буква «А». Это правило поможет распознать все буквы «А» независимо от шрифта. Вместо распознавания паттерна выделяются характерные индивидуальные черты, из которых состоит символ. 

Большинство современных омнишрифтовых (умеющих распознавать любой шрифт) OCR-программ работают по этому принципу. Чаще всего в них используются классификаторы на основе машинного обучения (т.к. фактически перед нами стоит задача классификации картинок по классам-буквам) в последнее время некоторые OCR-движки перешли на нейронные сети.

#### А что же такое нейронная сеть? 

![](https://github.com/alexdyul/Transkribus/blob/master/Netz.jpg)



### И снова возвращаемся к OCR. Алгоритм работы


![](https://github.com/alexdyul/Transkribus/blob/master/OCR_Bloc.jpg)


#### Предобработка. Улучшение качества изображения

Старый шрифт, пятна от кофе или чернил, заломы бумаги понижают шансы OCR.

Если исходное отсканированное изображение идеально, то все черное — это символы, а все белое — фон.


#### Распознавание

Сначала OCR-программа объединяет пиксели в возможные буквы, а буквы — в возможные слова. Затем система сопоставляет варианты слов со словарем. 

Если слово найдено, оно отмечается как распознанное. 

Если слово не найдено, программа предоставляет наиболее вероятный вариант и, соответственно, качество распознавания будет не таким высоким.

![](https://github.com/alexdyul/Transkribus/blob/master/text-detection.jpg)


#### Постобработка

Некоторые программы дают возможность просмотреть и исправить ошибки. 

Для этого они используют встроенную проверку орфографии и выделяют неверно написанные слова, что может указывать на неправильное распознавание. 

Продвинутые OCR-программы используют так называемый метод поиска соседа, чтобы найти слова, которые часто встречаются рядом. 
Этот метод позволяет исправить неверно распознанное словосочетание «тающая собака» на «лающая собака».

Кроме того, некоторые проекты, которые занимаются оцифровкой и распознаванием текстов, прибегают к помощи волонтеров: распознанные тексты выкладываются в открытый доступ для вычитки и проверки ошибок распознавания.

### Особые случаи

#### Иероглифы

Где заканчивается слово, где начинается новое? 

![](https://github.com/alexdyul/Transkribus/blob/master/japan.png)


#### Старые/уникальные шрифты

[FineReader XIX](https://www.abbyy.com/ru-ru/ocr-sdk/key-features/ocr) — платный софт для старых документов, книг и газет, напечатанных с 1600 по 1937 годы на английском, французском, немецком, итальянском и испанском языках старыми шрифтами, среди которых Fraktur, Schwabacher и Gothic 

[Проект OCR4all](https://github.com/OCR4all/OCR4all) - бесплатный полуавтоматический рабочий ресурс, позволяющий пользователям выполнять распознавание текста даже на самых ранних печатных книгах. Центрор филологии и цифровой науки "Kallimachos" в Вюрцбургском университете


## Проблемы работы с рукописными текстами

Каждый почерк уникален

Расстановка пробелов - дело каждого. Бывают пробелы и между букавами, а бывает и нет

Высокая вероятность ошибок в исходном тексте

### Промежуточный вариант

Рукопечатный текст (ICR) - такое правда существует. [Тут](https://www.abbyy.com/ru-ru/ocr-sdk/key-features/ocr) доказательства 

![](https://github.com/alexdyul/Transkribus/blob/master/Htext.png)


## Перепись населения Норвегии 1950 года. Успешный исторический кейс


Кто: Норвежский Центр исторических данных (Norwegian Historical Data Centre)

Данные проекта:
801 тысяча опросных листов — формуляров размером 29.7x70.7 см, заполненных вручную с обеих сторон. 
1,6 миллиона изображений в форматах jpeg и jpeg2000. 
В каждом формуляре могло быть зарегистрировано до 10 человек.


#### Как работало распознание?

Каждая клетка с текстом анализируется с помощью 30 математических переменных, которые характеризуют текстовое изображение. 

На основе этой информации клетки группируются в кластеры и далее анализируются с помощью интерактивного графического интерфейса

В процессе анализа на экран компьютера выводятся возможные варианты, например, мест рождений, которые похожи на изображения анализируемого кластера, а также вариант возможного транскрибирования 

![](https://github.com/alexdyul/Transkribus/blob/master/nor.jpg)

После этого оператор должен исключить ошибочно сгруппированные изображения и нажать «ОК» или изменить вариант транскрибирования остальных. 

Это достаточно эффективный метод ручного управления транскрибированием миллионов изображений, содержащих информацию о месте рождения, поскольку число вариантов таких названий в сельской местности Норвегии ограничено. Добровольцы, привлеченные к транскрибированию источников этим методом, считают, что этот процесс также увлекателен, как и разгадывание Судоку, но в отличие от Судоку, транскрибирование имеет еще и большое практическое значение.


Поскольку автоматически транскрибировать эту информацию оказалось невозможно, пришлось сделать это вручную, оплатив услуги индийской компании Suntech. Передача в Индию изображений, содержащих информацию о дате рождения, не являлась нарушением закона о защите персональных данных, поскольку они никак не могли быть связаны с конкретными персонами. Спустя четыре месяца Suntech вернули таблицы с отформатированными датами рождения в шестизначном или восьмизначном формате. 
Выборочные проверки показали, что точность их транскрибирования находится в пределах допустимой погрешности — 3%.


Прорыв в деле распознавания изображений произошел в связи с использованием инструментария нейросетевых технологий глубокого обучения машин нового поколения. 
353 000 распознанных машиной изображений использовались для обучения искусственной нейронной сети (ИНС), классифицирующей имена. 
Затем эту обученную ИНС применили для классификации оставшихся 3,4 миллионов не идентифицированных имен в переписи. 
Сеть предложила 10 наиболее вероятных имен, каждое с определенным числом баллов соответствия.

##  In Codice Ratio. Расшифровка древних архивов Ватикана

Кто: Ватиканский апостольский архив/Ватиканский секретный архив 

Данные проекта:
53 линейных мили стеллажей
Записи и документы обо всех действиях, предпринятых католической церковью за период более 12 веков
Большинство документов Ватикана написаны от руки


Пример бумаги начала 1200 годов. Алгоритм не понимает, где заканчивается одна буква и начинается другая.

![](https://github.com/alexdyul/Transkribus/blob/master/vat.png)


#### Как работало распознание?

Команда набрала учеников в 24 школах Италии для обработки образцов текста


![](https://github.com/alexdyul/Transkribus/blob/master/it.png)


После того, как школьники отметили «за» на достаточном количестве примеров, программное обеспечение начало самостоятельно собирать кусочки мозаики и самостоятельно оценивать, какие буквы были там.




## Альтернативные программы распознавания рукописного и печатного текста


#### [Google Lens](https://lens.google.com). Рукописный текст

![](https://github.com/alexdyul/Transkribus/blob/master/Google_H.gif)

#### Google Lens. Печатный текст

![](https://github.com/alexdyul/Transkribus/blob/master/Google_T.gif)




## Транскрибус – похоже единственная программа в открытом доступе, которая может распознать старые рукописи


### Кто и где придумал Транскрибус

### Возможности Транскрибус, что он умеет

### Регистрация и учетные записи. Первое знакомство с платформой. Ссылка для регистрации https://transkribus.eu/Transkribus/

### Загрузка и установка программного обеспечения. Ссылка для скачивания https://transkribus.eu/TrpServer/rest/downloadLatestGui 

### Структура данных. Где и как хранятся изображения и текст

### Тестируем систему. Пробуем распознать готовую рукопись

### Как выгружать данные. Форматы и особенности текстовых данных




[Образцы текста + инструкция на русском](https://drive.google.com/open?id=14b0I4bPHHPkkY_uN2V_S-baC3G404SYp)

## Источники:

[Системный блокъ. Из пикселей — в буквы: как работает распознавание текста](https://sysblok.ru/knowhow/iz-pikselej-v-bukvy-kak-rabotaet-raspoznavanie-teksta)

[Wikipedia. Optical character recognition](https://en.wikipedia.org/wiki/Optical_character_recognition)

[Abbyy. Полный набор технологий распознавания](https://www.abbyy.com/ru-ru/ocr-sdk/key-features/ocr)

[Robo-hunter. Как работают нейронные сети: о сложной системе простыми словами](https://robo-hunter.com/news/kak-rabotayt-neironnie-seti-o-slojnoi-sisteme-prostimi-slovami14200)

[Торвальдсен Г. Автоматизация транскрибирования исторических источников: опыт работы с материалами переписи населения Норвегии 1950 года // Историческая информатика. – 2018. – № 1. – С. 94 - 103. DOI: 10.7256/2585-7797.2018.1.25686](https://nbpublish.com/library_read_article.php?id=25686)

[The Atlantic. Artificial Intelligence Is Cracking Open the Vatican's Secret Archives](https://www.theatlantic.com/technology/archive/2018/04/vatican-secret-archives-artificial-intelligence/559205/)

