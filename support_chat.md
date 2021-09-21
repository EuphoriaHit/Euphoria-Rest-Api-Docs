#### Отправить сообщение в службу поддержки

> **Url**: http://45.76.89.136:90/api/v1/profile/send-message

> **Method**: POST



### Необходимые параметры

``` 
request Header:
    AccessToken  - required|string
    
body:
    message - required|string
    
```    

###  Описание параметров

```
header:
Authorization // заголовок - Bearer Token "токен авторизации"


body:
message //  cообщение в службу поддержки, без ограничений на кол-во символов

```
##### Пример:

```
Header:
{
"Authorization" : "Bearer Token eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1ODYzMzkxMzAsIm5iZiI6MTU4NjMzOTEzMCwianRpIjoiZjcxMDBmZmItYWFhMy00ZGM3LThmNDItOThjZDAxYzQ2MjQwIiwiZXhwIjoxNTg2MzQ2MzMwLCJpZGVudGl0eSI6IjkzIiwiZnJlc2giOmZhbHNlLCJ0eXBlIjoiYWNjZXNzIn0.3HW-qbkUYgfmGlv7vre9UMmpP9nU0oxT-uTHEOunD2A"
}

{
    "message": "че там"
}
```

##### Ответ

code : 201
```
{
    "code": 201,
    "message": "Message sent",
    "status": "Success!"
}
```


Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в 
#####  Пример ошибки с неправильным ключом в объекте запроса
```
  {
    "code": 400,
    "errors": [
        {
            "code": 400,
            "message": "key error 'message'"
        }
    ]
}
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