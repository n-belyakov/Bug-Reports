# Bug-report 2

## Сервер возвращает список всех игр на запрос поиска по ключевой фразе

### Описание

GET /games/search возвращает все игры, а не только те, что содержат частичное название игры в query-параметре.

При попытке провести поиск через GET-запрос с query-параметром, в котором содержится частичное название игры, сервер возвращает список всех игр.

### **Предусловия**

1. Авторизоваться в системе через **Bearer token** 

```jsx
"Authorization": "Bearer eyJhbGciOiJIUzI1NiIsImtpZCI6IldGZlRBQ0hzYUhvQ3VML1MiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhdXRoZW50aWNhdGVkIiwiZXhwIjoxNzE3MTU0ODY1LCJpYXQiOjE3MTY1NTQ4NjUsImlzcyI6Imh0dHBzOi8vbXlrb3RxYm9ja3p2emFjY2N1Ynouc3VwYWJhc2UuY28vYXV0aC92MSIsInN1YiI6IjMzZTM1N2U1LWJhZTEtNDYzMy05ZGY1LWNkNmNkODk0ZjcwNCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwicGhvbmUiOiIiLCJhcHBfbWV0YWRhdGEiOnsicHJvdmlkZXIiOiJnaXRodWIiLCJwcm92aWRlcnMiOlsiZ2l0aHViIl19LCJ1c2VyX21ldGFkYXRhIjp7ImF2YXRhcl91cmwiOiJodHRwczovL2F2YXRhcnMuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3UvMTM4MTUxOTMzP3Y9NCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImZ1bGxfbmFtZSI6Ik5pa2l0YSBCZWx5YWtvdiIsImlzcyI6Imh0dHBzOi8vYXBpLmdpdGh1Yi5jb20iLCJuYW1lIjoiTmlraXRhIEJlbHlha292IiwicGhvbmVfdmVyaWZpZWQiOmZhbHNlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJuLWJlbHlha292IiwicHJvdmlkZXJfaWQiOiIxMzgxNTE5MzMiLCJzdWIiOiIxMzgxNTE5MzMiLCJ1c2VyX25hbWUiOiJuLWJlbHlha292In0sInJvbGUiOiJhdXRoZW50aWNhdGVkIiwiYWFsIjoiYWFsMSIsImFtciI6W3sibWV0aG9kIjoib2F1dGgiLCJ0aW1lc3RhbXAiOjE3MTY1NTQ4NjV9XSwic2Vzc2lvbl9pZCI6ImFkNjFhZmQ4LTkwMTktNDVkZS1iOTk4LTUwMGYzN2NjMDVjMCIsImlzX2Fub255bW91cyI6ZmFsc2V9.aQ26JcXm7Rdo0e4sT1xAJVn2P7NNBfk_K6AKJyTvuS4",
"X-Task-Id": "API-2"
```

1. Отправить **POST** запрос на эндпоинт **`/setup`** для сброса вашей тестовой среды

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/setup

### Шаги

1. Отправить GET-запрос для получения списка всех игр

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/games

1. Выбрать часть названия игры “Baldur's”
2. Отправить GET-запрос для поиска игры, содержащей “Baldur's” в названии

[https://dev-gs.qa-playground.com/api/v1](https://dev-gs.qa-playground.com/api/v1)/games/search?query=Baldur's

1. Проверить, что возвращается **статус-код ответа** - **200**

### Ожидаемый результат

Сервер возвращает список игр, содержащих “Baldur's” в названии.

### Фактический результат

Сервер возвращает список всех игр, а не только тех, которые соответствуют поисковому запросу.

Полный ответ сервера прикреплен в приложении.

### Окружение

Postman for Windows Version 11.1.14

### Приоритет

P1 - Высокий, так как функциональность поиска по ключевым словам не работает должным образом, что значительно ухудшает пользовательский опыт

### **Серьезность**

S2 - Критическая, так как ошибка связана с основной функциональностью сервиса, влияющей на поиск и доступ к информации

### Приложение

```jsx
{
"games": [
{
"category_uuids": [
"e86aecef-fe7a-4164-a324-57503df14ab9"
],
"price": 5999,
"title": "Atomic Heart",
"uuid": "1990ecdd-4d3d-4de2-91b9-d45d794c82bc"
},
{
"category_uuids": [
"ac949f6c-80f5-40dd-9723-0cd47706060e"
],
"price": 5999,
"title": "Baldur's Gate 3",
"uuid": "0378c074-92d6-4d8c-b6d3-878c08dbe27f"
},
{
"category_uuids": [
"78fcb98b-d820-4d79-a049-e2089b7ce87a"
],
"price": 5999,
"title": "Elden Ring",
"uuid": "03dbad48-ad81-433d-9901-dd5332f5d9ee"
},
{
"category_uuids": [
"a24db271-1e09-4ddc-b40b-3f2b8875c00b"
],
"price": 2499,
"title": "Forza Horizon 5",
"uuid": "cb620f56-daa4-43e0-b4a0-e80f8e5be279"
},
{
"category_uuids": [
"8126d35b-5336-41ad-981d-f245c3e05665"
],
"price": 2999,
"title": "Red Dead Redemption 2",
"uuid": "aca79a7c-5b66-4ff2-b3b8-57e56fc053a7"
},
{
"category_uuids": [
"78fcb98b-d820-4d79-a049-e2089b7ce87a"
],
"price": 2499,
"title": "The Elder Scrolls V: Skyrim",
"uuid": "09531e2b-c3eb-4338-a002-cc4817a7cc58"
},
{
"category_uuids": [
"8126d35b-5336-41ad-981d-f245c3e05665"
],
"price": 1999,
"title": "The Last of Us",
"uuid": "77a94eec-38e0-4a08-a3d7-2be1007ef686"
},
{
"category_uuids": [
"5af3642a-2d97-40d1-aa82-c7f8758863fd"
],
"price": 1999,
"title": "The Sims 4",
"uuid": "12dc6bb3-cd3f-412a-86fe-3c1dce867481"
},
{
"category_uuids": [
"78fcb98b-d820-4d79-a049-e2089b7ce87a"
],
"price": 999,
"title": "The Witcher 3: Wild Hunt",
"uuid": "06520f6e-5096-4d49-a044-136357737eff"
},
{
"category_uuids": [
"8126d35b-5336-41ad-981d-f245c3e05665"
],
"price": 4999,
"title": "Uncharted 4: A Thief's End",
"uuid": "5449c9d0-3399-44e1-bd63-f6cbb62c38ea"
}
],
"meta": {
"total": 10
}
}
```