# Обновление токена

#### 
> **Url**: http://45.76.89.136:90/api/v1/refresh/token

> **Method**: POST


### Необходимые параметры

``` 
header:

    Bearer Token - required|string

```
### Описание параметров

```


Bearer Token // Refresh Token -  "токен авторизации"

```
##### Пример:

``` 
Header:
{
"Bearer Token" : " eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1ODYzMzkxMzAsIm5iZiI6MTU4NjMzOTEzMCwianRpIjoiZjcxMDBmZmItYWFhMy00ZGM3LThmNDItOThjZDAxYzQ2MjQwIiwiZXhwIjoxNTg2MzQ2MzMwLCJpZGVudGl0eSI6IjkzIiwiZnJlc2giOmZhbHNlLCJ0eXBlIjoiYWNjZXNzIn0.3HW-qbkUYgfmGlv7vre9UMmpP9nU0oxT-uTHEOunD2A"
}

```


##### Ответ

code : 200
```
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE2MTIwMTE0NTAsIm5iZiI6MTYxMjAxMTQ1MCwianRpIjoiZmNlODZhZDctZDc3Ny00YTM1LWFiM2ItMjVkNTBjZDg4ODViIiwiZXhwIjoxNjEyMDEyMzUwLCJpZGVudGl0eSI6ImFkZWRjNzE5LWMzNjMtNDc5OC1iNTMzLTQ0MGNkOTZkYzgxMyIsImZyZXNoIjpmYWxzZSwidHlwZSI6ImFjY2VzcyJ9.P5K5x81cSDDja72inPwiJz-EIRPmOmEEFETc2rSWE5Q",
}
```

Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в 
#####  Пример ошибки без Authorization header
```
{
  "msg": "Only refresh tokens are allowed"
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


Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в 
#####  Пример ошибки с неправильным токеном
```
{
  "msg": "Bad Authorization header. Expected value 'Bearer <JWT>'",
  "code" : "422"
}

```

Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в 
#####  Пример ошибки без Authorization header
```
{
  "msg": "Missing Authorization Header",
  "code" : "401"
}

```

#####  Пример ошибки, если пользователь заблокирован
```
{
  "code": 403,
  "errors": [
      {
          "message": "your account is blocked",
          "code": 403
      },
  ]
}
```