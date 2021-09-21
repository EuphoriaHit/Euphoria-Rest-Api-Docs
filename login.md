# Авторизация

#### 
> **Url**: http://45.76.89.136:90/api/v1/sign-in

> **Method**: POST



### Необходимые параметры

```
    email - required|string
    password - required|string
    
```

### Описание параметров

```

email // e-mail
password // пароль, строка, должен содержать как минимум 8 символов


```
##### Пример:

```
{
	"email" : "qqq@qqq.q",
	"password" : "qwerty123",
}
```


##### Ответ

code : 200
```
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJmcmVzaCI6ZmFsc2UsImlhdCI6MTYxODMxMjI2MSwianRpIjoiNGQ0MDVjMmYtNGVmMS00OGM1LTg1ZGEtZmNmYjhjOTY1YzA2IiwibmJmIjoxNjE4MzEyMjYxLCJ0eXBlIjoiYWNjZXNzIiwic3ViIjoyMiwiZXhwIjoxNjE4MzEzMTYxfQ.qbjIlcBa3tXMawQGtnbL3pkKYJbQu2wbutSSoZn7nEU",
    "code": 200,
    "message": "Success!",
    "refresh_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJmcmVzaCI6ZmFsc2UsImlhdCI6MTYxODMxMjI2MSwianRpIjoiOWQwOTVhNWUtNDdmYi00MmZjLTkzYTItNDQwOGRhYWI2ZGFkIiwibmJmIjoxNjE4MzEyMjYxLCJ0eXBlIjoicmVmcmVzaCIsInN1YiI6MjIsImV4cCI6MTYyMDkwNDI2MX0.Bkqo-cdDUs9y6jD-XXtgPD-OZdXiIFD15-SHA4-Mb5s"
}
```

Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в 
#####  Пример ошибки, если такого пользователя в базе нет
```
{
  "code": 404,
  "errors": [
      {
          "message": "user not found!",
          "code": 404
      },
  ]
}
```

#####  Пример ошибки, с неправильным паролем
```
{
  "code": 409,
  "errors": [
      {
          "message": "Incorrect password",
          "code": 409
      },
  ]
}
```


#####  Пример ошибки, с неподтвержденной почтой
```
{
  "code": 403,
  "errors": [
      {
          "message": "email is not confirmed",
          "code": 403
      },
  ]
}
```