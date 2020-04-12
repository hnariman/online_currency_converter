# nariman_m4
M4 project
Проект М4 — онлайн-конвертер валют

Разработать онлайн-конвертер валют, получая актуальные данные с открытого API:

https://ratesapi.io/documentation/

Это API поддерживает следующие валюты:


EUR
CHF
NOK
CAD
RUB
GBP
MXN
CNY
ISK
KRW
HKD
CZK
BGN
BRL
USD
IDR
SGD
PHP
RON
HUF
ILS
THB
SEK
NZD
AUD
DKK
HRK
PLN
TRY


INR
MYR
ZAR
JPY




Для получения данных по курсу валют, вам нужно запросить данные по валютной паре, добавив к URL адресу два сокращения этих валют (без пробелов и разделителей). Пример для пары USD и RUB:

https://api.ratesapi.io/api/latest?base=USD&symbols=RUB

В ответ приходит JSON с объектом. В поле “rates” этого объекта лежит объект пар ключ-значение. По ключу RUB будет находится число — текущий курс на данный момент.

Калькулятор с помощью элементов управления позволяет пользователю выбрать две валюты и сумму конвертации. После выбора калькулятор отображает кросс-курс и итоговую сумму. 

Предусмотреть обработку ошибок загрузки. Использовать webpack для сборки проекта.

Требования

Интерфейс должен соответствовать макету:

https://www.figma.com/file/xnlKM4x2oZR1T5jpt0bzYZ/%D0%9C4-v2?node-id=0%3A1

Для шапки реализована только верстка. К ссылкам и кнопкам не нужно привязывать никаких действий.

Два инпута для ввода валют. Поддерживает ввод цифр и точек, возможен ввод запятой, которая будет конвертироваться в точку при вводе. 

Изначально предзаполнены в следующем формате:
Правое поле заполнено единицей
Левое поле заполняется стоимостью за единицу валюты из правого поля, когда данные будут получены

Около полей доступны кнопки для выбора валют. При нажатии на кнопку со стрелкой, появляется выпадающий список всех валют (сделан при помощи элемента select).
Дополнительное задание: реализовать выпадающее окно со списком всех доступных валют, как в макете.
https://www.figma.com/file/1z9YnEYYOpblCX13X3NlJ1/%D0%9C4-v1?node-id=1%3A2) 

При выборе двух одинаковых валют не нужно делать запрос на сервер. Изначально для левого поля выбирается валюта RUB, для правого — USD (как на макете) 

При загрузке данных на экран накладывается затемнение, а также появляется “Загрузка” (см. макет).

Конвертер отображает курс как меняемой валюты к желаемой, так и желаемой к меняемой.

Есть кнопка-переключатель, позволяющая поменять местами меняемую валюту и желаемую. Значения полей и активная кнопка выбранной валюты также меняются местами.

Проект выполнен в качестве NPM-пакета и собирается с помощью Webpack. Есть NPM-скрипты для сборки проекта в режиме разработки “build” и для итогового использования “build:production”. Проект собирается в папку “/dist” в файл с названием “main.js”. Эта папка и папка node_modules добавлены в файл .gitignore пакета. При вызове команды “build:production” файл “main.js” собирается с поддержкой старых браузеров через Babel и его код минифицирован.

При недоступности API или ошибках при выполнении запроса на него происходит приложение не зависает и не перестает работать, а пользователю выводится сообщение о том, что что-то пошло не так

Дополнительное задание: подключить библиотеку для визуализации данных (например, https://www.chartjs.org/) и вывести график изменения цены по выбранной паре валют за последнюю неделю.



Чеклист

Условие
Да / нет
При загрузке файла проекта наблюдаем на экране необходимые элементы пользовательского интерфейса. В контролах установлены корректные начальные значения. 


Изначально выбраны две валюты: RUB и USD


Слева устанавливаем валюту RUB и значение 100.
Справа устанавливаем валюту USD, значение правого контрола пересчитывается по актуальному курсу к рублю.
Меняем валюту слева на EUR.
Значение правого контрола пересчитывается по актуальному курсу EUR к USD


Слева устанавливаем валюту RUB и значение 100.
Справа устанавливаем валюту USD.
Меняем валюту справа на EUR.
Значение левого контрола пересчитывается по актуальному курсу RUB к EUR
   
Слева устанавливаем валюту RUB и значение 100.
Справа устанавливаем валюту USD, значение правого контрола пересчитывается по актуальному курсу к рублю.
Меняем значение левого контрола на 200
Значение правого контрола пересчитывается по актуальному курсу и становится в два раза больше


Слева устанавливаем валюту RUB и значение 100.
Справа устанавливаем валюту USD, значение правого контрола пересчитывается по актуальному курсу к рублю.
Меняем значение правого контрола на 100
Значение левого контрола пересчитывается по актуальному курсу


Есть кнопка-переключатель, при валютной паре RUB к USD кликая на кнопку получим валютную пару USD к RUB. Правый контрол пересчитает значения по новому курсу.


Проект собран с помощью Webpack, на странице подключен один JavaScript файл “main.js”. Код внутри этого файла минифицирован.


Откройте инструменты разработчика в браузере Chrome. Перейдите во вкладку “Network”, найдите поле ‘Throttling’ (по умолчанию установлено Online) и выберете в нем “Offline”. Нажмите на кнопку-переключатель. Пользователю вывелось сообщение о том, что что-то пошло не так.
Верните  поле ‘Throttling’ на Online и снова нажмите на кнопку-переключатель. Кнопка отработала.


Выполнение дополнительного задания



При проверке каждого пункта мы также убеждаемся, что в консоли отсутствуют сообщения об ошибках.

