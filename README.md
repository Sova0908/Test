# Test
Баг 1. Логин пускает с пустыми полями

Где: the-internet.herokuapp.com/login, Chrome 130, Windows 11

Шаги:

    Открыть /login

    Ничего не вводить

    Жать «Login»

Что случилось: форма улетает на сервер, ошибка «Your username is invalid!». Клиентской проверки нет.

Что должно быть: либо кнопка неактивна, либо «Username is required» без запроса на сервер.

Severity: Minor | Priority: Medium

Баг 2. Чекбоксы сбрасываются после F5

Где: /checkboxes, Firefox 131, macOS

Шаги:

    Открыть /checkboxes

    Поставить галочку на первом, снять со второго

    F5

Что случилось: всё вернулось как было по умолчанию.

Что должно быть: выбор сохраняется после перезагрузки.

Severity: Major | Priority: Medium

Баг 3. Дропдаун показывает не то, что выбрал

Где: /dropdown, Edge 130, Windows 10

Шаги:

    Открыть /dropdown

    Выбрать «Option 2»

Что случилось: в поле видно «Option 1», хотя в DOM value="2". В Chrome повторяется, в Firefox — нет.

Что должно быть: показывается «Option 2».

Severity: Major | Priority: High

Баг 4. Двойной клик по Delete оставляет фантом

Где: /add_remove_elements/, Chrome 130

Шаги:

    Нажать «Add Element» 3 раза

    Быстро дважды кликнуть по первой «Delete»

    В консоли: document.querySelectorAll('#elements button').length

Что случилось: визуально 2 кнопки, в DOM — 3. Счётчик сбивается.

Что должно быть: удаляется ровно один, в DOM остаётся 2.

Severity: Major | Priority: Medium

Баг 5 (API). Неверный пароль — а токен всё равно дают

Где: POST /api/login, Postman

Запрос:
json

{ "username": "test_user", "password": "WrongPassword!" }

Что случилось: приходит 200 OK + валидный JWT + данные юзера. Токен потом спокойно проходит на /api/profile.

Что должно быть: 401 Unauthorized + {"error":"invalid_credentials"}, без токена.

Severity: Critical | Priority: High
