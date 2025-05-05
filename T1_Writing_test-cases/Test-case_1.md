# Тест-кейс 1. Попарное тестирование параметров recalculate, owner и region

## Таблица попарного тестирования параметров recalculate, owner и region выглядит следующим образом (пустая ячейка в таблице означает отсутствие параметра в запросе):  

| №  | recalculate | owner        | region       |
|----|-------------|--------------|--------------|
| 1  | true        | Создатель    | Северо-Запад |
| 2  | true        |              |              |
| 3  |             | Создатель    |              |
| 4  | false       |              | Северо-Запад |
| 5  |             | Пользователь | Северо-Запад |
| 6  |             |              | Поволжье     |
| 7  | true        | Пользователь | Сибирь       |
| 8  | true        | null         | Поволжье     |
| 9  |             | null         | Сибирь       |
| 10 | false       | Создатель    | Сибирь       |
| 11 | null        | Создатель    | Поволжье     |
| 12 | null        |              | Сибирь       |
| 13 | null        | null         | Северо-Запад |
| 14 | null        | Пользователь |              |
| 15 | false       | null         |              |
| 16 | false       | Пользователь | Поволжье     |


## Предусловия
1) Используется productId существующего продукта c параметрами recalculate = true, owner = Создатель, region = Северо-Запад
2) Используется корректный authToken


## Шаги
Выполнить запросы из таблицы "Запросы".


## Запросы
<table>
    <tr>
        <td>№</td>
        <td>Запрос</td>
        <td>Ожидаемый результат</td>
    </tr>
    <tr>
        <td>1</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=true&owner=Создатель&region=Северо-Запад
        </td>
        <td  rowspan="3">
            Ответ в json формате с http-кодом 200 {"productStatus": 1} <br>
            Допустимые значения 1- Готов, 0 - Не готов
        </td>
    </tr>
    <tr>
        <td>2</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=true
        </td>
    </tr>
    <tr>
        <td>3</td>
        <td>
            /products/{productId}/status?authToken={authToken}&owner=Создатель
        </td>
    </tr>
    <tr>
        <td>4</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=false&region=Северо-Запад
        </td>
        <td  rowspan="13">
            Ответ в json формате с http-кодом 500 {"errorMessage": }
        </td>
    </tr>
    <tr>
        <td>5</td>
        <td>
            /products/{productId}/status?authToken={authToken}&owner=Пользователь&region=Северо-Запад
        </td>
    </tr>
    <tr>
        <td>6</td>
        <td>
            /products/{productId}/status?authToken={authToken}&region=Поволжье
        </td>
    </tr>
    <tr>
        <td>7</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=true&owner=Пользователь&region=Сибирь
        </td>
    </tr>
    <tr>
        <td>8</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=true&owner=null&region=Поволжье
        </td>
    </tr>
    <tr>
        <td>9</td>
        <td>
            /products/{productId}/status?authToken={authToken}&owner=null&region=Сибирь
        </td>
    </tr>
    <tr>
        <td>10</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=false&owner=Создатель&region=Сибирь
        </td>
    </tr>
    <tr>
        <td>11</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=null&owner=Создатель&region=Поволжье
        </td>
    </tr>
    <tr>
        <td>12</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=null&region=Сибирь
        </td>
    </tr>
    <tr>
        <td>13</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=null&owner=null&region=Северо-Запад
        </td>
    </tr>
    <tr>
        <td>14</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=null&owner=Пользователь
        </td>
    </tr>
    <tr>
        <td>15</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=false&owner=null
        </td>
    </tr>
    <tr>
        <td>16</td>
        <td>
            /products/{productId}/status?authToken={authToken}&recalculate=false&owner=Пользователь&region=Поволжье
        </td>
    </tr>
</table>



