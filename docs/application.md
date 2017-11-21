# Проверка наличия критических обновлений

## Проверка версии приложения

`GET /api/v1/application/updates` вернёт индикатор наличия критических обновлений.

### Запрос:

Имя | Тип | Описание
--- | --- | ---
operatingSystemName | string | название ОС (ios, android, etc.)
applicationVersion | string | версия приложения

### Ответ:

```json
{
  "item": true
}
```
