#  Картинки игр

> **Url**: http://45.76.89.136:90/api/v1/baccarat/get-cards

> **Method**: GET


##### Ответ, если у игрока и диллера по 2 карты

code : 200
```
{
    "cards": {
        "dealer": [
            "sJ",
            "d9"
        ],
        "player": [
            "c7",
            "d9"
        ]
    },
    "scores": {
        "dealer": "9",
        "player": "6"
    },
    "winner": "Dealer wins"
}
```

##### Ответ,  если у игрока и диллера по 3 карты 

code : 200
```
{
    "cards": {
        "dealer": [
            "s9",
            "h6",
            "hJ"
        ],
        "player": [
            "cJ",
            "s10",
            "h4"
        ]
    },
    "scores": {
        "dealer": "5",
        "player": "4"
    },
    "winner": "Dealer wins"
}
```

##### Ответ,  если у игрока 2 карты, а у диллера по 3 карты 

code : 200

```
{
    "cards": {
        "dealer": [
            "c7",
            "s8",
            "d9"
        ],
        "player": [
            "s9",
            "h8"
        ]
    },
    "scores": {
        "dealer": "4",
        "player": "7"
    },
    "winner": "Player wins"
}
```

##### Ответ,  если у игрока 3 карты, а у диллера по 2 карты 

code : 200

```
{
    "cards": {
        "dealer": [
            "s10",
            "c4"
        ],
        "player": [
            "s8",
            "s2",
            "h10"
        ]
    },
    "scores": {
        "dealer": "4",
        "player": "0"
    },
    "winner": "Dealer wins"
}
```