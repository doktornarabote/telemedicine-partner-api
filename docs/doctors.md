# Врачи

## Поиск по врачам

`GET /api/v1/doctor/get-all` вернёт список врачей.

### Запрос:

Параметры: 

Имя | Тип | Описание
--- | --- | ---
firstName | string | имя
lastName | string | фамилия
middleName | string | отчество
hasAvatar | boolean | признак наличия фотографии
ageFrom | integer | мин. возраст
ageTo | integer | макс. возраст
regionIds | array | идентификаторы регионов
specialtyIds | array | идентификаторы специальностей
degreeIds | array | идентификаторы учёных степеней
positionIds | array | идентификаторы должностей
consultationTypes | array | идентификаторы видов консультаций
availableAtUtc | datetime | планируемое дата и время консультации
availableFromUtc | datetime | дата и время, начиная с которых доступны консультации врачей
availableToUtc | datetime | дата и время, по которые доступны консультации врачей
limit | integer | кол-во (записей в ответе)
offset | integer | смещение (сколько записей пропустить)

### Ответ:

[Врач](https://github.com/doktornarabote/telemedicine-partner-api/blob/master/docs/contracts.md#Doctor)

```json
{
  "items": [
    {
      //.. объект врач
    }
  ],
  "count": 10,
  "totalCount": 15
}
```

## Получение информации о враче

`GET /api/v1/doctor/get/{id}` вернёт информацию о враче.

### Запрос:

Параметры: 

Имя | Тип | Описание
--- | --- | ---
id | integer | уникальный идентификатор врача

### Ответ:

[Врач](https://github.com/doktornarabote/telemedicine-partner-api/blob/master/docs/contracts.md#Doctor)

```json
{
  //.. объект врач
}
```
