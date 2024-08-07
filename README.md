# ASFObzor
Плагин `ASFObzor` для ASF, под [сайт](https://obzor.biz/).

Версия плагина 0.1.1.0 (бета) Для получения обращайтесь - [@the_honkler](https://t.me/the_honkler).

Версия ArchiSteamFarm [![Версия ArchiSteamFarm](https://img.shields.io/github/v/release/JustArchiNET/ArchiSteamFarm.svg?label=Stable&logo=github&cacheSeconds=600)](https://github.com/JustArchiNET/ArchiSteamFarm/releases/latest)

## КОМАНДЫ

| Команда                    | Сокращение | Описание                                                                                                                                                                    |
| -------------------------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `OSITE`                    | `OS`       | Проверяет сайт на наличие новых заданий и текущих (автоматические каждые 10 мин)                                                                                            |
| `OGAME`                    | `OG`       | Запускает проверку активных заданий (автоматически по необходимости)                                                                                                        |
| `OADD Task Text`           | `OD`       | Добавляет отзыв или публикует, если время вышло, где `Task` - номер заказа, `Text` - текст отзыва. Будет проверено кол-во букв и показана основная информация о отзыве      |
| `OREVI [Bots]`             | `OR`       | Запускает публикацию 4 рандомных отзывов для указанных ботов/бота (автоматически, если включена опция `Review`)                                                             |


## Конфигурация плагина

> В настройках необходимо указать `Cookie` для авторизации, остальные настройки по желанию.

ASF.json

```json
{
  //ASF Configuration
  "CurrentCulture": "...",
  "IPCPassword": "...",

  //ASFObzor Configuration
  "ASFObzor": {
    "Cookie": "user=00000000000000000000000000",
    "BotNotUse": [],
    "TimeChek": 10,
    "Replay": false,
    "LangDefault": "russian",
    "Log": true,
    "AddTask": true,
    "BotUse": [765111111111111110,76550000000000000],
    "AddAcc": 0,
    "MinPriceGame": 0,
    "MaxPriceGame": 0,
    "MinPriceOtziv": 0,
    "MinTime": 0,
    "Bonus": 0,
    "Otziv": false,
    "GameFree": false,
    "AutoPay": true,
    "BotNotPay": [],
    "Review": false,
    "ReviewFree": false,
    "ReviewList": ["Супер","Найс"]
  }
}
```

### Основные
| Конфигурация      | Тип      | По умолчанию | Описание                                                                                                                                                                                         |
| ----------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Cookie`          | `string` |              |  Куки с сайта, единственный обязательный параметр                                                                                                                                                |
| `BotNotUse`       | `list`   | `[]`         |  Список id аккунтов, которые не будут использоваться плагином                                                                                                                                    |
| `TimeChek`        | `int`    | `10`         |  Время (в минутах) для проверки сайта на новые задания. Минимум 5 минут                                                                                                                          |
| `LangDefault`     | `string` | `russian`    |  Язык отзыва по умолчанию. (если в задании указан любой, так же, он будет использоваться в `Review`)                                                                                             |
| `Log`             | `bool`   | `false`      |  Показывает более подробные логи                                                                                                                                                                 |

### Заявки
| Конфигурация      | Тип      | По умолчанию | Описание                                                                                                                                                                                         |
| ----------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `AddTask`         | `bool`   | `true`       |  Автоматически вступать в новые заявки. Если в заявке уже есть аккаунт, она будет пропущена                                                                                                      |
| `BotUse`          | `list`   | `[]`         |  Плагин подгружает аккаунты с сайта и использует их в той же последовательности для подачи заявок. Если вы хотите изменить последовательность, то укажите id аккаунтов в этом списке             |
| `AddAcc`          | `int`    | `0`          |  Кол-во аккаунтов, которые будут подавать заявки. Если указать 0 - все аккаунты будут вступать в новые заявки. Если указать 1 - то только один, доспуный для этой заявки, аккаунт вступит в неё. |
| `MinPriceGame`    | `int`    | `0`          |  Минимальная цена игры для подачи заявки. Если стоимость меньше данного значения, то задание будет пропущено. (кроме 0)                                                                          |
| `MaxPriceGame`    | `int`    | `0`          |  Максимальная цена игры для подачи заявки. Если стоимость больше данного значения, то задание будет пропущено. (кроме 0)                                                                         |
| `MinPriceOtziv`   | `int`    | `0`          |  Минимальная стоимость отзыва для подачи заявки. Если указать 50, то плагин будет подавать заявки в задания, где стоимость отзыва выше 50 рублей. (кроме 0)                                      |
| `MinTime`         | `int`    | `0`          |  Минимальное время для выполнения заявки. Если указать 24, то все заказы с меньшим или таким же временем будут пропускаться. (кроме 0)                                                           |
| `Bonus`           | `int`    | `0`          |  Отказываемся от получение бонуса за отзыв. 0 - получать деньги, 1 - отказаться от получения.                                                                                                    |
| `Otziv`           | `bool`   | `false`      |  Вступать только в задания с готовым отзывом от заказчика. (если вы пишите хорошие отзывы, заказчик может не указать для вас отзыв)                                                              |
| `GameFree`        | `bool`   | `false`      |  Вступать только в задания с бесплатной игрой.                                                                                                                                                   |

### Покупка
| Конфигурация      | Тип      | По умолчанию | Описание                                                                                                                                                                                         |
| ----------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `AutoPay`         | `bool`   | `true`       |  Автоматически покупать игры за баланс стима                                                                                                                                                     |
| `BotNotPay`       | `list`   | `[]`         |  Список id аккунтов, которые не будут покупать игры сами                                                                                                                                         |

### Отзыв
| Конфигурация      | Тип      | По умолчанию | Описание                                                                                                                                                                                         |
| ----------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Review`          | `bool`   | `false`      |  После публикации платного отзыва ищет 4 другие игры(платные) на аккаунте, запускает их на 10 минут и пишет рандомный отзыв к ним по очереди                                                     |
| `ReviewFree`      | `bool`   | `false`      |  Для публикации отзывов берутся не только платные игры, но и бесплатные тоже. Добавить кучу бесплатных игр можно [тут](https://steamdb.info/freepackages/)                                       |
| `ReviewList`      | `list`   | `["Супер","Найс"]` |  Список отзывов. Для каждой игры, рандомно берется один из.                                                                                                                                |


## Где взять Cookie?
В браузере нажимаем F12, переходим во вкладку, как на скрине и копируем значение.
![Куки](https://github.com/uraabk/ASFObzor/assets/10533071/9e7f9ddd-17dc-47ee-a926-a1ee19dfed3a)






