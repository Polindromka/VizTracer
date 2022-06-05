# VizTracer
## Список авторов
Имя | Группа | Разделы
| --- | --- | ---
Гуницкий Р. Я. | БПИ195 | <ul><li> Общие архитектурные решения</li><li>Техническое описание отдельных ключевых архитектурных решений</li></ul>
Жупанов В. | БПИ195 |    <ul><li>4.5.	Представление развертывания </li> <li>4.10.	Атрибуты качества системы  </li> <li>4.10.1	Объем данных и производительность системы </li> <li>4.10.2	Гарантии качества работы системы  </li> </ul>
Кулешова П. О. | БПИ195 | 1.	Введение <ul><li>1.1.	Название проекта</li> <li>1.2.	Задействованные архитектурные представления  </li> <li>1.4.	Рамки и цели проекта   </li> <li> 6.	Приложения </li> <li> 6.2.	Ссылки на используемые документы </li> <li> Поиск документации по VizTracer</li> </ul>
Мелехин Д. А. | БПИ192 |2.	Архитектурные факторы  <ul><li>2.1.	Ключевые заинтересованные лица</li> <li>2.2.	Ключевые требования к системе</li> <li> 2.3.	Ключевые ограничения </li> </ul>
Цуркан Д. В. | БПИ195 |4.	Архитектурные представления <ul><li>4.1.	Представление прецедентов  </li> <li>4.2.	Логическое представление </li> <li>4.3.	Представление архитектуры процессов  </li> </ul>
## Регистрация изменений
Версия документа	| Дата	| Описание изменения	| Автор изменения
| --- | --- | --- | ---
1| 25.03.2022| Добавлен вводный раздел документ| Кулешова П.О.
2| 27.03.2022| Добавлены архитектурные факторы| Мелехин Д.А.
3| 27.03.2022| Добавлены архитектурные представления | Цуркан Д. В.
4| 27.03.2022| Добавлено представление развёртывания| Жупанов В.
5| 27.03.2022| Добавлено основные архитектурные решения| Гуницкий Р.Я.
6| 9.04.2022| Добавлены логические представления| Цуркан Д.В.
7| 9.04.2022| Добавлены описания проблем | Кулешова П.О.
8| 15.05.2022| Внесены исправления в код приложения | Кулешова П.О.
9| 15.05.2022| Добавлены ссылки на исправления в Архитектурный документ | Мелехин Д.А.
10| 22.05.2022 | Внесена схема проверки результативности решений | Кулешова П.О.
11| 05.06.2022 | Внесены изменения в алгоритмы записи в файл | Жупанов В.
## Введение
### Название проекта
VizTracer
### Задействованные архитектурные представления
Документ имеет следующую структуру:
- В разделе 1
  - Задействованные архитектурные представления
  - Рамки и цели проекта
- В разделе 3
  - Общие архитектурные решения
- В разделе 2 основные архитектурные факторы
  -   Ключевые и заинтересованные лица
  -   Ключевые требования к системе
  -   Ключевые ограничения
- В разделе 4 Общие архитектурные решения
  -  Представление прецедентов
  -  Логическое представление
  -  Представление архитектуры процессов
  -  Представление развёртывания
  -  Атрибуты качества системы
  -  Объём данных и производительность системы
  -  Гарантии качества работы системы
-  В разделе 5 
  - Техническое описание отдельных ключевых архитектурных решений
### Рамки и цели проекта
VizTracer - это инструмент для ведения журналов, отладки и профилирования с низкими затратами, который может отслеживать и визуализировать код на Python, что помогает лучше понять код и определить трудоемкую кода (части кода).\
VizTracer может отображать каждую выполненную функцию и соответствующее время входа/выхода от начала программы до конца, что помогает выявлять спорадические(случайные) проблемы с производительностью. 
## Архитектурные факторы (цели и ограничения)
### Ключевые и заинтересованные лица
Действующее лицо	| Заинтересованность в системе
| --- | ---
| Разработчик | Разработка поддерживаемой системы соответствующей требованиям; Написание документации;
Заказчик  | Предоставление требований; Установка дедлайнов разработки; Прием конечного продукта
Архитектор ПО | Разработка архитектуры системы
Тестировщик | Тестирование продукта на каждом этапе разработки; Проверка выполнения всех требований;


