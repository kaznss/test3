


Доработка: Business Room Rental





Системный аналитик: Емашева Анна



















Оглавление
1. Цель доработки	3
2. Ограничения	4
3. Функциональная архитектура	5
4.Функциональные требования	6
4.1. Сервис Rental Parameters	6
4.2. Сервис Rental Busy	7
4.3. Сервис Extra Service	8
4.4. Сервис Rental Selection	9




       1. Цель доработки
Создание микросервисной архитектуры для сервиса аренды конференц-залов


       2. Ограничения






















       3. Функциональная архитектура


 











       4.Функциональные требования
           4.1. Сервис Rental Parameters

Роли сервиса в системе:
    • Поставщик
    • Потребитель
Наличие API: Да
Предоставляемая сущность(объект): Залы для аренды
Сервисы-потребители API:
    • Rental Selection
4.1.1. Список функций (API)
Название
Расшифровка
create
Добавление нового зала
update
Обновление параметров зала
delete
Удаление зала
getRooms
Запрос списка всех залов
getService
Запрос списка доп.услуг по конкретному залу
getBusy
Запрос занятости по конкретному залу
getPhoto
Запрос фотографий зала

4.1.2 Требования к БД
БД Rooms должна состоять из одной таблицы Rooms (сущность “Залы для аренды”) и содержать следующую структуру
Название поля
Формат
Расшифровка
Id
Целое
Уникальный идентификатор зала
Name
Строка
Название зала
address
Строка
Адрес зала
phone
Строка
Телефон
email
Строка
Почтовый адрес
photo
Флаг
Флаг наличия фотографий зала
area
Целое
Площадь
capacityMin
Целое
Вместимость от
capacityMax
Целое
Вместимость до
doorIn
Флаг
Флаг наличия отдельного входа
foodGo
Флаг
Флаг возможности заказа еды
priceMin
Целое
Стоимость c оборудованием
priceMax
Целое
Стоимость без оборудования




           4.2. Сервис Rental Busy
Роли сервиса в системе: 
    • Поставщик
Наличие API: Да
Предоставляемая сущность(объект): Бронирование зала
Сервисы-потребители API:
    • Rental Selection
4.2.1. Список функций (API)
Название
Расшифровка
bookingIn
Бронирование зала
bconfirmation 
Подтверждение брони
invoiceStep
Флаг оплаты брони зала
bkProlong
Продление брони зала
bookingOut
Снятие брони с зала
getBkFull
Запрос занятости всех залов
getBkRoom
Запрос дат занятости конкретного зала
getBuzy
Запрос занятых залов
getFree
Запрос незанятых залов

4.2.2 Требования к БД
БД Busy должна состоять из одной таблицы Busy (сущность “Клиенты отеля”) и содержать следующую структуру
Название поля
Формат
Расшифровка
Id
Целое
Уникальный идентификатор зала
buzyDate
Флаг
Флаг занятости на выбранную дату
firstDate
Дата
Занят с даты
lastDate
Дата
Занят по дату



           4.3. Сервис Extra Service
Роли сервиса в системе: 
    • Поставщик
    • Потребитель
Наличие API: Да
Предоставляемая сущность(объект): Продукт (услуга)
Сервисы-потребители API:
    • Rental Parameters

4.3.1. Список функций (API)
Название
Расшифровка
create
Добавление новой услуги
update
Обновление параметров услуги
delete
Удаление услуги
getProducts
Получение списка возможных доп.услуг

4.3.1 Требования к БД
БД Service должна состоять из одной таблицы products и содержать следующую структуру
Название поля
Формат
Расшифровка
id
Целое
Уникальный идентификатор услуги
product
Строка
Наименование услуги
rooms
Строка
В каких залах доступна
price
Дробное
Цена
comments
Строка
Комментарий







           4.4. Сервис Rental Selection
Роли сервиса в системе:
    • Потребитель
Наличие API: Нет
Предоставляемая сущность (объект): Нет
Сервисы-потребители API: Нет
4.5.1. Список функций (API)
Нет
4.5.2 Требования к БД
Нет
