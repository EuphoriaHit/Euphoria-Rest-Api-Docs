# Список всех пользователей

####

> **Url**: http://45.76.89.136:90/admin/users-list

> **Method**: GET



### Необходимые параметры


``` 
    page - required|int
    per_page - required|int
request Header:
    AccessToken  - required|string
```
### Описание параметров

```
AcessToken // заголовок - Bearer Token "токен авторизации"
page // нумерация страница, начинается с 1
per_page // количество записей на одной странице
```

##### Пример:

```
"URL/admin/users-list?page=2&per_page=2"
```

##### Ответ

code : 200
```
{
    "currentPage": 2,
    "totalItems": 6,
    "totalPages": 3,
    "users": [
        {
            "created_at": "2021-04-23T12:40:47.559330",
            "email": "cool_boy_16234@mail.ru",
            "is_blocked": false
        },
        {
            "created_at": "2021-04-26T12:22:19.019886",
            "email": "cool_boy_16244@mail.ru",
            "is_blocked": false
        }
    ]
}
```

Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в 
#####  Пример ошибки с истечением срока действия токена
```
{
  "code": 401,
  "errors": [
      {
          "msg": "Token has expired",
          "code": 401
      }
  ]
}
```

