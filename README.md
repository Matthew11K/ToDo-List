## Описание проекта

Разработан с использованием языка программирования **Go** и веб-фреймворка **Gin** для создания бэкенда. Приложение предоставляет API для создания, чтения, обновления и удаления задач. Данные о задачах хранятся в базе данных **PostgreSQL**. Для обеспечения безопасности и персонализации, приложение имеет систему регистрации и аутентификации пользователей. Пароли хешируются перед сохранением в базе данных.

## Аутентификация

Процесс аутентификации осуществляется с помощью **JWT**. При успешной аутентификации пользователя, сервер генерирует JWT токен с использованием библиотеки `github.com/dgrijalva/jwt-go`. Этот токен содержит зашифрованную информацию о пользователе, включая его идентификатор и срок действия токена.

Полученный JWT токен возвращается клиенту и должен быть включен в заголовок `Authorization` для последующих запросов к API. На стороне сервера токен проверяется с помощью секретного ключа, и если он действителен, запрос обрабатывается соответствующим образом.

## Middleware для проверки JWT

Для обработки запросов, требующих аутентификации, реализован middleware для проверки JWT токена в заголовке запроса. Если токен отсутствует, невалиден или истек, запрос отклоняется с соответствующим статусом ошибки. Таким образом, приложение обеспечивает безопасный доступ к функциональности только для аутентифицированных пользователей, предотвращая несанкционированный доступ к данным и операциям с задачами.




### Для запуска приложения:
Выполните следующую команду:
```bash
make build && make run
```

Если приложение запускается впервые, необходимо применить миграции к базе данных:
```bash
make migrate
```