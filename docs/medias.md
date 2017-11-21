# Медиа (Файлы)

## Добавление медиа

`POST /api/v1/media/add` вернёт информацию о добавленном медиа объекте.

### Запрос:

Имя | Тип | Описание
--- | --- | ---
binary | string | multipart/form-data содержимое

### Ответ:

[Медиа](https://github.com/doktornarabote/telemedicine-partner-api/blob/master/docs/contracts.md#media)

```json
{
  "item": {
    //.. объект медиа
  }
}
```

## Получение информации о медиа

`GET /api/v1/media/get/{id}` вернёт информацию о медиа объекте.

### Запрос

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор медиа объекта

### Ответ

Бинарное содержимое объекта (файла)

## Получение загруженных пациентом документов

`GET /api/v1/media/get-uploaded` вернёт список ID загруженных пациентом документов.

### Запрос

Имя | Тип | Описание
--- | --- | ---
limit | integer | кол-во (записей в ответе)
offset | integer | смещение (сколько записей пропустить)
asc | boolean | сортировать по возрастанию по дате добавления

### Ответ

[Медиа](https://github.com/doktornarabote/telemedicine-partner-api/blob/master/docs/contracts.md#media)

```json
{
  "items": [
    {
      //.. ID медиа-объекта
    }
  ],
  "count": 10,
  "totalCount": 15
}
```
