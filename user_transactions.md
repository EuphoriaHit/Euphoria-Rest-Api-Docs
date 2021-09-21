#  История транзакций пользователя

> **Url**: http://45.76.89.136:90/api/v1/wallets/transactions/`<wallet>`

> **Method**: GET



### Необходимые параметры

``` 
    wallet - required|string

request Header:
    AccessToken  - required|string
```

### Описание параметров

```
wallet  // Название кошелька. Узнать названия кошельков можно через запрос. http://45.76.89.136:90/api/v1/wallets
        // Для получения истории всех транзакций значение должно быть 'all'
        // Для получения транзакций кошельков BEP20 Tether и ERC20 Tether вместе, значение должно быть 'Tether'

header:
Authorization // заголовок - Bearer Token "токен авторизации"

```
##### Пример:

```
wallet: Bitcoin

Header:
{
"Authorization" : "Bearer Token eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1ODYzMzkxMzAsIm5iZiI6MTU4NjMzOTEzMCwianRpIjoiZjcxMDBmZmItYWFhMy00ZGM3LThmNDItOThjZDAxYzQ2MjQwIiwiZXhwIjoxNTg2MzQ2MzMwLCJpZGVudGl0eSI6IjkzIiwiZnJlc2giOmZhbHNlLCJ0eXBlIjoiYWNjZXNzIn0.3HW-qbkUYgfmGlv7vre9UMmpP9nU0oxT-uTHEOunD2A"
}
```


##### Ответ

code : 200
```
{
    "data": [
        {
            "address_from": "0xc94ef698724936e1abcd0a284620ca47227edbfd",
            "address_to": "0x28c6db6b5a9fd2f18f0323f8db9b8272f373fa78",
            "commision": 0.00051015,
            "created_at": "Wed, 11 Aug 2021 17:27:19 GMT",
            "tx_hash": "0xc305b336fc6d1c20c2b1b9aacda07a7d9df47cb2536b18ef8a8084a500ff63b6",
            "tx_status": "Success",
            "tx_type": "input",
            "updated_at": null,
            "value": 16.0,
            "wallet_name": "BSC USD Coin",
            "wallet_symbol": "USDC"
        },
        {
            "address_from": "0xc94ef698724936e1abcd0a284620ca47227edbfd",
            "address_to": "0x28c6db6b5a9fd2f18f0323f8db9b8272f373fa78",
            "commision": 0.00051027,
            "created_at": "Wed, 11 Aug 2021 17:27:19 GMT",
            "tx_hash": "0x93775987cb696f8eb067acc39bf3a84cd301b0f82e3e301e8827d1495fedaf6d",
            "tx_status": "Success",
            "tx_type": "input",
            "updated_at": null,
            "value": 14.0,
            "wallet_name": "BSC USDT",
            "wallet_symbol": "BUSD"
        }
    ]
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

#####  Пример ошибки с неправильным названием кошелька
```
{
    "code": 404,
    "errors": [
        {
            "code": 404,
            "message": "wallet not found"
        }
    ]
}
```