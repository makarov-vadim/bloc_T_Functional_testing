# Тест-кейс 2. Тестирование параметра авторизации и аутентификации authToken

## Предусловия
1) Используется productId существующего продукта
2) Для корректной работы положительного теста используется корректный authToken, принятый как {true_authToken}


## Шаги
Выполнить запросы из таблицы "Запросы".


## Запросы
<table>
    <tr>
        <td><b>№</b></td>
        <td><b>Запрос</b></td>
        <td><b>Примечание</b></td>
        <td><b>Ожидаемый результат</b></td>
    </tr>
    <tr>
        <td>1</td>
        <td>/products/{productId}/status?authToken={true_authToken}</td>
        <td>16 символов (цифры и буквы)</td>
        <td>
            Ответ в json формате с http-кодом 200 {"productStatus": 1} <br>
            Допустимые значения 1- Готов, 0 - Не готов
        </td>
    </tr>
    <tr>
        <td>2</td>
        <td>/products/{productId}/status?authToken=qwerty123456789</td>
        <td>15 символов (цифры и буквы)</td>
        <td  rowspan="6">
            Ответ в json формате с http-кодом 500 {"errorMessage": }
        </td>
    </tr>
    <tr>
        <td>3</td>
        <td>/products/{productId}/status?authToken=0123456789123456</td>
        <td>16 символов (только цифры)</td>
    </tr>
    <tr>
        <td>4</td>
        <td>/products/{productId}/status?authToken=abcdefghIjklmnop</td>
        <td>16 символов (только буквы)</td>
    </tr>
    <tr>
        <td>5</td>
        <td>/products/{productId}/status?authToken=abcdefgh123456789</td>
        <td>17 символов (цифры и буквы)</td>
    </tr>
    <tr>
        <td>6</td>
        <td>/products/{productId}/status?authToken=абвгдеёжзийклмно</td>
        <td>16 символов (кириллица)</td>
    </tr>
    <tr>
        <td>7</td>
        <td>/products/{productId}/status?authToken=,.<>?;':"[]{}\|~</td>
        <td>16 символов (спецсимволы)</td>
    </tr>
</table>
