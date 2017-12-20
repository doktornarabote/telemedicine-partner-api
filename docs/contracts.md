# Контракты

## Currency

Возможные значения id: `RUB`, `USD`, `EUR`, `Bonus`.

Имя | Тип | Описание
--- | --- | ---
id | string | идентификатор внутри системы
name | string | название для отображения пользователю

```json
{
    "id": "RUB",
    "name": "руб."
}
```

## Money

Имя | Тип | Описание
--- | --- | ---
amount | float | количество денег
currency | [Currency](./contracts.md#currency) | валюта

```json
{
    "amount": 350.58,
    "currency": {
        "id": "RUB",
        "name": "руб."
    }
}
```

## Phone

Имя | Тип | Описание
--- | --- | ---
code | string | код страны
number | string | номер телефона

```json
{
    "code": "1",
    "number": "1111111111"
}
```

## Doctor

Имя | Тип | Описание
--- | --- | ---
id | integer | идентификатор
lastName | string | фамилия
firstName | string | имя
middleName | string | отчество
avatarUrl | string | url фотографии
birthDate | string | дата рождения
region | object | регион (справочник регионов)
degree | object | учёная степень (справочник учёных степеней)
position | object | должность (справочник должностей)
specialties | array | специальности (справочник медицинских специальностей)
consultationTypes | array<[ConsultationType](./contracts.md#consultation-type)> | доступные виды консультаций (объект вид консультации)
summary | [DoctorStatistics](./contracts.md#doctor-statistics) | статистическая информация (объект статистика врача)

```json
{
  "id": 113824,
  "lastName": "Серикова",
  "firstName": "Светлана",
  "middleName": "Николаевна",
  "avatarUrl": "https://testimg1.doktornarabote.ru/avatars/636174313217149988/123027248161174173111217198116156100001031056199/2",
  "birthDate": "1958-07-13T00:00:00",
  "region": {
    "id": 3001,
    "name": "Россия, Москва"
  },
  "degree": {
    "id": 2,
    "name": "Доктор медицинских наук"
  },
  "position": {
    "id": 16,
    "name": "Другая (введите вручную)"
  },
  "specialties": [
    {
      "id": 60,
      "name": "Терапия"
    },
    {
      "id": 21,
      "name": "Кардиология"
    }
  ],
  "consultationTypes": [
    {
      //..
    }
  ],
  "summary": {
    //..
  }
}
```

## Consultation Type

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
type | object | тип консультации
cost | [Money](./contracts.md#money) | стоимость (объект денежные средства)
timeSchedules | array<[TimeSchedule](./contracts.md#timeschedule)> | график доступности
isAvailable | boolean | признак доступности консультации
isDisabled | boolean | признак запрета на проведение консультации

```json
{
    "id": "03e56f3d-1d43-4824-b9dd-cb29c0036973",
    "type": {
        "id": "Callback",
        "name": "Обратный звонок"
    },
    "cost": {
        //..
    },
    "timeSchedules": [
        {
            //..
        }
    ],
    "isAvailable": true,
    "isDisabled": false
}
```

## Consultation Description

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
type | object | тип консультации
startedAtUtc | datetime | дата начала консультации
doctorName | string | имя доктора

```json
{
    "id": "03e56f3d-1d43-4824-b9dd-cb29c0036973",
    "type": {
        "id": "Callback",
        "name": "Обратный звонок"
    },
    "startedAtUtc": "2017-05-04T00:00:00",
    "doctorName": "Петрович"
}
```

## TimeSchedule

Имя | Тип | Описание
--- | --- | ---
beginAtUtc | datetime | дата начала
endAtUtc | datetime | дата окончания

```json
{
    "beginAtUtc": "2017-05-04T00:00:00",
    "endAtUtc": "2018-05-04T00:00:00"
}
```

## Doctor Statistics

Имя | Тип | Описание
--- | --- | ---
proRating | number | рейтинг
consultationCount | integer | кол-во проведённых консультаций
feedbackCount | integer | кол-во отзывов

```json
{
    "proRating": 5,
    "consultationCount": 56,
    "feedbackCount": 1
}
```

## Consultation Request

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
type | object | тип консультации
status | object | статус
createdAtUtc | datetime | дата создания
medicalReport | [MedicalReport](./contracts.md#medical-report) | заключение врача
feedbacks | array<[Feedback](./contracts.md#feedback)> | список отзывов
statuses | array<[StatusHistory](./contracts.md#status-history)> | история статусов консультации
doctor | [Doctor](./contracts.md#doctor) | врач, с которым проводится консультация
operations | array<[Operation](./contracts.md#operation)> | список проведённых операций
timeline | array<[TimelineEvent](./contracts.md#timeline-event)> | список возникавших событий

```json
{
    "id": "92606f49-9185-407e-b844-7734f0ffb170",
    "type": {
        "id": "Callback",
        "name": "Обратный звонок"
    },
    "status": {
        "id": "Processed",
        "name": "Завершено"
    },
    "createdAtUtc": "2016-12-12T14:10:12",
    "medicalReport": {
        //..
    },
    "feedbacks": [
        //..
    ],
    "statuses": [
        //..
    ],
    "doctor": {
        //..
    },
    "operations": [
        //..
    ],
    "timeline": [
        //..
    ]
}
```

## Callback

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
status | object | статус
createdAtUtc | datetime | дата создания
medicalReport | [MedicalReport](./contracts.md#medical-report) | заключение врача
feedbacks | array<[Feedback](./contracts.md#feedback)> | список отзывов
statuses | array<[StatusHistory](./contracts.md#status-history)> | история статусов консультации
doctor | [Doctor](./contracts.md#doctor) | врач, с которым проводится консультация
operations | array<[Operation](./contracts.md#operation)> | список проведённых операций
timeline | array<[TimelineEvent](./contracts.md#timeline-event)> | список возникавших событий
patientPhone | [Phone](./contracts.md#phone) | телефон, на который поступит звонок для консультации
patientFullName | string | фио пациента
costPerMinute | [Money](./contracts.md#money) | стоимость
calls | array<[Call](./contracts.md#call)> | список осуществлённых звонков

```json
{
    "id": "92606f49-9185-407e-b844-7734f0ffb170",
    "status": {
        "id": "Processed",
        "name": "Завершено"
    },
    "createdAtUtc": "2016-12-12T14:10:12",
    "medicalReport": {
        //..
    },
    "feedbacks": [
        //..
    ],
    "statuses": [
        //..
    ],
    "doctor": {
        //..
    },
    "operations": [
        //..
    ],
    "timeline": [
        //..
    ],
    "patientPhone": {
        //..
    },
    "patientFullName": "Иванов Пётр Сергеевич",
    "costPerMinuite": {
        //..
    },
    "calls": [
        //..
    ]
}
```

## Writing

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
status | object | статус
createdAtUtc | datetime | дата создания
medicalReport | [MedicalReport](./contracts.md#medical-report) | заключение врача
feedbacks | array<[Feedback](./contracts.md#feedback)> | список отзывов
statuses | array<[StatusHistory](./contracts.md#status-history)> | история статусов консультации
doctor | [Doctor](./contracts.md#doctor) | врач, с которым проводится консультация
operations | array<[Operation](./contracts.md#operation)> | список проведённых операций
timeline | array<[TimelineEvent](./contracts.md#timeline-event)> | список возникавших событий
costPerRequest | [Money](./contracts.md#money) | стоимость за консультацию
correspondence | [Correspondence](./contracts.md#correspondence) | информация о сообщениях

```json
{
  "id": "273d9b37-dbb1-4c8c-9931-a76f00ea4669",
  "status": {
	"id": "PreProcessing",
	"name": "Обрабатывается"
  },
  "costPerRequest": {
	//..
  },
  "correspondence": {
	//..
  },
  "createdAtUtc": "2017-05-10T14:12:58",
  "medicalReport": {
    //..
  },
  "doctor": {
	//..
  },
  "statuses": [
	//..
  ],
  "operations": [
	//..
  ],
  "timeline": [
	//..
  ],
  "feedbacks": [
	//..
  ]
}
```

## Voip

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
status | object | статус
createdAtUtc | datetime | дата создания
medicalReport | [MedicalReport](./contracts.md#medical-report) | заключение врача
feedbacks | array<[Feedback](./contracts.md#feedback)> | список отзывов
statuses | array<[StatusHistory](./contracts.md#status-history)> | история статусов консультации
doctor | [Doctor](./contracts.md#doctor) | врач, с которым проводится консультация
operations | array<[Operation](./contracts.md#operation)> | список проведённых операций
timeline | array<[TimelineEvent](./contracts.md#timeline-event)> | список возникавших событий
patientPhone | [Phone](./contracts.md#phone) | телефон, на который поступит звонок для консультации
videoSupport | boolean | поддержка видео-связи
patientFullName | string | фио пациента
costPerMinute | [Money](./contracts.md#money) | стоимость
calls | array<[Call](./contracts.md#call)> | список осуществлённых звонков

```json
{
    "id": "92606f49-9185-407e-b844-7734f0ffb170",
    "status": {
        "id": "Processed",
        "name": "Завершено"
    },
    "createdAtUtc": "2016-12-12T14:10:12",
    "medicalReport": {
        //..
    },
    "feedbacks": [
        //..
    ],
    "statuses": [
        //..
    ],
    "doctor": {
        //..
    },
    "operations": [
        //..
    ],
    "timeline": [
        //..
    ],
    "videoSupport": false,
    "patientFullName": "Иванов Пётр Сергеевич",
    "costPerMinuite": {
        //..
    },
    "calls": [
        //..
    ]
}
```

## Correspondence

Имя | Тип | Описание
--- | --- | ---
unreadCount | integer | кол-во непрочитанных сообщений
totalCount | integer | кол-во всего сообщений
message | [Message](./contracts.md#message) | последнее сообщение

```json
{
    "unreadCount": 0,
    "totalCount": 1,
    "message": {
        "id": "4cfaa854-a184-4856-ae5f-a76f00ea4672",
        "requestId": "273d9b37-dbb1-4c8c-9931-a76f00ea4669",
        "sender": {
            "id": "Patient",
            "name": "Пациент"
        },
        "text": "hi, i've got a problem 2...",
        "attachment": null,
        "createdAtUtc": "2017-05-10T14:12:58",
        "readAtUtc": null
    }
}
```

## Message

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
requestId | string | идентификатор консультации
sender | object | отправитель (участник)
text | string | текстовое содержимое сообщения
attachment | object | приложение (объект медиа)
createdAtUtc | datetime | дата создания
readAtUtc | datetime | дата прочтения адресатом

```json
{
    "id": "af84c649-802f-42e6-abff-a74a00abc271",
    "requestId": "273d9b37-dbb1-4c8c-9931-a76f00ea4669",
    "sender": {
        "id": "Patient",
        "name": "Пациент"
    },
    "text": "oh, i'm really sick. have you got anythyng to help me?",
    "attachment": null,
    "createdAtUtc": "2017-04-03T10:25:21",
    "readAtUtc": null
}
```

## Mime Type Category

ID | Названия категорий | Название для отображения
--- | --- | ---
0 | Default | Файл
1 | Application | Документ
2 | Audio | Звукозапись
3 | Image | Изображение
4 | Message | Документ
5 | Model | Документ
6 | Multipart | Документ
7 | Text | Документ
8 | Video | Видео
9 | VND | Документ
10 | X | Файл
11 | X_PKCS | Файл

## Media

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
url | string | url медиа
name | string | наименование
mime | string | mime-type
mimeCategoryId | integer | ID [MIME-категории](./contracts.md#mime-type-category)
size | integer | размер byte
image | object | информация об изображении

```json
{
    "id": "6bde2fff-0dd1-4669-9f31-a78477b232c9",
    "url": "https://devapidoctortm.doktornarabote.ru/api/v1/media/get/6bde2fff-0dd1-4669-9f31-a78477b232c9",
    "name": "artifact-image.jpg",
    "mime": "image/jpeg",
    "size": 6222,
    "image": {
        "width": 246,
        "height": 163
    }
}
```

## Medical Report

Имя | Тип | Описание
--- | --- | ---
doctor | [Doctor](./contracts.md#doctor) | врач, который написал заключение (объект врач)
text | string | текстовое содержимое заключения (свободная форма)
createdAtUtc | datetime | дата создания
attachments | array<[Media](./contracts.md#media)> | массив вложений

```json
{
    "doctor": {
        //..
    },
    "text": "Ola!",
    "createdAtUtc": "2017-06-05T16:13:27",
    "attachments": [
        //..
    ]
}
```

## Profile

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
nickName | string | псевдоним
firstName | string | имя
lastName | string | фамилия
patronimycName | string | отчество
bornOn | datetime | дата рождения
weight | number | вес
sex | object | пол
photo | [Media](./contracts.md#media) | фотография
avatarUrl | string | адрес фото профиля
phone | [Phone](./contracts.md#phone) | телефон пользователя
balance | object | баланс пользователя, состоит из пары rub, bonus типа [Money](./contracts.md#money)
createdAtUtc | datetime | дата создания профиля
isDeleted | boolean | индикатор удаления профиля

```json
{
    "id": "2fbee309-b324-4f72-8e35-ee8a0907a9c6",
    "firstName": "Иван",
    "lastName": "Алексеев",
    "patronimycName": "Сергеевич",
    "bornOn": "1980-05-25T00:00:00",
    "weight": 95.3,
    "sex": {
        "id": "M",
        "name": "Муж."
    },
    "photo": {
        //
    },
    "avatarUrl": "https://...",
    "phone": {
        //..
    },
    "balance": {
        "rub": {
            //..Money
        },
        "bonus": {
            //..Money
        }
    },
    "createdAtUtc": "2017-11-20T00:00:00",
    "isDeleted": false
}
```

## Medical Report

Имя | Тип | Описание
--- | --- | ---
text | string | текст заключения
createdAtUtc | datetime | дата создания
consultation | [ConsultationDescription](./contracts.md#consultation-description) | краткое описание консультации
attachments | array<[Media](./contracts.md#media)> | дата начала

```json
{
    "text": "eb70612a-c05c-42da-a533-a6ce014bf055",
    "createdAtUtc": "2016-11-30T17:07:47",
    "consultation": {
        //..описание_консультации
    },
    "attachments": [
        {
            //..медиа
        }
    ]
}
```

## Call

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
actor | object | участник (владелец телефонного номера)
duration | integer | продолжительность
startedAtUtc | datetime | дата начала
successful | boolean | признак успешно состоявшего звонка

```json
{
    "id": "eb70612a-c05c-42da-a533-a6ce014bf055",
    "actor": {
        "id": "Patient",
        "name": "Пациент"
    },
    "duration": 17,
    "startedAtUtc": "2016-11-30T17:07:47",
    "successful": true
}
```

## Status History

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
status | object | статус
actor | object | участник (инициатор действия)
createdAtUtc | datetime | дата создания

## Transaction

Имя | Тип | Описание
--- | --- | ---
amount | [Money](./contracts.md#money) | сумма
createdAtUtc | datetime | дата создания
completedAtUtc | datetime | дата завершения
correspondentAccountId | string | идентификатор корреспондентского счёта
operation | [Operation](./contracts.md#operation) | операция, в рамках которой проводилась транзакция

## Operation

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
type | [OperationType](./contracts.md#operationtype) | тип операции
description | string | описание
createdAtUtc | datetime | дата создания
completedAtUtc | datetime | дата завершения

## OperationType

Возможные значения: `Deposit`, `Withdraw`.

Имя | Тип | Описание
--- | --- | ---
id | string | идентификатор внутри системы
name | string | название для отображения пользователю

```json
{
    "id": "Deposit",
    "name": "Пополнение счёта"
}
```

## Request Status

Значения, в скобках указано численное соответствие:
  * `Registered` (`1`);
  * `PreProcessing` (`2`);
  * `Delayed` (`3`);
  * `Processing` (`4`);
  * `PostProcessing` (`5`);
  * `Processed` (`6`);
  * `Unsuccessful` (`7`).

## Request Type

Значения:
  * `Callback` (`1`);
  * `Writing` (`2`);
  * `Voip` (`3`);
  * `Video` (`4`).

## Timeline Event

Имя | Тип | Описание
--- | --- | ---
id | string | уникальный идентификатор
type | object | тип события
createdAtUtc | datetime | дата возникновения
data | object | специфичные событию данные

## Feedback

Имя | Тип | Описание
--- | --- | ---
rate | number | оценка
comment | string | текстовый комментарий
createdAtUtc | datetime | дата добавления
actor | object | участник (инициатор действия)

```json
{
    "rate": 5,
    "comment": "Елена Сергеевна чудесный специалист и просто волшебница...",
    "createdAtUtc": "2017-05-10T10:55:04",
    "actor": {
        "id": "Patient",
        "name": "Пациент"
    }
}
```

## PushSubscription

Имя | Тип | Описание
--- | --- | ---
endpoint | string | адрес подписки на push-сервере
keys | object | VAPID-ключи

```json
{
    "endpoint": "https://...",
    "keys": {
        "p256dh": "p256dh_key",
        "auth": "auth_key"
    }
}
```

## Регион

Имя | Тип | Описание
--- | --- | ---
id | integer | уникальный идентификатор
name | string | Наименование

```json
{
    "id": 3001,
    "name": "Россия, Москва"
}
```

## Учёная степень

Имя | Тип | Описание
--- | --- | ---
id | integer | уникальный идентификатор
name | string | Наименование

```json
{
    "id": 1,
    "name": "Кандидат медицинских наук"
}
```

## Должность

Имя | Тип | Описание
--- | --- | ---
id | integer | уникальный идентификатор
name | string | Наименование

```json
{
    "id": 1,
    "name": "Ассистент кафедры"
}
```

## Специальность

Имя | Тип | Описание
--- | --- | ---
id | integer | уникальный идентификатор
name | string | Наименование

```json
{
    "id": 1,
    "name": "Авиационная и космическая медицина"
}
```
