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

#### Предобработка. Улучшение качества изображения

Старый шрифт, пятна от кофе или чернил, заломы бумаги понижают шансы OCR.

Если исходное отсканированное изображение идеально, то все черное — это символы, а все белое — фон.

#### Распознавание

Сначала OCR-программа объединяет пиксели в возможные буквы, а буквы — в возможные слова. Затем система сопоставляет варианты слов со словарем. 

Если слово найдено, оно отмечается как распознанное. 

Если слово не найдено, программа предоставляет наиболее вероятный вариант и, соответственно, качество распознавания будет не таким высоким.

#### Постобработка

Некоторые программы дают возможность просмотреть и исправить ошибки. 

Для этого они используют встроенную проверку орфографии и выделяют неверно написанные слова, что может указывать на неправильное распознавание. 

Продвинутые OCR-программы используют так называемый метод поиска соседа, чтобы найти слова, которые часто встречаются рядом. 
Этот метод позволяет исправить неверно распознанное словосочетание «тающая собака» на «лающая собака».

Кроме того, некоторые проекты, которые занимаются оцифровкой и распознаванием текстов, прибегают к помощи волонтеров: распознанные тексты выкладываются в открытый доступ для вычитки и проверки ошибок распознавания.

### Особые случаи

#### Иероглифы

![](https://github.com/alexdyul/Transkribus/blob/master/Japan.png)

#### Старые/уникальные шрифты

[FineReader XIX](https://www.abbyy.com/ru-ru/ocr-sdk/key-features/ocr) — для старых документов, книг и газет, напечатанных с 1600 по 1937 годы на английском, французском, немецком, итальянском и испанском языках старыми шрифтами, среди которых Fraktur, Schwabacher и Gothic 



## Проблемы работы с рукописными текстами

Рукопечатный текст (ICR) - такое правда существует. [Тут](https://www.abbyy.com/ru-ru/ocr-sdk/key-features/ocr) доказательства 

![](https://github.com/alexdyul/Transkribus/blob/master/Htext.png)


## Исторические кейсы и первые опыты автоматического транскрибирования рукописей

## Современные программы и принципы распознавания рукописного текста (HTR). Посмотрим, что действительно работает.



#### [Google Lens](https://lens.google.com). Рукописный текст

![](https://github.com/alexdyul/Transkribus/blob/master/Google_H.gif)

#### Google Lens. Печатный текст

![](https://github.com/alexdyul/Transkribus/blob/master/Google_T.gif)


[Образцы текста + инструкция на русском](https://drive.google.com/open?id=14b0I4bPHHPkkY_uN2V_S-baC3G404SYp)

## Источники:

[Системный блокъ. Из пикселей — в буквы: как работает распознавание текста](https://sysblok.ru/knowhow/iz-pikselej-v-bukvy-kak-rabotaet-raspoznavanie-teksta)

[Wikipedia. Optical character recognition](https://en.wikipedia.org/wiki/Optical_character_recognition)

[Abbyy. Полный набор технологий распознавания](https://www.abbyy.com/ru-ru/ocr-sdk/key-features/ocr)

[Robo-hunter. Как работают нейронные сети: о сложной системе простыми словами](https://robo-hunter.com/news/kak-rabotayt-neironnie-seti-o-slojnoi-sisteme-prostimi-slovami14200)

