#  Сохранение аватара пользователя

> **Url**: http://45.76.89.136:90/api/v1/profile/avatar

> **Method**: POST



### Необходимые параметры

``` 
request Header:
    AccessToken  - required|string

request Files:
    file  - required|File
```

### Описание параметров

```
header:
Authorization // заголовок - Bearer Token "токен авторизации"

files:
file // файл формата png, jpg, jpeg

```
##### Пример:

```
Header:
{
"Authorization" : "Bearer Token eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1ODYzMzkxMzAsIm5iZiI6MTU4NjMzOTEzMCwianRpIjoiZjcxMDBmZmItYWFhMy00ZGM3LThmNDItOThjZDAxYzQ2MjQwIiwiZXhwIjoxNTg2MzQ2MzMwLCJpZGVudGl0eSI6IjkzIiwiZnJlc2giOmZhbHNlLCJ0eXBlIjoiYWNjZXNzIn0.3HW-qbkUYgfmGlv7vre9UMmpP9nU0oxT-uTHEOunD2A"
}

File:
{
    file: path/to/file/png
}
```


##### Ответ

code : 201
```
{
    "code": 201,
    "file": "http://127.0.0.1:5000/static/images/uploadsScreenshot_from_2021-08-09_09-55-53.png",
    "status": "success"
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

##### Пример ошибки, если не найден параметр file
```
{
    "code": 400,
    "errors": [
        {
            "code": 400,
            "message": "file not found"
        }
    ]
}
```

##### Пример ошибки, если файл не выбран
```
{
    "code": 400,
    "errors": [
        {
            "code": 400,
            "message": "no selected file"
        }
    ]
}
```

##### Пример ошибки, если отправлен файл неправильного формата
```
{
    "code": 400,
    "errors": [
        {
            "code": 400,
            "message": "file type is not valid"
        }
    ]
}
```


#  Удаление аватара пользователя

> **Url**: http://45.76.89.136:90/api/v1/profile/avatar

> **Method**: DELETE



### Необходимые параметры

``` 
request Header:
    AccessToken  - required|string

body:
    file  - required|string
```

### Описание параметров

```
header:
Authorization // заголовок - Bearer Token "токен авторизации"

files:
file // пустая строка

```
##### Пример:

```
Header:
{
"Authorization" : "Bearer Token eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1ODYzMzkxMzAsIm5iZiI6MTU4NjMzOTEzMCwianRpIjoiZjcxMDBmZmItYWFhMy00ZGM3LThmNDItOThjZDAxYzQ2MjQwIiwiZXhwIjoxNTg2MzQ2MzMwLCJpZGVudGl0eSI6IjkzIiwiZnJlc2giOmZhbHNlLCJ0eXBlIjoiYWNjZXNzIn0.3HW-qbkUYgfmGlv7vre9UMmpP9nU0oxT-uTHEOunD2A"
}

body:
{
    file: ""
}
```


##### Ответ

code : 201
```
{
    "code": 201,
    "message": "File deleted",
    "status": "success"
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

##### Пример ошибки, если не найден параметр file
```
{
    "code": 400,
    "errors": [
        {
            "code": 400,
            "message": "file not found"
        }
    ]
}
```

##### Пример ошибки, если файл не выбран
```
{
    "code": 400,
    "errors": [
        {
            "code": 400,
            "message": "Key file not found"
        }
    ]
}
```


