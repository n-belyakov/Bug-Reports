# Bug-report 4

## Обновление данных пользователя уже занятыми “email” или “nickname”

### Описание

При попытке обновить данные пользователя с помощью PATH-запроса на эндпоинт /users/{uuid} с телом запроса, содержащим email или nickname, которые уже используются другим пользователем, сервер возвращает код 200 и обновляет данные.

### **Предусловия**

1. Авторизоваться в системе через **Bearer token** 

```jsx
"Authorization": "Bearer eyJhbGciOiJIUzI1NiIsImtpZCI6IldGZlRBQ0hzYUhvQ3VML1MiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhdXRoZW50aWNhdGVkIiwiZXhwIjoxNzE3MTU0ODY1LCJpYXQiOjE3MTY1NTQ4NjUsImlzcyI6Imh0dHBzOi8vbXlrb3RxYm9ja3p2emFjY2N1Ynouc3VwYWJhc2UuY28vYXV0aC92MSIsInN1YiI6IjMzZTM1N2U1LWJhZTEtNDYzMy05ZGY1LWNkNmNkODk0ZjcwNCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwicGhvbmUiOiIiLCJhcHBfbWV0YWRhdGEiOnsicHJvdmlkZXIiOiJnaXRodWIiLCJwcm92aWRlcnMiOlsiZ2l0aHViIl19LCJ1c2VyX21ldGFkYXRhIjp7ImF2YXRhcl91cmwiOiJodHRwczovL2F2YXRhcnMuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3UvMTM4MTUxOTMzP3Y9NCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImZ1bGxfbmFtZSI6Ik5pa2l0YSBCZWx5YWtvdiIsImlzcyI6Imh0dHBzOi8vYXBpLmdpdGh1Yi5jb20iLCJuYW1lIjoiTmlraXRhIEJlbHlha292IiwicGhvbmVfdmVyaWZpZWQiOmZhbHNlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJuLWJlbHlha292IiwicHJvdmlkZXJfaWQiOiIxMzgxNTE5MzMiLCJzdWIiOiIxMzgxNTE5MzMiLCJ1c2VyX25hbWUiOiJuLWJlbHlha292In0sInJvbGUiOiJhdXRoZW50aWNhdGVkIiwiYWFsIjoiYWFsMSIsImFtciI6W3sibWV0aG9kIjoib2F1dGgiLCJ0aW1lc3RhbXAiOjE3MTY1NTQ4NjV9XSwic2Vzc2lvbl9pZCI6ImFkNjFhZmQ4LTkwMTktNDVkZS1iOTk4LTUwMGYzN2NjMDVjMCIsImlzX2Fub255bW91cyI6ZmFsc2V9.aQ26JcXm7Rdo0e4sT1xAJVn2P7NNBfk_K6AKJyTvuS4",
"X-Task-Id": "API-4"
```

1. Отправить **POST** запрос на эндпоинт **`/setup`** для сброса тестовой среды

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/setup

### Шаги

1. Сформировать GET-запрос на получение списка пользователей

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/users

1. Использовать данные двух пользователей, у первого взять “email” или ”nickname”, у второго “uuid”
- **Пользователь 1:** email: "alex@gmail.com"
- **Пользователь 2:** uuid: "6a4bce2a-fee7-47d8-855c-84606e95820d"
1. Сформировать тело запроса с данными **Пользователя 2** из предыдущего шага

```json
{
"email": "alex@gmail.com",
}
```

1. Отправить PATH-запрос на эндпоинт /users, c указанным path-параметром {uuid} и телом запроса из шага 3

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/users/6a4bce2a-fee7-47d8-855c-84606e95820d

### Ожидаемый результат

Сервер возвращает ответ со статус-кодом 409 и сообщением “**User email already taken**”

```json
{
"code": 409,
"message": "User email already taken: [alex@gmail.com](mailto:alex@gmail.com)"
}
```

### Фактический результат

Сервер возвращает ответ со статус-кодом 200 и сообщением с обновленными данными пользователя.

```json
{
    "avatar_url": "",
    "email": "alex@gmail.com",
    "name": "John",
    "nickname": "john",
    "uuid": "6a4bce2a-fee7-47d8-855c-84606e95820d"
}
```

### Окружение

Postman for Windows Version 11.1.14

### Приоритет

P1- Высокий. Ошибка связана с нарушением уникальности данных пользователей, что может привести к серьезным проблемам в работе системы.

### Серьезность

S2 - Критическая. Ошибка приводит к нарушению целостности данных.