### Ключевые требования к системе
- Система должна работать на Linux/MacOS/Windows
- Система должна иметь возможность установки через pip3
- Система должна поддерживать Jupyter Notebook
- Система должна уметь профилировать python файл из консоли и записывать результат в файл формата json
- Система должна уметь отображать результат профилирования (из json файла)
- Система должна предоставлять пользователю возможность установки собственного значения размера буффера (Дефолтное значение 150МБ)
- Система должна уметь считывать настройки из конфиг файла
- Система должна иметь возможно дебага файла профилирования из консоли (с помощью команды vdb)
### Ключевые ограничения
- Требуется версия python 3.6 или выше
- При использование WSL1 (Windows Subsystem Linux) невозможна корректная работа системы. Требуется обновление до WSL2
- Система должна быть написана на Python & C/C++

 
## Общие архитектурные решения
Одной из основных архитектурных задач, которую должна решать библиотека viztracer - это ведение журналов, отладки и профилирования кода на Python и отображения результатов в выбранной среде выполнения. Благодаря этому пользователи могут анализировать и оптимизировать свой код. Исполнение вышеупомянутых основных функций выполняется, предварительно проверяя код на соответствие требованиям методами класса VizUI, главным классом библиотеки - viztracer с помощью уточняющих методов в соседних модулях с целью более четкой структуры проекта. Объект библиотеки, находящийся на верхнем уровне и содержащий и управляющий элементами ввода и вывода носит имя VizUI.
 
## Архитектурные представления
В данном разделе подробно описывается каждое из используемых в проекте архитектурных представлений.
### Представление прецендентов
Рассматриваемая система предлагает пользователям детальную информацию о работе скрипта, написанного на языке Python, выступая в качестве помощника при отладке, логировании и профилировании кода. Результат работы системы отвечает на следующий вопрос: “Почему моя программа делает это?”. Основная идея VizTracer – помочь понять, что делает программа. VizTracer фокусируется на стеке вызовов по ходу выполнения кода и может визуализировать каким образом вызываются функции, одна за другой, пока отрабатывает код.

Так как система работает локально на устройстве из актеров можно выделить рядового Python разработчика/аналитика. 

Пользователь должен обладать следующими возможностями использования системы: 

- выполнение скрипта/модуля на языке Python из командной строки с помощью VizTracer (в т. ч. с исходными аргументами)
- получение отчета о ходе выполнения кода, после завершения исполнения, в трех форматах – json, html, gz (управление настройками возможностями системы и фильтрации отчета ложится на аргументы командной строки)
- визуализация процессного времени, потраченного на функции (flamegraph)
- ручной запуск/остановка профилирования в скрипте для отдельных частей кода
- генерация и отображение отчета в Jupyter Notebook
- открытие отчета из командной строки в браузере
- объединение нескольких отчетов, созданных системой 
- удаленное присоединение/отключение к продолжающемуся процессу
- виртуальная отладка программы по сохраненному отчету в формате Json

![Alt text](img/use_cases.jpg?raw=true "Title")


### Логическое представление

![Alt text](img/msg1068871904-37341.jpg?raw=true "Title")

### Представление архитектуры процессов
Основная часть VizTracer написана на чистом C. В среднем выполнение скрипта с помощью VizTracer увеличивается меньше, чем вдвое, по сравнению с выполнение скрипта с помощью Python, а в худшем случае может доходить до тройного увеличения времени выполнения.

В рассматриваемой системе параллелизм является неотъемлемым функционалом, позволяющим выполнять предоставленный скрипт, в том же формате, в котором он был написан. То есть VizTracer способен выполнять предоставленный ему асинхронный код и выводить отчет по каждому процессу. Также VizTracer может визуализировать код, выполняемый в многопоточном формате, с помощью flamegraph. 

