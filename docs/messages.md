# Текстовые сообщения

## Получение списка сообщений

`GET /api/v2/message/get-all` вернёт список сообщений в рамках консультации, упорядоченных по убыванию даты создания или с учетом указанных полей (см. lookForward).

### Запрос:

Имя | Тип | Описание
--- | --- | ---
requestId | string | уникальный идентификатор консультации
hasAttachment | boolean | наличие вложений в сообщениях
createdFromUtc | datetime | дата начала поиска сообщений
lookForward | boolean | (по умолчанию false) в каком направлении производить поиск, если указано поле createdFromUtc. Определяет направление отсчёта сообщений при постраничной загрузке сообщений
limit | integer | кол-во (записей в ответе)
offset | integer | смещение (сколько записей пропустить)

### Ответ:

[Объект Сообщение](./contracts.md#message)

```json
{
  "items": [
    {
      //.. объект сообщение
    }
  ],
  "count": 10,
  "totalCount": 15
}
```

## Получение списка непрочитанных сообщений

`GET /api/v1/message/get-all-unread` вернёт список непрочитанных сообщений в рамках консультации, упорядоченных по убыванию даты создания.

### Запрос:

Имя | Тип | Описание
--- | --- | ---
requestId | string | уникальный идентификатор консультации
limit | integer | кол-во (записей в ответе)
offset | integer | смещение (сколько записей пропустить)

### Ответ:

[Объект Сообщение](./contracts.md#message)

```json
{
  "items": [
    {
      //.. объект сообщение
    }
  ],
  "count": 10,
  "totalCount": 15
}
```

## Добавление сообщения

`POST /api/v1/message/add` вернёт информацию о добавленном сообщении.

### Запрос:

Имя | Тип | Описание
--- | --- | ---
requestId | integer | уникальный идентификатор консультации
text | string | текстовое содержимое сообщения
attachmentId | string | уникальный идентификатор медиа объекта

### Ответ:

[Объект Сообщение](./contracts.md#message)

```json
{
  "item": {
    //.. объект сообщение
  }
}
```

## Пометить сообщения как прочитанные

`POST /api/v1/message/mark-as-read` вернёт информацию о дате выполнения запроса.

### Запрос:

Имя | Тип | Описание
--- | --- | ---
messageIds | array | массив идентификаторов сообщений

### Ответ:

```json
{
  "item": {
    "executedAtUtc": "2017-11-21T11:17:59.994Z"
  }
}
```
