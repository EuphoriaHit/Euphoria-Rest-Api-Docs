# ожидание подтверждения транзакции и получение информации о ней

####

> **Url**: http://45.76.89.136:90/api/v1/wallets/transactions

> **Method**: POST



### Необходимые параметры


``` 
    wallet - required|string
    hash - required|string
request Header:
    AccessToken  - required|string
```
### Описание параметров

```
AcessToken // заголовок - Bearer Token "токен авторизации"
wallet // название кошелька
hash // хэш транзакции
```
##### Пример:

```
{
	"wallet": "Ethereum",
    "hash": "0x21a1c2bbae0c4da467fbf5c0bc5e7b172195bd7cf44afdb7ebcdf320078e5561"
}
```


##### Ответ

```
"code": 200,
"data": {
    "commission": 7.23e-05,
    "timeStamp": "Wed, 18 Aug 2021 09:44:14 GMT",
    "transactionHash": "0x21a1c2bbae0c4da467fbf5c0bc5e7b172195bd7cf44afdb7ebcdf320078e556a"
},
"message": "transaction was updated",
"status": "Success"
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

##### Пример ошибки, если поле wallet не указано или имеет неправильное значение
```
{
    "code": 404,
    "errors": [
        {
            "message": "wallet not found",
            "code": 404
        }
    ]
}
```

##### Пример ошибки, если поле hash не указано или имеет неправильное значение
```
{
    "code": 400,
    "errors": [
        {
            "message": "hash field not found or is not valid",
            "code": 400
        }
    ]
}
```


##### Пример ошибки, если пользователь не имеет транзакции с данным хэшом в историии транзакций
```
{
    "code": 404,
    "errors": [
        {
            "message": "transaction not found",
            "code": 404
        }
    ]
}
```

##### Пример ошибки, если в истории транзакций пользователя есть такая транзакция, но в сети блокчейн она не оказалась в течение 120 секунд
```
{
    "code": 404,
    "errors": [
        {
            "code": 404,
            "message": "Transaction HexBytes('0x21a1c2bbae0c4da467fbf5c0bc5e7b172195bd7cf44afdb7ebcdf320078e5561') is not in the chain, after 120 seconds"
        }
    ]
}
```