Набор основных выполняемых процессов системы:
- Запуск скрипта/модуля, написанного на языке Python из командной строки
- Генерация отчета с помощью open-source инструмента Perfetto
- Присоединение/отключение к запущенному процессу для трассировки кода
- Просмотр сгенерированного отчета с помощью VizTracer

![Alt text](img/sequence_diagram.jpg?raw=true "Title")

### Физическое представление архитектуры
### Представление развёртывания
Так как данный проект представляет собой питоновскую библиотеку, развертывание в данном сервисе не предусмотрено. Библиотека добавляется в pip3 и доступна пользователям для скачивания.\
Весь код проекта находится в открытом репозитории на Github поставляется заказчику в виде пакета, который он устанавливает в виде библиотеки путем выполнения команды «pip install viztracer[full]». Таким образом никаких дополнительных компонентов устанавливаться не придется. \
Обновление системы будет устроено следующим образом: вносятся правки в репозиторий, после чего обновляется библиотека в pip3 и пользователям будет доступна новая версия для скачивания. 
### Атрибуты качества системы
К атрибутам качества системы относятся: надежность, удобство сопровождения, удобство использования, портативность, точность, оцениваемость и способность к взаимодействию.\
Ниже представлена таблица описывающая каждый атрибут в разрезе проекта VizTracer: 
Название	| Описание
| --- | ---
|Надежность	|Так как проект представляет собой библиотеку с отлаженным функционалом, то при любых нагрузках корректность его работы гарантирована.
|Удобство сопровождения	|Проект имеет довольно простую и понятную архитектуру, что позволяет с легкостью поддерживать его.
|Удобство использования	|Так как проект это питоновская библиотека, то сценарии использования абсолютно очевидны и удобны каждому пользователю.
|Портативность	|Проект скачивается командой «pip install viztracer[full]».
|Точность 	|Продукт всецело соответствует заявленным функциональным требованиям, отличается корректностью работы и правильностью отображения пользовательской информации.
|Оцениваемость 	|Система легкотестируема на наличие багов.
|Способность к взаимодействию	|Продукт состоит всего из одной системы.

#### Объём данных и производительность системы
Максимальный объем данных, который программа может хранить - 150 МБ, после превышения данного лемита, данные перезаписываются. Программа хранит в себе данные стека запуска функций,  логирования и аргументов исполняемого кода.\
Код, запущенный с использованием VizTracer, должен отрабатывать за время, не более чем в два раза большее, чем время работы того же кода без использования VizTracer.
#### Гарантии качества работы системы
Так как проект представляет собой питоновскую библиотеку, гарантиями качества является безошибочная работа всех функций библиотеки при условии, что они используются в соответствии с их сигнатурой.\
Безошибочная работа всех функций библиотеки проверяется на определенном массиве сходных данных с заготовленными предполагаемыми результатами работы. На первом этапе проверяется, что функция не «падает» с ошибкой на заготовленных входных данных. На втором этапе сравнивается ожидаемый результат с фактическим.

