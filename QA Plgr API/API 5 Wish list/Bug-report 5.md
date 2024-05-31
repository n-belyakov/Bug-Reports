# Bug-report 5

## Ошибка “Wishlist limit is reached” при добавлении игры в пустой список желаний

### Описание

При попытке добавить игру в список желаний пользователя, сервер возвращает код 422 Unprocessable Entity с сообщением "Wishlist limit is reached: 10”, несмотря на то, что список желаний пользователя пустой.

### **Предусловия**

1. Авторизоваться в системе через **Bearer token** 

```jsx
"Authorization": "Bearer eyJhbGciOiJIUzI1NiIsImtpZCI6IldGZlRBQ0hzYUhvQ3VML1MiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhdXRoZW50aWNhdGVkIiwiZXhwIjoxNzE3MTU0ODY1LCJpYXQiOjE3MTY1NTQ4NjUsImlzcyI6Imh0dHBzOi8vbXlrb3RxYm9ja3p2emFjY2N1Ynouc3VwYWJhc2UuY28vYXV0aC92MSIsInN1YiI6IjMzZTM1N2U1LWJhZTEtNDYzMy05ZGY1LWNkNmNkODk0ZjcwNCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwicGhvbmUiOiIiLCJhcHBfbWV0YWRhdGEiOnsicHJvdmlkZXIiOiJnaXRodWIiLCJwcm92aWRlcnMiOlsiZ2l0aHViIl19LCJ1c2VyX21ldGFkYXRhIjp7ImF2YXRhcl91cmwiOiJodHRwczovL2F2YXRhcnMuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3UvMTM4MTUxOTMzP3Y9NCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImZ1bGxfbmFtZSI6Ik5pa2l0YSBCZWx5YWtvdiIsImlzcyI6Imh0dHBzOi8vYXBpLmdpdGh1Yi5jb20iLCJuYW1lIjoiTmlraXRhIEJlbHlha292IiwicGhvbmVfdmVyaWZpZWQiOmZhbHNlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJuLWJlbHlha292IiwicHJvdmlkZXJfaWQiOiIxMzgxNTE5MzMiLCJzdWIiOiIxMzgxNTE5MzMiLCJ1c2VyX25hbWUiOiJuLWJlbHlha292In0sInJvbGUiOiJhdXRoZW50aWNhdGVkIiwiYWFsIjoiYWFsMSIsImFtciI6W3sibWV0aG9kIjoib2F1dGgiLCJ0aW1lc3RhbXAiOjE3MTY1NTQ4NjV9XSwic2Vzc2lvbl9pZCI6ImFkNjFhZmQ4LTkwMTktNDVkZS1iOTk4LTUwMGYzN2NjMDVjMCIsImlzX2Fub255bW91cyI6ZmFsc2V9.aQ26JcXm7Rdo0e4sT1xAJVn2P7NNBfk_K6AKJyTvuS4",
"X-Task-Id": "API-5"
```

1. Отправить **POST** запрос на эндпоинт **`/setup`** для сброса тестовой среды

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/setup 

### Шаги

1. Получить список всех пользователей с помощью GET-запроса

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/users 

1. Выбрать пользователя с “uuid” равным 3779ba46-8ca8-433b-8b86-1b4384dc8554 .
2. Получить список всех игр с помощью GET-запроса

[https://dev-gs.qa-playground.com/api/v1/games](https://dev-gs.qa-playground.com/api/v1/games) 

1. Выбрать игру с “uuid” равным 06520f6e-5096-4d49-a044-136357737eff 
2. Сформировать тело запроса для добавления игры в список желаний

```
{
    "item_uuid": "06520f6e-5096-4d49-a044-136357737eff"
}
```

1. Отправить POST-запрос на добавление игры выбранного пользователя. С телом запроса из шага 5

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/users/3779ba46-8ca8-433b-8b86-1b4384dc8554/wishlist/add 

1. Проверить список желаний пользователя с помощью GET-запроса

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/users/3779ba46-8ca8-433b-8b86-1b4384dc8554/wishlist

### Ожидаемый результат

Шаг 6. Статус код ответа 200 OK игра добавлена в список желаний

Шаг 7. Статус код ответа 200 OK с сообщением формата

```json
{
  "items": [
    {
      "category_uuids": [
                "78fcb98b-d820-4d79-a049-e2089b7ce87a"
            ],
            "price": 999,
            "title": "The Witcher 3: Wild Hunt",
            "uuid": "06520f6e-5096-4d49-a044-136357737eff"
        }
  ],
  "user_uuid": "3779ba46-8ca8-433b-8b86-1b4384dc8554"
}
```

### Фактический результат

Шаг 6. Сервер возвращает код 422 Unprocessable Entity с сообщением "Wishlist limit is reached: 10”

Шаг 7. Сервер возвращает код 200 с пустым списком желаний пользователя

```json
{
    "items": [],
    "user_uuid": "3779ba46-8ca8-433b-8b86-1b4384dc8554"
}
```

### Окружение

Postman for Windows Version 11.1.14

### Приоритет

P2 - Средний. Ошибка не позволяет добавлять пользователю игру в список желаний, что негативно сказывается на пользовательском опыте

### Серьезность

S2 - Критическая. Ошибка в работе логики сервера, некорректно определяющего лимит списка желаний