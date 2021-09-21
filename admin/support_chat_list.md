# Список сообщений в слубжу поддержки

####

> **Url**: http://45.76.89.136:90/admin/support-chat

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
"URL/admin/support-chat?page=1&per_page=2"
```

##### Ответ

code : 200
```
{
    "currentPage": 1,
    "support_chat_list": [
        {
            "created_at": "2021-08-25T12:57:36.824401",
            "message": "че там че там",
            "recited": false,
            "user_email": "noorah667@mail.ru"
        },
        {
            "created_at": "2021-08-25T12:57:36.824401",
            "message": "че там че там",
            "recited": false,
            "user_email": "noorah667@mail.ru"
        }
    ],
    "totalItems": 3,
    "totalPages": 2
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

# Удаление сообщения в службе поддержки

####

> **Url**: http://45.76.89.136:90/admin/support-chat

> **Method**: DELETE



### Необходимые параметры


``` 
    chat_id - required|int
request Header:
    AccessToken  - required|string
```
### Описание параметров

```
AcessToken // заголовок - Bearer Token "токен авторизации"
chat_id // id сообщение в службу поддержки
```

##### Пример:

```
{
    "chat_id": 5
}
```

##### Ответ

code : 202
```
{
    "status": "Success!",
    "code": 202,
    "message": "Message deleted successfully"
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

# Поменять статус сообщения в службе поддержки

####

> **Url**: http://45.76.89.136:90/admin/support-chat

> **Method**: PUT



### Необходимые параметры


``` 
    chat_id - required|int
request Header:
    AccessToken  - required|string
```
### Описание параметров

```
AcessToken // заголовок - Bearer Token "токен авторизации"
chat_id // id сообщение в службу поддержки
```

##### Пример:

```
{
    "chat_id": 5
}
```

##### Ответ

code : 202
```
{
    "status": "Success!",
    "code": 202,
    "message": "Message updated successfully",
    "recited": true
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

# Чат с одним пользователем

####

> **Url**: http://45.76.89.136:90/admin/support-chat/<user_email>

> **Method**: GET



### Необходимые параметры


``` 
    user_email - required|string
request Header:
    AccessToken  - required|string
```
### Описание параметров

```
AcessToken // заголовок - Bearer Token "токен авторизации"
user_email // email пользователя
```

##### Пример:

```
"URL/admin/support-chat/noorah667@mail.ru"
```

##### Ответ

code : 200
```
{
    "support_chat_list": [
        {
            "admin_message": "",
            "created_at": "2021-08-26T16:41:10.394290",
            "id": 8,
            "message": "че там че там",
            "recited": false,
            "user_email": "noorah667@mail.ru"
        },
        {
            "admin_message": "",
            "created_at": "2021-08-26T16:41:10.394290",
            "id": 9,
            "message": "че там че там",
            "recited": false,
            "user_email": "noorah667@mail.ru"
        },
        {
            "admin_message": "",
            "created_at": "2021-08-26T16:41:10.394290",
            "id": 10,
            "message": "че там че там",
            "recited": false,
            "user_email": "noorah667@mail.ru"
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

# Отправка сообщения в службе поддержки

####

> **Url**: http://45.76.89.136:90/admin/support-chat

> **Method**: POST



### Необходимые параметры


``` 
    email - required|string
    message - required|string
request Header:
    AccessToken  - required|string
```
### Описание параметров

```
AcessToken // заголовок - Bearer Token "токен авторизации"
email // email пользователя
message // сообщение в службу поддержки
```

##### Пример:

```
{
    "email": "email@email.com", 
    "nickname": "Nick"
}
```

##### Ответ

code : 201
```
{
    "code": 201,
    "status": "Success!",
    "message": "Message sent"
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

