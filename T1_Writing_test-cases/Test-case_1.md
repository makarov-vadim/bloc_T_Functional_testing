# Тест-кейс 1. Попарное тестирование параметров recalculate, owner и region

## Предусловия
1) Необходимо наполнить базу данных продуктами с параметрами из таблицы "Запросы"
2) Используется корректный authToken


## Шаги
Выполнить запросы из таблицы "Запросы".


## Запросы

| №  | recalculate | owner        | region       | Запрос                                                                                                  |
|----|-------------|--------------|--------------|---------------------------------------------------------------------------------------------------------|
| 1  | true        | Создатель    | Северо-Запад | /products/{productId}/status?authToken={authToken}&recalculate=true&owner=Создатель&region=Северо-Запад |
| 2  | true        | Пользователь | Сибирь       | /products/{productId}/status?authToken={authToken}&recalculate=true&owner=Пользователь&region=Сибирь    |
| 3  | true        | null         | Поволжье     | /products/{productId}/status?authToken={authToken}&recalculate=true&owner=null&region=Поволжье          |
| 4  | true        |              |              | /products/{productId}/status?authToken={authToken}&recalculate=true                                     |
| 5  | false       | Пользователь | Поволжье     | /products/{productId}/status?authToken={authToken}&recalculate=false&owner=Пользователь&region=Поволжье |
| 6  | false       | null         |              | /products/{productId}/status?authToken={authToken}&recalculate=false&owner=null                         |
| 7  | false       |              | Северо-Запад | /products/{productId}/status?authToken={authToken}&recalculate=false&region=Северо-Запад                |
| 8  | false       | Создатель    | Сибирь       | /products/{productId}/status?authToken={authToken}&recalculate=false&owner=Создатель&region=Сибирь      |
| 9  | null        | null         | Северо-Запад | /products/{productId}/status?authToken={authToken}&recalculate=null&owner=null&region=Северо-Запад      |
| 10 | null        |              | Сибирь       | /products/{productId}/status?authToken={authToken}&recalculate=null&region=Сибирь                       |
| 11 | null        | Создатель    | Поволжье     | /products/{productId}/status?authToken={authToken}&recalculate=null&owner=Создатель&region=Поволжье     |
| 12 | null        | Пользователь |              | /products/{productId}/status?authToken={authToken}&recalculate=null&owner=Пользователь                  |
| 13 |             |              | Поволжье     | /products/{productId}/status?authToken={authToken}&region=Поволжье                                      |
| 14 |             | Создатель    |              | /products/{productId}/status?authToken={authToken}&owner=Создатель                                      |
| 15 |             | Пользователь | Северо-Запад | /products/{productId}/status?authToken={authToken}&owner=Пользователь&region=Северо-Запад               |
| 16 |             | null         | Сибирь       | /products/{productId}/status?authToken={authToken}&owner=null&region=Сибирь                             |

## Ожидаемый результат
Ответ в json формате с http-кодом 200 {"productStatus": 1}. Допустимые значения 1- Готов, 0 - Не готов
