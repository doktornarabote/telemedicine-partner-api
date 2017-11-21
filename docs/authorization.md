# Авторизация

В API используется двухфакторная авторизация. Авторизация осуществляется с помощью СМС-уведомлений и протокола OAuth 2.0. Подробная документация по протоколу: [RFC 6749](http://tools.ietf.org/html/rfc6749). Для того, чтобы авторизоваться в приложении, необходимо сначала зарегистрировать номер телефона (п.1), затем подтвердить номер телефона, впоследствии получив token для авторизации в API.

## Регистрация номера телефона

Для регистрации номера телефона необходимо отправить GET-запрос на [https://testapipartner.doktornarabote.ru/api/v1/access/validation-code](https://testapipartner.doktornarabote.ru/api/v1/access/validation-code).

В запросе необходимо передать:

`code={country_code}&number={phone_number}`

Пример: https://testapipartner.doktornarabote.ru/api/v1/access/validation-code?code=1&number=1111111111

## Получение access и refresh токенов

Для получения пары access и refresh токенов необходимо сделать POST-запрос на [https://testauthpartner.doktornarabote.ru/token](https://testauthpartner.doktornarabote.ru/token).

В запросе необходимо передать:

`grant_type=password&client_id={client_id}&username={username}&password={validation_code}`

В качестве `{username}` указываются код страны и номер телефона, сложенные вместе. `{validation_code}` приходит на номер мобильного телефона в виде смс-уведомления.

Тело запроса необходимо передавать в стандартном application/x-www-form-urlencoded с указанием соответствующего заголовка Content-Type.

* Пример: 
  * URL: https://testauthpartner.doktornarabote.ru/token
  * Body: `grant_type=password&client_id=98483c47f17f4888b0bf695d1165062e&username=11111111111&password=7654`

В ответе вернётся JSON:

```json
{
  "access_token": "{access_token}",
  "token_type": "bearer",
  "expires_in": 1209599,
  "refresh_token": "{refresh_token}"
}
```

## Использование и проверка access_token

Для взаимодействия с платформой потребуется использовать полученный access_token для авторизации, передавая его в заголовке в формате:

`Authorization: Bearer ACCESS_TOKEN`
