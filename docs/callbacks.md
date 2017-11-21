# Обратный звонок

## Запуск консультации

`POST /api/v1/callbackrequest/start-callback` вернёт информацию о запущенной консультации.

### Запрос:

Имя | Тип | Описание
--- | --- | ---
doctorId | integer | уникальный идентификатор врача
patientPhone | [phone](https://github.com/doktornarabote/telemedicine-partner-api/blob/master/docs/contracts.md#phone) | телефонный номер пациента.
patientFullName | string | фио пациента
cost | [money](https://github.com/doktornarabote/telemedicine-partner-api/blob/master/docs/contracts.md#money) | стоимость выбранной консультации. Необходимо для сверения последних данных о стоимости консультаций от врача со стоимостью, показанной пациенту.
beginAtUtc | datetime | (optional) время начала консультации. Если параметр не указан, то консультация начнется сразу.

### Ответ:

[Обратный звонок](https://github.com/doktornarabote/telemedicine-partner-api/blob/master/docs/contracts.md#Обратный-звонок)

```json
{
  "item": {
    //.. объект обратный звонок
  }
}
```

## Получение информации о консультации

`GET /api/v1/callbackrequest/get/{id}` вернёт информацию о консультации.

### Запрос

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор консультации вида обратный звонок

### Ответ

[Обратный звонок](https://github.com/doktornarabote/telemedicine-partner-api/blob/master/docs/contracts.md#Обратный-звонок)

```json
{
  "item": {
    //.. объект обратный звонок
  }
}
```

## Поиск по консультациям

`GET /api/v1/callbackrequest/get-all` вернёт список консультаций.

### Запрос

Имя | Тип | Описание
--- | --- | ---
ids | array | уникальные идентификаторы консультации вида обратный звонок
statuses | array | статусы консультации
order | string | сортировать по полю (Created, Updated)
asc | boolean | сортировать по возрастанию
limit | integer | кол-во (записей в ответе)
offset | integer | смещение (сколько записей пропустить)

### Ответ

[Обратный звонок](https://github.com/doktornarabote/telemedicine-partner-api/blob/master/docs/contracts.md#Обратный-звонок)

```json
{
  "items": [
    {
      //.. объект обратный звонок
    }
  ],
  "count": 10,
  "totalCount": 15
}
```

## Прерывание консультации

`POST /api/v1/callbackrequest/terminate-callback` вернёт информацию о результате прерывания.

### Запрос

Имя | Тип | Описание
--- | --- | ---
requestId | string | уникальный идентификатор консультации вида обратный звонок

### Ответ

```json
{
  "success": true
}
```