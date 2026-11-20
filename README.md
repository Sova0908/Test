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
