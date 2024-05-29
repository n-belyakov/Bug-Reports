# Test-case 3

### **Цель задачи**

Протестировать функциональность, которая позволяет администраторам создавать новых пользователей в системе.

### **Тестовые данн**

### **Базовый URL**

```jsx
https://dev-gs.qa-playground.com/api/v1
```

### **Заголовки**

```jsx
"Authorization": "Bearer eyJhbGciOiJIUzI1NiIsImtpZCI6IldGZlRBQ0hzYUhvQ3VML1MiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhdXRoZW50aWNhdGVkIiwiZXhwIjoxNzE3MTU0ODY1LCJpYXQiOjE3MTY1NTQ4NjUsImlzcyI6Imh0dHBzOi8vbXlrb3RxYm9ja3p2emFjY2N1Ynouc3VwYWJhc2UuY28vYXV0aC92MSIsInN1YiI6IjMzZTM1N2U1LWJhZTEtNDYzMy05ZGY1LWNkNmNkODk0ZjcwNCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwicGhvbmUiOiIiLCJhcHBfbWV0YWRhdGEiOnsicHJvdmlkZXIiOiJnaXRodWIiLCJwcm92aWRlcnMiOlsiZ2l0aHViIl19LCJ1c2VyX21ldGFkYXRhIjp7ImF2YXRhcl91cmwiOiJodHRwczovL2F2YXRhcnMuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3UvMTM4MTUxOTMzP3Y9NCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImZ1bGxfbmFtZSI6Ik5pa2l0YSBCZWx5YWtvdiIsImlzcyI6Imh0dHBzOi8vYXBpLmdpdGh1Yi5jb20iLCJuYW1lIjoiTmlraXRhIEJlbHlha292IiwicGhvbmVfdmVyaWZpZWQiOmZhbHNlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJuLWJlbHlha292IiwicHJvdmlkZXJfaWQiOiIxMzgxNTE5MzMiLCJzdWIiOiIxMzgxNTE5MzMiLCJ1c2VyX25hbWUiOiJuLWJlbHlha292In0sInJvbGUiOiJhdXRoZW50aWNhdGVkIiwiYWFsIjoiYWFsMSIsImFtciI6W3sibWV0aG9kIjoib2F1dGgiLCJ0aW1lc3RhbXAiOjE3MTY1NTQ4NjV9XSwic2Vzc2lvbl9pZCI6ImFkNjFhZmQ4LTkwMTktNDVkZS1iOTk4LTUwMGYzN2NjMDVjMCIsImlzX2Fub255bW91cyI6ZmFsc2V9.aQ26JcXm7Rdo0e4sT1xAJVn2P7NNBfk_K6AKJyTvuS4",
"X-Task-Id": "API-3"
```

### **Скопировать Bearer-токен**

```jsx
eyJhbGciOiJIUzI1NiIsImtpZCI6IldGZlRBQ0hzYUhvQ3VML1MiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhdXRoZW50aWNhdGVkIiwiZXhwIjoxNzE3MTU0ODY1LCJpYXQiOjE3MTY1NTQ4NjUsImlzcyI6Imh0dHBzOi8vbXlrb3RxYm9ja3p2emFjY2N1Ynouc3VwYWJhc2UuY28vYXV0aC92MSIsInN1YiI6IjMzZTM1N2U1LWJhZTEtNDYzMy05ZGY1LWNkNmNkODk0ZjcwNCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwicGhvbmUiOiIiLCJhcHBfbWV0YWRhdGEiOnsicHJvdmlkZXIiOiJnaXRodWIiLCJwcm92aWRlcnMiOlsiZ2l0aHViIl19LCJ1c2VyX21ldGFkYXRhIjp7ImF2YXRhcl91cmwiOiJodHRwczovL2F2YXRhcnMuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3UvMTM4MTUxOTMzP3Y9NCIsImVtYWlsIjoibXlAYmVseWFrb3ZuLnJ1IiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImZ1bGxfbmFtZSI6Ik5pa2l0YSBCZWx5YWtvdiIsImlzcyI6Imh0dHBzOi8vYXBpLmdpdGh1Yi5jb20iLCJuYW1lIjoiTmlraXRhIEJlbHlha292IiwicGhvbmVfdmVyaWZpZWQiOmZhbHNlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJuLWJlbHlha292IiwicHJvdmlkZXJfaWQiOiIxMzgxNTE5MzMiLCJzdWIiOiIxMzgxNTE5MzMiLCJ1c2VyX25hbWUiOiJuLWJlbHlha292In0sInJvbGUiOiJhdXRoZW50aWNhdGVkIiwiYWFsIjoiYWFsMSIsImFtciI6W3sibWV0aG9kIjoib2F1dGgiLCJ0aW1lc3RhbXAiOjE3MTY1NTQ4NjV9XSwic2Vzc2lvbl9pZCI6ImFkNjFhZmQ4LTkwMTktNDVkZS1iOTk4LTUwMGYzN2NjMDVjMCIsImlzX2Fub255bW91cyI6ZmFsc2V9.aQ26JcXm7Rdo0e4sT1xAJVn2P7NNBfk_K6AKJyTvuS4
```

> Вы можете использовать этот токен на протяжении всей тестовой сессии, включая последующие задачи.
> 

### **Документация**

- [**Redoc**](https://redocly.github.io/redoc/?url=https://dev-gs.qa-playground.com/api/v1/swagger.json)
- [**Swagger**](https://petstore.swagger.io/?url=https://dev-gs.qa-playground.com/api/v1/swagger.json)

### **Предусловия**

1. Авторизоваться в системе через **Bearer token** (взять его из заголовков выше).
2. Использовать **Базовый URL**, указанный в тестовых данных, для отправки запросов во время тестирования.
3. Отправить **POST** запрос на эндпоинт **`/setup`** для **настройки/сброса** вашей **тестовой среды**.
    - **Если вы получили код 401**, возможно, ваш токен отсутствует или истек. В этом случае, необходимо скопировать его снова из заголовка выше.
    - Настроенная тестовая среда работает на протяжении всей тестовой сессии, в том числе и для последующие задач.
    - Каждый этап тестирования использует одну и ту же **базу данных**.

### **Шаги для выполнения задачи**

1. Заполните **тело запроса** валидными данными в соответствии с требованиями документации.
    
    ### **Шаблон тела запроса:**
    
    ```json
    {
        "email": "string",
        "password": "string",
        "name": "string",
        "nickname": "string"
    }
    ```
    
2. Отправьте **POST** запрос на эндпоинт **`/users`** с ранее подготовленным **телом запроса**.
3. Проверьте, что возвращается **статус-код ответа** - **200**.
4. Убедитесь, что **поля ответа** соответствуют ожидаемым полям ответа из документации и содержат ваши данные.
    
    ### **Пример ответа:**
    
    ```json
    {
     "email": "john.doe@gmail.com",
     "name": "John Doe",
     "nickname": "johndoe",
     "avatar_url": "",
     "uuid": "00000000-0000-4562-b3fc-2c963f66afa6"
    }
    ```
    
5. Проверьте, что новый пользователь был создан и существует в списке пользователей **`user list`**, отправив **GET** запрос на эндпоинт **`/users`**.
6. Убедитесь, что информация о пользователе успешно возвращается путем отправки **GET** запроса с **`uuid`** пользователя на эндпоинт **`/users/{uuid}`**.

### **Приемочные критерии**

1. Статус-код ответа - **200**.
2. Ответ содержит ваши данные и не теряет значений.
3. Пользователь отображается в **`списке пользователей`**.
4. Добавленный пользователь корректно отображается при получении по его **`uuid`**.