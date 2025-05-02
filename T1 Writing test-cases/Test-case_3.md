# Тест-кейс 3. Тестирование параметра productId

## Предусловия
1) Используется корректный authToken
2) productId существующего продукта принят как {true_productId}
3) productId несуществующего продукта принят как {false_productId}


## Шаги
Выполнить запросы (таблица "Запросы"), используя параметры из предусловия.

/products/{productId}/status?authToken={authToken}

## Запросы
<table>
    <tr>
        <td>№</td>
        <td>Запрос</td>
        <td>Ожидаемый результат</td>
    </tr>
    <tr>
        <td>1</td>
        <td>/products/{true_productId}/status?authToken={authToken}</td>
        <td>
            Ответ в json формате с http-кодом 200 {"productStatus": 1} <br>
            Допустимые значения 1- Готов, 0 - Не готов
        </td>
    </tr>
    <tr>
        <td>2</td>
        <td>/products/{false_productId}/status?authToken={authToken}</td>
        <td>
            Ответ с http-кодом 404
        </td>
</table>
