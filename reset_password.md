#  смена пароля

> **Url**: http://45.76.89.136:90/api/v1/profile/password/update

> **Method**: PUT



### Необходимые параметры

``` 
request Header:
    AccessToken  - required|string
body:
    old_password - required|string
    password_1 - required|string
    password_2 - required|string


```

### Описание параметров

```
header:
Authorization // заголовок - Bearer Token "токен авторизации"


body:
old_password //  старый пароль пользователя
new_password1 // новый пароль, строка, должен содержать как минимум 8 символов
new_password2 // новый пароль, строка, должен содержать как минимум 8 символов



```
##### Пример:

```
Header:
{
"Authorization" : "Bearer Token eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1ODYzMzkxMzAsIm5iZiI6MTU4NjMzOTEzMCwianRpIjoiZjcxMDBmZmItYWFhMy00ZGM3LThmNDItOThjZDAxYzQ2MjQwIiwiZXhwIjoxNTg2MzQ2MzMwLCJpZGVudGl0eSI6IjkzIiwiZnJlc2giOmZhbHNlLCJ0eXBlIjoiYWNjZXNzIn0.3HW-qbkUYgfmGlv7vre9UMmpP9nU0oxT-uTHEOunD2A"
}

{
    "old_password" : "qwerty123",
    "new_password1" : "sudoaptget",
    "new_password2" : "sudoaptget"
}
```


##### Ответ

code : 200
```
{
    "code": 201,
    "message": "password updated",
    "status": "Success!"
}
```

Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в 
#####  Пример ошибки, если пароль меньше 8 знаков
```
{
    "code": 411,
    "errors": [
        {
            "code": 411,
            "message": "Password must be at least 8 characters long"
        }
    ]
}
```


Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в 
#####  Пример ошибки, если пароли не совпадают
```
{
    "code": 409,
    "errors": [
        {
            "code": 409,
            "message": "Password mismatch"
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