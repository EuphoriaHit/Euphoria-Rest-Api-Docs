# Гугл аутентификация

#### Получение qr-кода и ключа 

> **Url**: http://45.76.89.136:90/api/v1/authenticator

> **Method**: GET



### Необходимые параметры


``` 
request Header:
    AccessToken  - required|string

```
### Описание параметров

```
AcessToken // заголовок - Bearer Token "токен авторизации"
```
##### Пример:

```
 http://45.76.89.136:90/api/v1/authenticator

```


##### Ответ

code : 200
```
{
    "QR_link": "otpauth://totp/Euphoria%20test:cool_boy_16%40mail.ru?secret=EPHLO7RHDOHBV5WDOYI6FIS3MIRTN5JW&issuer=Euphoria%20test",
    "code": 200,
    "key": "EPHLO7RHDOHBV5WDOYI6FIS3MIRTN5JW",
    "status": "Success!"
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






#### Подтверждение гугл аутентификации

> **Url**: http://45.76.89.136:90/api/v1/authenticator/complete

> **Method**: POST



### Необходимые параметры

```
header:
Authorization // заголовок - Bearer Token "токен авторизации"


body:
code //  код, полученный в приложении Google Authenticator

```
##### Пример:

```
Header:
{
"Authorization" : "Bearer Token eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1ODYzMzkxMzAsIm5iZiI6MTU4NjMzOTEzMCwianRpIjoiZjcxMDBmZmItYWFhMy00ZGM3LThmNDItOThjZDAxYzQ2MjQwIiwiZXhwIjoxNTg2MzQ2MzMwLCJpZGVudGl0eSI6IjkzIiwiZnJlc2giOmZhbHNlLCJ0eXBlIjoiYWNjZXNzIn0.3HW-qbkUYgfmGlv7vre9UMmpP9nU0oxT-uTHEOunD2A"
}

{
    "code": "397091"
}
```

##### Ответ

code : 201
```
{
    "code": 201,
    "message": "Google Authenticator is active",
    "status": "Success"
}
```
Если у пользователя включен гугл аутентификатор, то ответ будет таким:
```
{
    "code": 201,
    "message": "Google Authenticator is disabled",
    "status": "Success"
}
```

Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в 
#####  Пример ошибки с невалидным кодом
```
  {
        "code": 400,
        "errors": [
            {
                "message": "wrong code",
                "code": 400
            }
        ]
    }, 400
```
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