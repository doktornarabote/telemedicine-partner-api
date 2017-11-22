# Push-уведомления

## Подписка

`POST /api/v1/push/subscribe`

Необходимо указать либо pushToken, либо subscription. Если указан pushToken, то subscription игнорируется.

### Запрос:

Имя | Тип | Описание
--- | --- | ---
pushToken | string | Token устройства, выданный Push-сервисом производителя
subscription | [PushSubscription](./contracts.md#pushsubscription) | объект подписки устройства с помощью VAPID-ключей
applicationId | string | ID приложения Телемедицины (отдельные ключи для iOS, Android, Chrome, Firefox, etc.)

### Ответ:

```json
{
  "item": "success"
}
```

## Отписка

`GET /api/v1/push/unsubscribe`.

Необходимо указать либо pushToken, либо subscription. Если указан pushToken, то subscription игнорируется.

### Запрос

Имя | Тип | Описание
--- | --- | ---
pushToken | string | Token устройства, выданный Push-сервисом производителя
subscription | [PushSubscription](./contracts.md#pushsubscription) | объект подписки устройства с помощью VAPID-ключей
applicationId | string | ID приложения Телемедицины (отдельные ключи для iOS, Android, Chrome, Firefox, etc.)

### Ответ

```json
{
  "item": "success"
}
```
