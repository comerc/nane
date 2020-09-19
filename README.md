# Ай-нане-нане

Тот самый цыганский сервер для тестового задания.



## Запуск 

Запуск не нужен, сервер **уже** работает по адресу http://nane.tada.team, но если очень хочется, можно запустить его локально:

```bash
go get -u github.com/tada-team/nane
$HOME/go/bin/nane
```

## HTTP API

Все вызовы доступны без авторизации.

 * Настройки сервера: `GET /api/settings`
 * Список комнат: `GET /api/rooms`
 * История сообщений: `GET /api/rooms/{name}/history`

## Веб-сокеты

Соединение: `/ws?username={username}`

По ws отправляются сообщения формата:

```text
{
  "room": string, // название комнаты. Если такой комнаты нет, она будет создана
  "text": string,  // текст сообщения
  "id": string // необязательный идентификатор, можно назначить на клиенте, чтобы получить подтверждение получения сообщения сервером
}
```

По ws приходят сообщения формата:
```text
{
  "room": string,
  "text": string,
  "id": string,
  "created": iso_datetime, // время создания сообщения 
  "sender": {"username": string} // информация об отправителе  
}
