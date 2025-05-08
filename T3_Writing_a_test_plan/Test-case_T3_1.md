# Тест-кейс 1. Попарное тестирование параметров count и start

## Предусловия
1) Используется productId существующего продукта
2) Используется корректный authToken


## Шаги
Выполнить запросы из таблицы "Запросы".

## Запросы
| №  | start | count | Вычисление стоимости   | Запрос                                                           | Ожидаемый результат |
|----|-------|-------|------------------------|------------------------------------------------------------------|---------------------|
| 1  | 0     | 0     | =0                     | /products/{productId}/cost?authToken={authToken}&count=0&start=0 | { "cost": 0}        |
| 2  | 0     | 1     | =30                    | /products/{productId}/cost?authToken={authToken}&count=0&start=1 | { "cost": 30}       |
| 3  | 0     | 5     | =30+25+20+15+10=100    | /products/{productId}/cost?authToken={authToken}&count=0&start=5 | { "cost": 100}      |
| 4  | 0     | 6     | =30+25+20+15+10+30=130 | /products/{productId}/cost?authToken={authToken}&count=0&start=6 | { "cost": 130}      |
| 5  | 1     | 0     | =0                     | /products/{productId}/cost?authToken={authToken}&count=1&start=0 | { "cost": 0}        |
| 6  | 1     | 1     | =25                    | /products/{productId}/cost?authToken={authToken}&count=1&start=1 | { "cost": 25}       |
| 7  | 1     | 5     | =25+20+15+10+30=100    | /products/{productId}/cost?authToken={authToken}&count=1&start=5 | { "cost": 100}      |
| 8  | 1     | 6     | =25+20+15+10+30+25=125 | /products/{productId}/cost?authToken={authToken}&count=1&start=6 | { "cost": 125}      |
| 9  | 5     | 0     | =0                     | /products/{productId}/cost?authToken={authToken}&count=5&start=0 | { "cost": 0}        |
| 10 | 5     | 1     | =30                    | /products/{productId}/cost?authToken={authToken}&count=5&start=1 | { "cost": 30}       |
| 11 | 5     | 5     | =30+25+20+15+10=100    | /products/{productId}/cost?authToken={authToken}&count=5&start=5 | { "cost": 100}      |
| 12 | 5     | 6     | =30+25+20+15+10+30=130 | /products/{productId}/cost?authToken={authToken}&count=5&start=6 | { "cost": 130}      |
| 13 | 6     | 0     | =0                     | /products/{productId}/cost?authToken={authToken}&count=6&start=0 | { "cost": 0}        |
| 14 | 6     | 1     | =25                    | /products/{productId}/cost?authToken={authToken}&count=6&start=1 | { "cost": 25}       |
| 15 | 6     | 5     | =25+20+15+10+30=100    | /products/{productId}/cost?authToken={authToken}&count=6&start=5 | { "cost": 100}      |
| 16 | 6     | 6     | =25+20+15+10+30+25=125 | /products/{productId}/cost?authToken={authToken}&count=6&start=6 | { "cost": 125}      |


## Ожидаемый результат
Ответ в json формате с http-кодом 200 {"cost":} (значение "cost" согласно таблице "Запросы").
