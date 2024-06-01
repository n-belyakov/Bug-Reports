# Bug-report 1

## DELETE метод возвращает 500 Internal Server Error при попытке удалить пользователя

### Описание

При попытке удалить пользователя с помощью DELETE запроса на эндпоинт /users/{uuid}, сервер возвращает ошибку 500 Internal Server Error вместо ожидаемого статуса 204 No Content.

### Шаги

1. Авторизоваться в системе через Bear token

```jsx
"Authorization": "Bearer eyJhbGciOiJIUzI1NiIsImtpZCI6IldGZlRBQ0hzYUhvQ3VML1MiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhdXRoZW50aWNhdGVkIiwiZXhwIjoxNzE3MTU0ODY1LCJpYXQiOjE3MTY1NTQ4NjUsImlzcyI6Imh0dHBzOi8vbXlrb3RxYm9ja3p2emFjY2N1Ynouc3VwYWJhc2UuY28vYXV0aC92MSIsInN1YiI6IjMzZTM1N2U1LWJhZTEtNDYzMy05ZGY1LWNkNmNkODk0ZjcwNCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwicGhvbmUiOiIiLCJhcHBfbWV0YWRhdGEiOnsicHJvdmlkZXIiOiJnaXRodWIiLCJwcm92aWRlcnMiOlsiZ2l0aHViIl19LCJ1c2VyX21ldGFkYXRhIjp7ImF2YXRhcl91cmwiOiJodHRwczovL2F2YXRhcnMuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3UvMTM4MTUxOTMzP3Y9NCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImZ1bGxfbmFtZSI6Ik5pa2l0YSBCZWx5YWtvdiIsImlzcyI6Imh0dHBzOi8vYXBpLmdpdGh1Yi5jb20iLCJuYW1lIjoiTmlraXRhIEJlbHlha292IiwicGhvbmVfdmVyaWZpZWQiOmZhbHNlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJuLWJlbHlha292IiwicHJvdmlkZXJfaWQiOiIxMzgxNTE5MzMiLCJzdWIiOiIxMzgxNTE5MzMiLCJ1c2VyX25hbWUiOiJuLWJlbHlha292In0sInJvbGUiOiJhdXRoZW50aWNhdGVkIiwiYWFsIjoiYWFsMSIsImFtciI6W3sibWV0aG9kIjoib2F1dGgiLCJ0aW1lc3RhbXAiOjE3MTY1NTQ4NjV9XSwic2Vzc2lvbl9pZCI6ImFkNjFhZmQ4LTkwMTktNDVkZS1iOTk4LTUwMGYzN2NjMDVjMCIsImlzX2Fub255bW91cyI6ZmFsc2V9.aQ26JcXm7Rdo0e4sT1xAJVn2P7NNBfk_K6AKJyTvuS4",
"X-Task-Id": "API-1"
```

2. Отправить **POST** запрос на эндпоинт ”setup”

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/setup

3. Отправить GET запрос на эндпоинт /users для получения списка пользователей

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/users

4. Выбрать пользователя с uuid равным "d6098dd7-f60d-4495-9571-e9081df02a13”
5. Отправить DELETE запрос на эндпоинт 

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/users/d6098dd7-f60d-4495-9571-e9081df02a1

### Ожидаемый результат

Сервер возвращает пустой ответ со статусом 204 No Content

### Фактический результат

Сервер возвращает ответ:

`{
    "code": 500,
    "message": "Internal server error"
}`

### Окружение

Postman for Windows Version 11.1.14

### Приоритет

P1 - Высокий, так как ошибка блокирует тестирование функциональности удаления пользователей и может привести к невозможности управления пользователями в системе

### **Серьезность**

S2 - Критическая, так как ошибка 500 свидетельствует о серьезной проблеме на сервере, которая может повлиять на работу других функций системы

### Приложение

Ссылка на Postman Collection: 

[API 1 delete user | API testing](https://www.postman.com/science-cosmonaut-75965667/workspace/api-testing/folder/28095965-d25bc4ef-9439-428e-83f4-baeb47a53109?action=share&source=copy-link&creator=28095965&active-environment=c26c9641-54d8-492a-9edd-de95192106e8)
