Автоматическая генерация тестов
---

Для получения методов с тестами и без анализируется специальная метка в коде:

<code>//#TestMethod: <ИмяМетодаВТесте></code>

Для исключения метода из списка тестируемых необходимо установить значение равное 'none'

<code>//#TestMethod: none</code>

Параметры и возвращаемые значения получаются парсингом описания метода, парсер анализирует строки начинающиеся с '//#'.

Учитывается:

<code>//#  ВидСправочника  - Строка - ВидСправочника</code>

Не учитывается:

<code>//  ВидСправочника  - Строка - ВидСправочника</code>

**ВАЖНО: Параметры методов должны размещаться в одной строке**

  
##Классы

###РаботаСТекстовымиФайлами

###ГенераторТестов

  - `ПолучитьСписокМетодов` - Структура - Список методов. 

    Парсит текст файла с модулем, получает список всех методов и параметров. 
    **ВАЖНО: Параметры берутся только из описания метода**

    Ключи: 

    - Тип - Строка - Процедура/Функция

    - Имя - Строка - Имя метода

    - Экспорт - Булево - Признак экспортного метода

    - Параметры - Структура - Параметры метода

    - Возврат - Структура - Возвращаемые значения функции, если процедура - пустая структура

    - Тест - Строка - Имя тесового метода

  - `ПолучитьСписокМетодовБезТестов` - Структура - Методы без тестов. Тестированию подлежат **экспортные** методы.

  - `ПолучитьСписокМетодовCТестами` - Структура - Методы с указанным методом теста. Тестированию подлежат **экспортные** методы

  - `СоздатьТесты` - Строка - Генерация костяка теста для методов без тестов.

###ГенераторМодулейНаОсновеТестов