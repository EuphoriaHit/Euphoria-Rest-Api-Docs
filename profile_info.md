#  Информация о пользователе

> **Url**: http://45.76.89.136:90/api/v1/profile/info

> **Method**: GET



### Необходимые параметры

``` 
request Header:
    AccessToken  - required|string
```

### Описание параметров

```
header:
Authorization // заголовок - Bearer Token "токен авторизации"

```
##### Пример:

```
Header:
{
"Authorization" : "Bearer Token eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1ODYzMzkxMzAsIm5iZiI6MTU4NjMzOTEzMCwianRpIjoiZjcxMDBmZmItYWFhMy00ZGM3LThmNDItOThjZDAxYzQ2MjQwIiwiZXhwIjoxNTg2MzQ2MzMwLCJpZGVudGl0eSI6IjkzIiwiZnJlc2giOmZhbHNlLCJ0eXBlIjoiYWNjZXNzIn0.3HW-qbkUYgfmGlv7vre9UMmpP9nU0oxT-uTHEOunD2A"
}
```


##### Ответ

code : 200
```
{
    "avatar": "http://127.0.0.1:5000/static/images/image.png",
    "email": "tishkambekov@mail.ru",
    "email_confirmed": true,
    "google_2FA_activated": false,
    "is_blocked": false,
    "user_id": "24d91e9a-5d57-42be-bd65-e8359e3af03b"
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