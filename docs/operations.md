# Операции

## Поиск операций

`GET /api/v1/operation/get-all` вернёт список операций.

### Запрос:

Параметры:

Имя | Тип | Описание
--- | --- | ---
operationTypes | array<[OperationType](https://github.com/doktornarabote/telemedicine-partner-api/blob/master/docs/contracts.md#operationtype)> | фильтр по типам операций
currencies | array<[currency](https://github.com/doktornarabote/telemedicine-partner-api/blob/master/docs/contracts.md#currency)> | фильтр по валютам
limit | integer | кол-во (записей в ответе)
offset | integer | смещение (сколько записей пропустить)

### Ответ:

```json
{
  "items": [
    {
      //.. объект операция
    }
  ],
  "count": 10,
  "totalCount": 15
}
```
