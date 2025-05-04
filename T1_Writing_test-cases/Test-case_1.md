# Тест-кейс 1. Попарное тестирование параметров recalculate, owner и region

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
        <td  rowspan="3">
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
</table>



