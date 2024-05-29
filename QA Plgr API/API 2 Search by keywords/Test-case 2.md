# Test-case 2

### **Цель задачи**

Протестировать функциональность, которая позволяет пользователю искать игры по ключевым словам или фразе.

### **Тестовые данные**

### **Базовый URL**

```jsx
https://dev-gs.qa-playground.com/api/v1
КопироватьСкопировано!
```

### **Заголовки**

```jsx
"Authorization": "Bearer eyJhbGciOiJIUzI1NiIsImtpZCI6IldGZlRBQ0hzYUhvQ3VML1MiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhdXRoZW50aWNhdGVkIiwiZXhwIjoxNzE3MTU0ODY1LCJpYXQiOjE3MTY1NTQ4NjUsImlzcyI6Imh0dHBzOi8vbXlrb3RxYm9ja3p2emFjY2N1Ynouc3VwYWJhc2UuY28vYXV0aC92MSIsInN1YiI6IjMzZTM1N2U1LWJhZTEtNDYzMy05ZGY1LWNkNmNkODk0ZjcwNCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwicGhvbmUiOiIiLCJhcHBfbWV0YWRhdGEiOnsicHJvdmlkZXIiOiJnaXRodWIiLCJwcm92aWRlcnMiOlsiZ2l0aHViIl19LCJ1c2VyX21ldGFkYXRhIjp7ImF2YXRhcl91cmwiOiJodHRwczovL2F2YXRhcnMuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3UvMTM4MTUxOTMzP3Y9NCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImZ1bGxfbmFtZSI6Ik5pa2l0YSBCZWx5YWtvdiIsImlzcyI6Imh0dHBzOi8vYXBpLmdpdGh1Yi5jb20iLCJuYW1lIjoiTmlraXRhIEJlbHlha292IiwicGhvbmVfdmVyaWZpZWQiOmZhbHNlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJuLWJlbHlha292IiwicHJvdmlkZXJfaWQiOiIxMzgxNTE5MzMiLCJzdWIiOiIxMzgxNTE5MzMiLCJ1c2VyX25hbWUiOiJuLWJlbHlha292In0sInJvbGUiOiJhdXRoZW50aWNhdGVkIiwiYWFsIjoiYWFsMSIsImFtciI6W3sibWV0aG9kIjoib2F1dGgiLCJ0aW1lc3RhbXAiOjE3MTY1NTQ4NjV9XSwic2Vzc2lvbl9pZCI6ImFkNjFhZmQ4LTkwMTktNDVkZS1iOTk4LTUwMGYzN2NjMDVjMCIsImlzX2Fub255bW91cyI6ZmFsc2V9.aQ26JcXm7Rdo0e4sT1xAJVn2P7NNBfk_K6AKJyTvuS4",
"X-Task-Id": "API-2"
```

### **Скопировать Bearer-токен**

```jsx
eyJhbGciOiJIUzI1NiIsImtpZCI6IldGZlRBQ0hzYUhvQ3VML1MiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhdXRoZW50aWNhdGVkIiwiZXhwIjoxNzE3MTU0ODY1LCJpYXQiOjE3MTY1NTQ4NjUsImlzcyI6Imh0dHBzOi8vbXlrb3RxYm9ja3p2emFjY2N1Ynouc3VwYWJhc2UuY28vYXV0aC92MSIsInN1YiI6IjMzZTM1N2U1LWJhZTEtNDYzMy05ZGY1LWNkNmNkODk0ZjcwNCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwicGhvbmUiOiIiLCJhcHBfbWV0YWRhdGEiOnsicHJvdmlkZXIiOiJnaXRodWIiLCJwcm92aWRlcnMiOlsiZ2l0aHViIl19LCJ1c2VyX21ldGFkYXRhIjp7ImF2YXRhcl91cmwiOiJodHRwczovL2F2YXRhcnMuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3UvMTM4MTUxOTMzP3Y9NCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImZ1bGxfbmFtZSI6Ik5pa2l0YSBCZWx5YWtvdiIsImlzcyI6Imh0dHBzOi8vYXBpLmdpdGh1Yi5jb20iLCJuYW1lIjoiTmlraXRhIEJlbHlha292IiwicGhvbmVfdmVyaWZpZWQiOmZhbHNlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJuLWJlbHlha292IiwicHJvdmlkZXJfaWQiOiIxMzgxNTE5MzMiLCJzdWIiOiIxMzgxNTE5MzMiLCJ1c2VyX25hbWUiOiJuLWJlbHlha292In0sInJvbGUiOiJhdXRoZW50aWNhdGVkIiwiYWFsIjoiYWFsMSIsImFtciI6W3sibWV0aG9kIjoib2F1dGgiLCJ0aW1lc3RhbXAiOjE3MTY1NTQ4NjV9XSwic2Vzc2lvbl9pZCI6ImFkNjFhZmQ4LTkwMTktNDVkZS1iOTk4LTUwMGYzN2NjMDVjMCIsImlzX2Fub255bW91cyI6ZmFsc2V9.aQ26JcXm7Rdo0e4sT1xAJVn2P7NNBfk_K6AKJyTvuS4
```

### **Документация**

- [**Redoc**](https://redocly.github.io/redoc/?url=https://dev-gs.qa-playground.com/api/v1/swagger.json)
- [**Swagge**](https://petstore.swagger.io/?url=https://dev-gs.qa-playground.com/api/v1/swagger.json)

### **Предусловия**

1. Авторизоваться в системе через **Bearer token** (взять его из заголовков выше).
2. Использовать **Базовый URL**, указанный в тестовых данных, для отправки запросов во время тестирования.
3. Отправить **POST** запрос на эндпоинт **`/setup`** для **настройки/сброса** вашей **тестовой среды**.
    - **Если вы получили статус-код 401**, возможно, ваш токен отсутствует или истек. В этом случае, необходимо скопировать его снова из заголовка выше.
    - Настроенная тестовая среда работает на протяжении всей тестовой сессии, в том числе и для последующие задач.
    - Каждый этап тестирования использует одну и ту же **базу данных**.

### **Шаги для выполнения задачи**

1. Отправить **GET** запрос на эндпоинт **`/games`** для получения **`списка всех игр`**.
2. Выбрать любую игру и в качестве ключевого слова скопируйте часть её названия.
3. Подготовить **query**параметр для поискового запроса с использованием ранее скопированной части названия игры.
    
    ### **Пример параметра:**
    
    ```json
    {
        "query": "Witcher"
    }
    КопироватьСкопировано!
    ```
    
4. Отправить **GET** запрос на эндпоинт **`/games/search`** с ранее подготовленным **query-параметром**.
5. Проверить, что возвращается **статус-код ответа** - **200**.
6. Проверить, что **поля ответа** соответствуют полям из документации и содержат данные только с запрашиваемым ключевым словом или фразой.
    
    ### **Пример ответа:**
    
    ```json
    {
     "games": [
       {
         "category_uuids": [
           "78fcb98b-d820-4d79-a049-e2089b7ce87a"
         ],
         "price": 999,
         "title": "The Witcher 3: Wild Hunt",
         "uuid": "06520f6e-5096-4d49-a044-136357737eff"
       }
     ],
     "meta": {
       "total": 1
     }
    }
    КопироватьСкопировано!
    ```
    

### **Приемочные критерии**

1. Статус-код ответа - **200**.
2. Функция поиска возвращает результаты, основанные только на предоставленном ключевом слове или фразе.
3. Система корректно обрабатывает пустые или невалидные поисковые запросы.
4. Результаты поиска правильно отформатированы и содержат соответствующую информацию о запрашиваемых играх.