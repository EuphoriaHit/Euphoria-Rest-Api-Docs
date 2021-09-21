# Вывод средств

####

> **Url**: http://45.76.89.136:90/api/v1/wallets/send-currency

> **Method**: POST



### Необходимые параметры


``` 
    wallet - required|string
    amount - required|float
    toAddress - required|string
request Header:
    AccessToken  - required|string
```
### Описание параметров

```
AcessToken // заголовок - Bearer Token "токен авторизации"
wallet // название кошелька
amount // сумма для получения
toAddress // адресс аккаунта куда посылаются деньги
```
##### Пример:

```
{
    "wallet": "Ethereum",
    "amount": 0.001,
    "toAddress": "0xc94eF698724936e1ABcD0a284620ca47227EdBfd"
}
```


##### Ответ

code : 201
```
{
    "status": "Success!",
    "status_code": 201,
    "tx_hash": "2d4ac3db1d5fc722a1b258defc4f4855f731f6279059ccc7b57412801c627add"
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
            "message": "wallet, amount or toAddress field not found",
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

##### Пример ошибки, если был введен неправильный адресс toAddress
{
    "code": 400,
    "errors": [
        {
            "message": "toAddress field type is not valid",
            "code": 400
        }
    ]
}


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