## Техническое описание отдельных ключевых архитектурных решений
### Техническое описание решения №1
#### Проблема
Выбор языка программирования, на котором будет написан код приложения.
#### Идея решения
Выбрать за основу язык C и Python для "обёртки" функций, вызываемых пользователями.
#### Факторы
Данный язык программирования является наиболее быстрым. Позволяет значительно ускорить выполнение кода программы, относительно других языков. Однако, библиотека предназначена для пользователей питона, поэтому вызов функций должен быть с помощью питона.
#### Решение
Написание библиотеки на C и Python
#### Мотивировка
Для проектирования универсальной программы необходима переносимость и скорость - язык C удовлетворяет данным требованиям. Так как библиотека предназначена для разработчиков на питоне, то "обёртка" библиотеки должна быть на питоне.
#### Неразрешённые вопросы
Нет.
#### Альтернативы
Написать основу на C++, это бы замедлило скорость выполнения кода, однако значительно упростило бы разработку ПО. Язык Python, как основной для разработки не подошёл бы, так является достаточно "медленным" языком программирования. Java является кроссплатформенным языком программирования, однако, уступает по скорости языку С.
## Схема проверки результативности решений
### Проблема с типизацией данных
#### Решение
Добавить явную типизацию данных в модулях для упрощения восприятия кода и вызова внутренних функций.
#### Код
- https://github.com/Polindromka/VizTracer/commit/ce36775b6390e0560600284a39903ae5d4d231a1
- https://github.com/Polindromka/VizTracer/commit/d4ef3a8a3c4c3762078f336bfb163d5a8a7ac961
- https://github.com/Polindromka/VizTracer/commit/33be390f6dc9794c49c9472c8ab2a2927b2cfa2e
- https://github.com/Polindromka/VizTracer/commit/91ca2fd982ad19f2baa7ac227e610cfa5428a8c1
- https://github.com/Polindromka/VizTracer/commit/38d8d07acb63fafa716fcee8fa34fdbbe971a5a7
- https://github.com/Polindromka/VizTracer/commit/0dfad7967316bea3f664ef54413f52c6b9b1cc44
- https://github.com/Polindromka/VizTracer/commit/ba8b475d99654e3e6b81e747965eaaa56501e9bb
#### Оценка результативности
После добавления явной типизации данных код приложения стало проще читать и воспринимать. Соответственно упростилась задача модификации кода и архитектуры приложения. Так как теперь стало понятно какого типа переменные должны быть использованы в приложении. Достаточно часто приложение вызывало переменные внутренних классов или использовало библиотечные функции. Если понимать, переменные какого класса задействованы, то проще понять назначение функции, даже без комментариев. Современные средства разработки, такие как PyCharm, позволяют узнать тип переменной только если ей где-то в функции присваивается значение определённого типа или она используется при вызове функции с строго типизированными аргкментами. \\
После добавления явной типизации код стало проще воспринимать и изменять. Код иможно проверить на встроенных тестах к библиотеке.
### В архитектурном документе не хватает диаграмм для понимания логики взаимодействия
модулей
#### Решение
Для решения проблемы с архитектурным представлением необходимо добавить диаграмму прецендентов и Use-Case.
#### Код
![Alt text](img/sequence_diagram.jpg?raw=true "Title")
![Alt text](img/use_cases.jpg?raw=true "Title")

#### Оценка результативности
После добавления дополнительных архитектурных представлений стало проще воспринимать программу,  как единое целое. По отзывам рецензентов стало проще читать и воспринимать архитектурный документ (дополнительные архитектурные представления были реализованы на этапе предложений П2) 

###  Медленная запись в файл через .json
#### Решение
Для реализации нового подхода в хранении данных планировалось заменить запись в файлы в формате .json на модуль ProtocolBuffers, который отличается скоростью сохранения данных. Однако, в процессе анализа кода, были обнаружены следующие конструкции:
```python
if isinstance(wait, str):
    while True:
        line = p.stdout.readline().decode("utf-8")
        if wait in line:
            time.sleep(0.5)
            break
```
Которые были заменены на более эффективные:
```python
if isinstance(wait, str):
    line = p.stdout.readline().decode("utf-8")
    while wait not in line:
        line = p.stdout.readline().decode("utf-8")
```
#### Код
https://github.com/Polindromka/VizTracer/commit/310195b2b6936a346e48b37295cdf41e4a1636ab
#### Оценка результативности
В результате удалось увеличить скорость почти в 1,5 раза (в 1,47):
![изображение](https://user-images.githubusercontent.com/59918228/172047491-b32e5da7-817f-4a67-93f7-d64f1aa4c05d.png) \ 
Что позволило достичь поставленной цели. Так как код приложения полностью зависит от .json формата и мы не могли использовать protobufer, так как структура json'a всегда разная, нельзя определить какое-то n-ное кол-во структур, которые будут записываться в .json. 
## Приложение
### Ссылки на использованные документы
- [VizTracer репозиторий](https://github.com/gaogaotiantian/viztracer)
- [VizTracer документация для пользователя](https://viztracer.readthedocs.io/en/stable/)
- [VizTracer описание проекта на Medium](https://gaogaotiantian.medium.com/why-you-should-try-viztracer-to-understand-your-python-program-9e08ccbd5e97)
