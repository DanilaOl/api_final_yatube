# API_Final_Yatube
## Описание
Учебный проект для Яндекс.Практикума в рамках изучения Django Rest Framework
Проект представляет собой REST API для социальной сети, в которой пользователи могут создавать посты, оставлять комментарии, подписываться на других пользователей

## Как запустить проект
Клонировать репозиторий и перейти в него в командной строке:
```
cd api_final_yatube
```
Создать и активировать виртуальное окружение:
```
python -m venv venv
```
```
source env/bin/activate
```
Установить зависимости:
```
pip install -r requirements.txt
```
Выполнить миграции:
```
python yatube_api/manage.py migrate
```
Запустить сервер разработки:
```
python yatube_api/manage.py runserver
```
## Примеры
### Список постов
Запрос:
```
GET /api/v1/posts/ HTTP/1.1
Host: 127.0.0.1:8000
```
Ответ:
```
[
    {
        "id": 1,
        "author": "regular_user",
        "text": "Пост зарегистрированного пользователя.",
        "pub_date": "2025-04-01T20:34:57.008146Z",
        "image": null,
        "group": null
    },
    {
        "id": 2,
        "author": "regular_user",
        "text": "Пост с группой",
        "pub_date": "2025-04-01T20:34:57.102727Z",
        "image": null,
        "group": 1
    }
]
```

### Создание поста
Запрос:
```
POST /api/v1/posts/ HTTP/1.1
Host: 127.0.0.1:8000
Content-Type: application/json
Authorization: ••••••
Content-Length: 56

{
    "text": "Пост зарегистрированного пользователя."
}
```
Ответ:
```
{
    "id": 1,
    "author": "regular_user",
    "text": "Пост зарегистрированного пользователя.",
    "pub_date": "2025-04-01T20:34:57.008146Z",
    "image": null,
    "group": null
}
```
### Получение токена
Запрос:
```
POST /api/v1/jwt/create/ HTTP/1.1
Host: 127.0.0.1:8000
Content-Type: application/json
Content-Length: 67

{
    "username": "regular_user",
    "password": "iWannaBeAdmin"
}
```
Ответ:
```
{
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTc0MzYyNjA5NiwianRpIjoiYzhiYjBjZTM5NjUyNDEzYmI5MWQ3NDA3MjEzMzgzNzgiLCJ1c2VyX2lkIjoyfQ.nGV-eujG1U2A3NqNm_Qc4YFyjKaXMd9WJvDfgnaIaV8",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNzQzNTQzMjk2LCJqdGkiOiJhODc5YTk2OGU5M2Y0NzhlYTMwMmQ4NGJlZjUxZjIwNCIsInVzZXJfaWQiOjJ9.v2t8IiN7o3ELWD2AMP_Wr2Q2HRylON7vvTu3fz8n0q0"
}
```

### Документация
Документация для API доступна по URL:
```
http://127.0.0.1:8000/redoc/
```
