# DegreesMinutesSeconds

Для автоматизации расчётов, связанных с решением геодезических задач и камеральной обработкой результатов съёмки местности, используются электронные таблицы, в том числе Microsoft  Excel. Но не все вычисления можно произвести с использованием стандартного функционала, представленного в редакторе.

В Excel  отсутствует функционал вычисления со значениями градусов, минут и секунд. Необходимо ввести формулу со ссылками на отдельные ячейки, содержащие значения соответственно градусов, минут и секунд, для того, чтобы получить значение, выраженное в десятичном представлении градусов (только в таком формате Excel  может обрабатывать эти значения). Также чтобы Excel  производил расчёты корректно, нужно переводить градусы в радианы.

После вычислений с градусами, могут потребоваться и обратные преобразования – из радианов в десятичное представление градусов, а затем в градусы, минуты и секунды, для чего потребуется отдельно в каждую из трёх ячеек вписать формулу, содержащую функцию ОТБР, которая отбрасывает дробную часть числа.

Все эти преобразования сопровождаются вводом минимум семи формул (без учёта самих вычислений), что замедляет процесс расчётов. Особенно это заметно при обработке диапазонов с десятками, а иногда и сотнями ячеек – если речь идёт о многоэтапных вычислениях, алгоритм установки ссылки на ячейки может меняться, и формулы придётся редактировать неоднократно.
![](https://sun9-11.userapi.com/impg/ECaXPk0ahVkLeZyTNPPoFpfRxqpyk0oYYYqgJQ/BK2hrAPilYg.jpg?size=1024x1024&quality=96&sign=d33df6a085ce53bcdec9c176f267b099)

**Надстройка DegreesMinutesSeconds упрощает преобразования значений, представленных в градусах, минутах и секундах, в радианы и наоборот. Значения градусов, минут и секунд записываются в одну ячейку и переводятся в радианы и обратно буквально парой кликов!**

## Алгоритм решения

### **Основная процедура «DMS»**

Получает выделенный диапазон ячеек, вставляет новый столбец справа от первой ячейки в выделенном диапазоне и выводит результат в новый столбец.

### **Логика преобразования:**
Проверяет, содержит ли значение в ячейке пробелы.

Если да, и значение находится в пределах от -6.28319 до 6.28319 (радианы), то оно преобразуется градусы, минуты и секунды с помощью функции RadiansToDms.

Если значение содержит пробелы (выражено в градусах, минутах и секундах), оно преобразуется в радианы с помощью функции DmsToRadians, а новой ячейке присваивается числовой формат с 14 знаками после запятой.

### **Функция 1: Преобразование градусов, минут и секунд в радианы «DmsToRadians»**

Макрос преобразует строку в формате DMS в радианы. Для этого значение в ячейке разбивается на части (градусы, минуты, секунды) с помощью функции Split, после чего преобразовывается в десятичные градусы, а затем в радианы с помощью функции РАДИАНЫ из Excel.

### **Функция 2: Преобразование радианов в градусы, минуты и секунды «RadiansToDms»**
Макрос преобразует радианы в DMS. Сначала он преобразует радианы в десятичные градусы, затем вычисляет минуты и секунды (последние округляются до целого значения), после чего выводит результат в строку в формате DMS.

## Стек  технологий:

**Язык:** VBA (Visual Basic for Applications)

**Окружение:**  Microsoft  Excel (любая версия)

## **ПОДГОТОВКА К РАБОТЕ С НАДСТРОЙКОЙ**

**1. Скачайте файл с надстройкой**

**2. Запустите Excel и откройте книгу с расчётами. Чтобы добавить надстройку, необходима вкладка «Разработчик».**

**Если вкладка уже отображается на ленте, переходите к п. 6. Если нет – необходимо её добавить.  Для этого зайдите в меню «Файл».**
![](https://sun9-67.userapi.com/impg/egmovoaViEhxIDFybjRjelTiPKlxFmS6HQM4_g/d3OroxSyPsE.jpg?size=1801x766&quality=95&sign=56172d95b2e1c8bd2534945e3eff55c6)

**3. Перейдите в «Параметры».**
![](https://sun9-24.userapi.com/impg/We5GNI96mHj5XjVZcCfrzUWE5lLfwytXwy5BfQ/K5fK2myoCuI.jpg?size=568x785&quality=95&sign=b6c98c22a53a68da3bee818b6913470d)

**4. Перейдите в пункт «Настройка ленты»**
![](https://sun9-39.userapi.com/impg/7IqcEIK8012UbAPcZ3ZN13gwmRkyCseq394zFA/pnSk6mgaZYQ.jpg?size=471x761&quality=95&sign=ef747e849ff2f52203f972daf8938ad6)

**5. Поставьте галочку на пункте «Разработчик», нажмите «ОК», и в ленте появится новая вкладка.**
![](https://sun9-60.userapi.com/impg/43e9EDG4yHV2rMq1iN3OghsUOmU2NmN_zSBxrA/oH7cuvGxcmg.jpg?size=1067x776&quality=95&sign=abb86b6f22ca4fbac4ffcfb2ca1c8b05)

**6. Во вкладке «Разработчик» перейдите в «Надстройки»** (в Excel 2013 и новее «Надстройки Excel»)
![](https://sun9-75.userapi.com/impg/_le7WaabLXwGIJ3Wy-tmFxC-j144eeW286mbHg/Kk9uTi-xlgw.jpg?size=806x171&quality=95&sign=e553560b66eb0755359b9850b0b49bcf)

**7. Нажмите «Обзор…»**
![](https://sun9-33.userapi.com/impg/krEsaW1VxD5Vpe2FXWHRaJKd0s4QDWlv7NywfA/ftx8-x8FBoA.jpg?size=389x445&quality=95&sign=480e81b24b2ee0c9dec7e5014e15d0e2)

**8. Выберите загруженный ранее файл, и надстройка появится в списке доступных.**
![](https://sun9-25.userapi.com/impg/tVQJn4HO3M8ewBhpB39ip-fGIN642BQ37GRo8A/hAqo7ubeiec.jpg?size=944x768&quality=95&sign=620b5b3d6c01d89e703db61f78dc4e1e)

**9. Далее можно задать сочетание клавиш для работы с надстройкой. Для этого перейдите в «Макросы».**
![](https://sun9-9.userapi.com/impg/mDixaDdQjHN6mZrYdz9rU7kaKs_kJ3PsaBJCIw/i1zwWfaO5BQ.jpg?size=807x171&quality=95&sign=248d242cd429af118c9f529428e773ba)

**10. В поле поиска введите название надстройки и перейдите в «Параметры»**
![](https://sun9-28.userapi.com/impg/OrCzZExtSChn2k_MYsoU9pyeJfRhOhSil_X6PQ/vGgnSWxzv_w.jpg?size=502x438&quality=95&sign=e8b3c83826e3307f1e7c3a156a737924)

**11. Назначьте удобное вам сочетание клавиш (например, Ctrl + d).**
![](https://sun9-72.userapi.com/impg/J5xCH139_tOx_oPGTHqB_3tF-UFIfSvQnf_yZQ/NGItsO8UbSc.jpg?size=434x295&quality=95&sign=d15176de03868b7a87309d4a5a73a5c0)

## **ИНСТРУКЦИЯ К ИСПОЛЬЗОВАНИЮ**

**1. Введите в ячейку значение градусов, минут и секунд через пробел**

>**ПРИМЕЧАНИЕ**
Если значение отрицательное, перед знаком «минус» поставьте одинарную кавычку.

![](https://sun9-16.userapi.com/impg/HIyLIFY1pZ7Z28TyvzjDiJsMycTUDRuQAMC6kw/p39mw6A-anM.jpg?size=356x445&quality=95&sign=6b4851d9b44b71f99d64bf4e45c6df09)

**2. Выделите ячейку (диапазон ячеек), нажмите назначенное ранее сочетание клавиш, и справа появится значение в радианах.**
![](https://sun9-39.userapi.com/impg/0jv__9_MfDJVVJ1b-ObfqHOeFnu3bw8AV4QKyw/WbqJ8D-gQDI.jpg?size=563x374&quality=95&sign=ac22e5c66889f6ff48b8a354fb3f00ec)

**3. Теперь можно ссылаться на эту ячейку при вводе формул с переменными, выраженными в других единицах измерения**

В примере ниже вводится формула для вычисления расстояния. В результате получается значение метрах, не нуждающееся в дальнейших преобразованиях
![](https://sun9-2.userapi.com/impg/YC_NG_vlT4KGpGPSzuI_8Sl3tC_ymRPGsRyitw/XABIiNOxYQM.jpg?size=770x503&quality=95&sign=4be35fe2c2b968184e76d0d104d2b396)

Если необходимо произвести расчёт только со значениями градусов, минут и секунд, ссылайтесь на ячейки, содержащие соответствующие значения в радианах. Результатом будет значение в радианах, которое, можно преобразовать.

Нажмите назначенное ранее сочетание клавиш, и справа появится значение в градусах, минутах и секундах.
![](https://sun9-57.userapi.com/impg/8YuCCmi9UiNwF7afx1lliwWzuy0HFszu9y2UEg/RntKBkOVjQU.jpg?size=846x486&quality=95&sign=b0eb56826e4e7e5334b8242bc01eaa9f)



## ***[Polina-Pash (github.com)](https://github.com/Polina-Pash)***
