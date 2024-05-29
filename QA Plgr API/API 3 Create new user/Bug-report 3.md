# Bug-report 3

## Не сохраняется значение поля “nickname” при создании нового пользователя

### Описание

При отправке POST-запроса на эндпоинт /users  с телом запроса, содержащим данные нового пользователя, сервер не сохраняет значение поля “nickname”. В результате чего, в ответе сервера, а также в списке пользователей, поле “nickname” остается пустым.

### **Предусловия**

1. Авторизоваться в системе через **Bearer token** 

```jsx
"Authorization": "Bearer eyJhbGciOiJIUzI1NiIsImtpZCI6IldGZlRBQ0hzYUhvQ3VML1MiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhdXRoZW50aWNhdGVkIiwiZXhwIjoxNzE3MTU0ODY1LCJpYXQiOjE3MTY1NTQ4NjUsImlzcyI6Imh0dHBzOi8vbXlrb3RxYm9ja3p2emFjY2N1Ynouc3VwYWJhc2UuY28vYXV0aC92MSIsInN1YiI6IjMzZTM1N2U1LWJhZTEtNDYzMy05ZGY1LWNkNmNkODk0ZjcwNCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwicGhvbmUiOiIiLCJhcHBfbWV0YWRhdGEiOnsicHJvdmlkZXIiOiJnaXRodWIiLCJwcm92aWRlcnMiOlsiZ2l0aHViIl19LCJ1c2VyX21ldGFkYXRhIjp7ImF2YXRhcl91cmwiOiJodHRwczovL2F2YXRhcnMuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3UvMTM4MTUxOTMzP3Y9NCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImZ1bGxfbmFtZSI6Ik5pa2l0YSBCZWx5YWtvdiIsImlzcyI6Imh0dHBzOi8vYXBpLmdpdGh1Yi5jb20iLCJuYW1lIjoiTmlraXRhIEJlbHlha292IiwicGhvbmVfdmVyaWZpZWQiOmZhbHNlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJuLWJlbHlha292IiwicHJvdmlkZXJfaWQiOiIxMzgxNTE5MzMiLCJzdWIiOiIxMzgxNTE5MzMiLCJ1c2VyX25hbWUiOiJuLWJlbHlha292In0sInJvbGUiOiJhdXRoZW50aWNhdGVkIiwiYWFsIjoiYWFsMSIsImFtciI6W3sibWV0aG9kIjoib2F1dGgiLCJ0aW1lc3RhbXAiOjE3MTY1NTQ4NjV9XSwic2Vzc2lvbl9pZCI6ImFkNjFhZmQ4LTkwMTktNDVkZS1iOTk4LTUwMGYzN2NjMDVjMCIsImlzX2Fub255bW91cyI6ZmFsc2V9.aQ26JcXm7Rdo0e4sT1xAJVn2P7NNBfk_K6AKJyTvuS4",
"X-Task-Id": "API-3"
```

1. Отправить **POST** запрос на эндпоинт **`/setup`** для сброса тестовой среды

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/setup

### Шаги

1. Сформировать POST-запрос с телом в формате JSON

```jsx
{
"email": "[d2.utime@yandex.ru](mailto:d2.utime@yandex.ru)",
"password": "veryhardpass",
"name": "Nik",
"nickname": "Nik"
}
```

1. Отправить POST-запрос на эндпоинт /users с телом запроса

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/users

### Ожидаемый результат

Статус код 200. Поля ответа соответствуют ожидаемым полям ответа из документации и содержат данные из запроса. Включая поле “nickname”.

### Фактический результат

Статус-код 200. В ответе сервера поле nickname остается пустым.

```jsx
{
"avatar_url": "",
"email": "[d2.utime@yandex.ru](mailto:d2.utime@yandex.ru)",
"name": "Nik",
"nickname": "",
"uuid": "32cc9027-2891-412b-ae83-4e03f5a14a14"
}
```

### Окружение

Postman for Windows Version 11.1.14

### Приоритет

P1 - Высокий. Ошибка связана с некорректным сохранением данных пользователя, что может негативно повлиять на работу других функций системы, использующих данное поле.

### Серьезность

S2 - Критическая. Ошибка приводит к потере данных.