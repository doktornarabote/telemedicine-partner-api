# Push-уведомления - Android

## Объект Push-уведомления

Имя параметра Push-уведомления - content. Значение этого параметра есть строка в формате json следующего вида:

```json
{
  "category" : "$notificationType",
  "title" : "$title",
  "body" : "$body",
  "consultation": { /*$consultation*/ }
}
```

### Параметры:

1. `$title` - текстовый заголовок уведомления.
2. `$body` - содержание уведомления.
3. `$notificationType` - тип уведомления, может принимать одно из следующих значений: `ConsultationRegistered`, `ConsultationStarting`, `ConsultationPreFinished`, `ConsultationFinished`, `ConsultationCancelled`, `WritingMessageSent`, `Withdraw`, `ActivationCode`.
4. `$consultation` - объект краткой информации о состоянии запроса на консультацию вида `{ "id": "311932D6-C1BC-4AD3-9835-A6DE00C67194", "status": 1, "type": 3 }`,
где
  * id - уникальный идентификатор запроса на консультацию;
  * status - численное соответствие [Request Status](./contracts.md#request-status);
  * type - численное соответствие [Request Type](./contracts.md#request-type).

