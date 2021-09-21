#  запрос на сброс пароля

> **Url**: http://45.76.89.136:90/api/v1/send-code

> **Method**: POST



### Необходимые параметры

```
    email - required|string    
```

### Описание параметров

```
body:
email // e-mail
```
##### Пример:

```
{
    "email" : "qqq@qqq.q",
}
```


##### Ответ

code : 200
```
{
    "code": 200,
    "message": "a message has been sent to your mail",
    "status": "Success!"
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




#  проверка отправленного кода на почту

> **Url**: http://45.76.89.136:90/api/v1/check-code

> **Method**: POST



### Необходимые параметры

```
    email - required|string    
    code - required|string
```

### Описание параметров

```
body:
email // e-mail
code // код, который присылается на почту при регистации
```
##### Пример:

```
{
    "email" : "qqq@qqq.q",
    "code": "1918434"
}
```


##### Ответ

code : 200
```
{
    "code": 200,
    "status": "Success!"
}
```

Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в
#####  Пример ошибки с невалидным кодом
```
  {
        "code": 409,
        "errors": [
            {
                "message": "Incorrect code",
                "code": 409
            }
        ]
    }, 409
```





#  сброс пароля

> **Url**: http://45.76.89.136:90/api/v1/password/drop

> **Method**: POST



### Необходимые параметры

```
    email - required|string    
    code - required|string
    password1 - required|string
    password2 - required|string
```

### Описание параметров

```
body:
email // e-mail
code // код, который присылается на почту при регистации
password1 // новый пароль, строка, должен содержать как минимум 8 символов
password2 // новый пароль, строка, должен содержать как минимум 8 символов

```
##### Пример:

```
{
    "email" : "qqq@qqq.q",
    "code": "1918434"
    "password1": "qwerty123",
    "password2": "qwerty123"
}
```


##### Ответ

code : 201
```
{
    "code": 201,
    "message": "password updated",
    "status": "Success!"
}
```

Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в
#####  Пример ошибки если длина пароля составляет меньше 8
```
 {
        "code": 411,
        "errors": [
            {
                "message": "Password must be at least 8 characters long",
                "code": 411
            }
       ]
   }, 411
```

#####  Пример ошибки если пароли не совпадают
```
    {
        "code": 409,
        "errors": [
                {
                    "message": "Password mismatch",
                     "code": 409
                }
            ]
    }, 409
```