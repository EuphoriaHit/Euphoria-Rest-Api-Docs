# Ввод средств

####

> **Url**: http://45.76.89.136:90/api/v1/wallets/get-currency

> **Method**: POST



### Необходимые параметры


``` 
    wallet - required|string
    amount - required|float
request Header:
    AccessToken  - required|string
```
### Описание параметров

```
AcessToken // заголовок - Bearer Token "токен авторизации"
wallet // название кошелька
amount // сумма для получения
```
##### Пример:

```
{
	"wallet": "Ethereum",
    "amount": 0.001
}
```


##### Ответ

code : 201
```
{
    "code": 201,
    "status": "Succses",
    "message": "transaction was created"
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

##### Пример ошибки, если не были указаны некоторые или все поля
```
{
    "code": 404,
    "errors": [
        {
            "message": "wallet or amount field not found",
            "code": 404
        }
    ]
}
```


##### Пример ошибки, если был введен неправильный тип для amount
```
{
    "code": 400,
    "errors": [
        {
            "message": "amount field type is not valid",
            "code": 400
        }
    ]
}
```

##### Пример ошибки, если значение wallet неправильное
```
{
    "code": 404,
    "errors": [
        {
            "message": "wallet not found or not available now",
            "code": 404
        }
    ]
}
```

#####  Пример ошибки, если на биткоин кошельке пользователя не хватает средств для перевода
```
{
    "code": 400,
    "errors": [
        {
            "error": "Unable to find a transaction to spend for address mqSbekrVSqeZc8L4KghKz64WaYVGXeEgom."
        },
        {
            "error": "Not enough funds in 0 inputs to pay for 1 outputs, missing -1000."
        },
        {
            "error": "Not enough funds after fees in 0 inputs to pay for 1 outputs, missing -6000."
        },
        {
            "error": "Error validating generated transaction: Transaction missing input or output."
        }
    ]
}
```