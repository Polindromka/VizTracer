# VizTracer
## Список авторов
Имя | Группа | Разделы
| --- | --- | ---
Гуницкий Р. Я. | БПИ195 |
Жупанов В. | БПИ195 |
Кулешова П. О. | БПИ195 |
Мелехин Д. А. | БПИ192 |2.	Архитектурные факторы  <ul><li>2.1.	Ключевые заинтересованные лица</li> <li>2.2.	Ключевые требования к системе</li> <li> 2.3.	Ключевые ограничения </li> </ul>
Цуркан Д. В. | БПИ195 |
## Регистрация изменений
Версия документа	| Дата	| Описание изменения	| Автор изменения
| --- | --- | --- | ---
01|
02|
03|
## Введение
### Название проекта
VizTracer
### Задействованные архитектурные представления
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
### Принципы проектирования
 
## Архитектурные представления
### Представление прецендентов
### Логическое представление
### Представление архитектуры процессов
### Физическое представление архитектуры
### Представление развёртывания
Производить развертывание наших сервисов мы решили в Kubernetes.\
Так как данный проект представляет собой питоновскую библиотеку, развертывание в данном сервисе не предусмотрено. Библиотека добавляется в pip3 и доступна пользователям для скачивания.\
Весь код проекта находится в открытом репозитории на Github поставляется заказчику в виде пакета, который он устанавливает в виде библиотеки путем выполнения команды «pip install viztracer[full]». Таким образом никаких дополнительных компонентов устанавливаться не придется. \
Обновление системы будет устроено следующим образом: вносятся правки в репозиторий, после чего обновляется библиотека в pip3 и пользователям будет доступна новая версия для скачивания. 

### Представление архитектуры данных
### Представление архитектуры безопасности
### Представление реализации и разработки
### Представление производительности
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
#### Идея решения
#### Факторы
#### Решение
#### Мотивировка
#### Неразрешённые вопросы
#### Альтернативы
 
## Приложение
### Словарь терминов
### Ссылки на использованные документы
- [VizTracer репозиторий](https://github.com/gaogaotiantian/viztracer)
- [VizTracer документация для пользователя](https://viztracer.readthedocs.io/en/stable/)
- [VizTracer описание проекта на Medium](https://gaogaotiantian.medium.com/why-you-should-try-viztracer-to-understand-your-python-program-9e08ccbd5e97)
### Определения
### Другое
