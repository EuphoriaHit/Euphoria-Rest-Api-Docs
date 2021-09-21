# Регистрация

#### Первичная регистрация

> **Url**: http://45.76.89.136:90/api/v1/register

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

code : 201
```
{
    "code": 201,
    "message:": "Success",
    "status": "successfully registered"
}
```

Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в 
#####  Пример ошибки с уже занятыми почтой и логином
```
 {
        "code": 409,
        "errors": [
        {
           "message": "email is already exist",
           "code": 409
        }
       ]
       }, 409
```

#####  Пример ошибки с невалидной почтой
```
 {
        "code": 400,
        "errors": [
            {
                "message": "email is not valid",
                "code": 400
            }
       ]
   }, 400
```


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

### Возможные статусы пользователя

```
  successfully registered - Пройдена регистрация (e-mail не подтвержден)
  e-mail confirmed - e-mail подтвержден
```






#### Подтверждение почты

> **Url**: http://45.76.89.136:90/api/v1/email-confirm

> **Method**: POST



### Необходимые параметры

```
    code - required|string
    email - string

```

### Описание параметров

```
code // код, который присылается на почту при регистации
email // e-mail пользователя



```
##### Пример:

```
{
	"code" : "59143",
	"email" : "qqq@qqq.q"
}
```


##### Ответ

code : 200
```
{
    "code": 200,
    "message": "Success!",
    "status": "e-mail confirmed"
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

#####  Пример ошибки с подтвержденной почтой
```
  {
        "code": 400,
        "errors": [
            {
                "message": "his user is already confirmed e-mail!",
                "code": 400
            }
        ]
    }, 400
```

# Отправка кода активации

#### отправка кода активации повторно

> **Url**: http://45.76.89.136:90/api/v1/register/resent-code

> **Method**: POST



### Необходимые параметры

```
    email - required|string    
```

### Описание параметров

```
email // e-mail
```
##### Пример:

```
{
	"email" : "qqq@qqq.q"
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