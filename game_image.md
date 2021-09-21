#  Картинки игр

> **Url**: http://45.76.89.136:90/api/v1/games/images

> **Method**: GET



### Необходимые параметры

``` 
game-name: optional|string
```

### Описание параметров

```
game-name // название игры: poker, bakkara, sport
```

##### Пример:

```
game-name: poker
```


##### Ответ

code : 200
```
{
    "poker": "http://127.0.0.1:5000/static/images/games/poker.png"
}
```

##### Ответ при не указании параметра game-name

code : 200
```
{
    "bakkara": "http://127.0.0.1:5000/static/images/games/bakkara.png",
    "poker": "http://127.0.0.1:5000/static/images/games/poker.png",
    "sport": "http://127.0.0.1:5000/static/images/games/sport.png"
}
```

Если код ошибки 4** то произошло ошибка валидаций некоторых полей. Ошибочные поля указывается в поле "errors" в 
#####  Пример ошибки с неправильным значением параметра game-name
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