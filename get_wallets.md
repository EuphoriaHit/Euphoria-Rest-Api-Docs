#  запрос на получение данных из кошельков пользователя

> **Url**: http://45.76.89.136:90/api/v1/wallets

> **Method**: GET



### Необходимые параметры

``` 
request Header:
    AccessToken  - required|string
```

### Описание параметров

```
header:
Authorization // заголовок - Bearer Token "токен авторизации"

```

##### Пример:

```
Header:
{
"Authorization" : "Bearer Token eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1ODYzMzkxMzAsIm5iZiI6MTU4NjMzOTEzMCwianRpIjoiZjcxMDBmZmItYWFhMy00ZGM3LThmNDItOThjZDAxYzQ2MjQwIiwiZXhwIjoxNTg2MzQ2MzMwLCJpZGVudGl0eSI6IjkzIiwiZnJlc2giOmZhbHNlLCJ0eXBlIjoiYWNjZXNzIn0.3HW-qbkUYgfmGlv7vre9UMmpP9nU0oxT-uTHEOunD2A"
}
```


##### Ответ

"code": 200,
"data": [
    {
        "address": "mqSbekrVSqeZc8L4KghKz64WaYVGXeEgom",
        "balance": 0.0001,
        "image_url": "http://127.0.0.1:5000/static/images/bitcoin1.png",
        "in_usd": 45214.194381857225,
        "symbol": "BTC",
        "wallet": "Bitcoin"
    },
    {
        "address": "0x28c6dB6b5a9FD2f18f0323F8dB9b8272f373fA78",
        "balance": 3.1317042421794206,
        "image_url": "http://127.0.0.1:5000/static/images/ethereum1.png",
        "in_usd": 3049.929681540888,
        "symbol": "ETH",
        "wallet": "Ethereum"
    },
    {
        "address": "0x28c6dB6b5a9FD2f18f0323F8dB9b8272f373fA78",
        "balance": 0.220581056,
        "image_url": "http://127.0.0.1:5000/static/images/bnb.png",
        "in_usd": 400.4757599589711,
        "symbol": "BNB",
        "wallet": "Binance Coin"
    },
    {
        "balance": 68.0,
        "image_url": "http://127.0.0.1:5000/static/images/tether1.png",
        "in_usd": 1.00033170280356,
        "symbol": "USDT",
        "wallet": "Tether",
        "wallets": [
            {
                "address": "0x28c6dB6b5a9FD2f18f0323F8dB9b8272f373fA78",
                "balance": 54.0,
                "in_usd": 1.00033170280356,
                "symbol": "USDT",
                "wallet": "ERC20 Tether"
            },
            {
                "address": "0x28c6dB6b5a9FD2f18f0323F8dB9b8272f373fA78",
                "balance": 14.0,
                "in_usd": 1.00026442498262,
                "symbol": "BUSD",
                "wallet": "BEP20 Tether"
            }
        ]
    },
    {
        "address": "0x28c6dB6b5a9FD2f18f0323F8dB9b8272f373fA78",
        "balance": 3.6999999999999997,
        "image_url": "http://127.0.0.1:5000/static/images/usdc.png",
        "in_usd": 1.00026953631474,
        "symbol": "USDC",
        "wallet": "ERC20 USD Coin"
    }
],
"status": "Success!"
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