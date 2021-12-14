Задания для выполнения
Написать простейший веб-сервер. Сервер должен принимать входящие соединения на порту 80 и отдавать пользователю содержимое запрошенного ресурса из определенной директории (рабочей директории сервера).
Разместите в рабочей директории сервера простой веб сайт, содержащий страницу index.html. Убедитесь, что при подключении к серверу, если не указан необходимый ресурс он отдает содержимое страницы index.html.
Познакомьтесь со спецификацией протокола HTTP. Узнайте, в каком формате клиент посылает запрос серверу и в каком формате сервер посылает ответ клиенту. Особое внимание уделите полям заголовка.
Сделайте так, чтобы к вашему серверу можно было обращаться по протоколу HTTP. Для этого не нужно реализовывать поддержку всех возможных нюансов, вам нужно лишь описать общий формат запросов и ответов и поддерживать некоторые поля заголовков.
Проверьте работу вашего сервера, обратившись к нему из адресной строки любого браузера. Для этого достаточно написать в ней адрес хоста, на котором работает сервер (localhost тоже подходит). Вы должны увидеть содержимое (не код) вашей страницы.
Дополнительные задания
При ответе вашего сервера посылайте некоторые основные заголовки:
Date
Content-type
Server
Content-length
Connection: close.
Создайте файл настроек вашего веб-сервера, в котором можно задать прослушиваемый порт, рабочую директорию, максимальный объем запроса в байтах. Можете добавить собственные настройки по желанию.
Если файл не найден, сервер передает в сокет специальный код ошибки - 404.
Сервер должен работать в многопоточном режиме.
Сервер должен вести логи в следующем формате: Дата запроса. IP-адрес клиента, имя запрошенного файла, код ошибки.
Добавьте возможность запрашивать только определенные типы файлов (.html, .css, .js и так далее). При запросе неразрешенного типа, верните ошибку 403.
Реализуйте поддержку постоянного соединения с несколькими запросами.
Реализуйте поддержку бинарных типов данных, в частночти, картинок.

Основной код программы:  ( Отдельно в файле settings прописываем все доступные типы расширений)

![image](https://user-images.githubusercontent.com/92279258/146086411-0ffed314-504a-4d96-bbba-b1351caac3f6.png)

![image](https://user-images.githubusercontent.com/92279258/146086449-198922b6-ee87-4a20-bdb4-a7d2bfb8d5a3.png)


![image](https://user-images.githubusercontent.com/92279258/146091610-454dd487-21bd-469a-ab24-8c02bf0fca00.png)


![image](https://user-images.githubusercontent.com/92279258/146086515-15f8e460-0c2b-4a5c-8f04-00ca050b28e2.png)

Создайте файл настроек вашего веб-сервера, в котором можно задать прослушиваемый порт, рабочую директорию, максимальный объем запроса в байтах. Можете добавить собственные настройки по желанию. Файл настроек в формате JSON - скрин функции работы с файлом json

![image](https://user-images.githubusercontent.com/92279258/146091848-947a1085-bc9d-47ed-8fd8-4d9a2447d7fe.png)

Если файл не найден, сервер передает в сокет специальный код ошибки - 404.

![image](https://user-images.githubusercontent.com/92279258/146092015-f0662cd0-8281-4c02-af4f-0ac076881f8e.png)

Если ошибок не возникает - то осуществляется успешное открытие файла index.html 

Запуск index.html:

![image](https://user-images.githubusercontent.com/92279258/146092557-af8f88b3-9112-47c2-ae8e-6639ac4d8f2f.png)

Проверка корректного запуска всех изображений с разным расширением, (все доступные расширения прописаны в settings.py, скрин приложен выше)
Запуск image.jpg:

![image](https://user-images.githubusercontent.com/92279258/146093478-5c9b9668-e815-4507-b9bd-d3e2bbca7c05.png)
Запуск image.png:

![image](https://user-images.githubusercontent.com/92279258/146093501-d484ddc3-6503-4fe4-946e-f9bce4585d6a.png)
Запуск image.gif:

![image](https://user-images.githubusercontent.com/92279258/146093545-02338e55-aeed-416c-957d-8ee260c80973.png)

Функция для  выведения ошибок 404 и 403 - 
Если файл не найден, сервер передает в сокет специальный код ошибки - 404.
Сервер должен работать в многопоточном режиме.
При запросе неразрешенного типа, вовращаем  ошибку 403.
Что будет - если запустить html, которого нет в директории:

![image](https://user-images.githubusercontent.com/92279258/146092738-f9707b14-f7d3-40f5-b059-ee11d7d39739.png)

Если запустить cтраницу с разрешением, которго нет в типах (settings.py) , но при этом в директории есть 403.html:

![image](https://user-images.githubusercontent.com/92279258/146092866-3927cd11-858c-465f-a771-df735c04d481.png)

Если запустить html, которого нет в директории, но  при этом в директории есть 404.html:

![image](https://user-images.githubusercontent.com/92279258/146092990-d0de9ccc-74db-4959-958e-cf1251d38685.png)








