## Описание

Яндекс Практикум. Спринт 9. Итоговый проект. API для Yatube.

## Функционал

- Подписка и отписка от авторизованного пользователя;
- Авторизованный пользователь просматривает посты, создавёт новые, удаляет и изменяет их;
- Просмотр сообществ;
- Комментирование, просмотр, удаление и обновление комментариев;
- Фльтрация по полям.

## Установка

1. Клонировать репозиторий:

   ```python
   git clone https://github.com/dopioxdiavolo/api_final_yatube
   ```

2. Перейти в папку с проектом:

   ```python
   cd api_final_yatube/
   ```

3. Установить виртуальное окружение для проекта:

   ```python
   python -m venv venv
   ```

4. Активировать виртуальное окружение для проекта:

   ```python
   # для OS Lunix и MacOS
   source venv/bin/activate

   # для OS Windows
   source venv/Scripts/activate
   ```

5. Установить зависимости:

   ```python
   python3 -m pip install --upgrade pip
   pip install -r requirements.txt
   ```

6. Выполнить миграции на уровне проекта:

   ```python
   cd yatube
   python3 manage.py makemigrations
   python3 manage.py migrate
   ```

7. Запустить проект:

   `python manage.py runserver`

## Примеры запросов

Получение токена

Отправить POST-запрос на адрес `api/v1/jwt/create/` и передать 2 поля в `data`:

1. `username` - имя пользователя.
2. `password` - пароль пользователя.

Создание поста

Отправить POST-запрос на адрес `api/v1/posts/` и передать обязательное поле `text`, в заголовке указать `Authorization`:`Bearer <токен>`.

1. Пример запроса:

   ```json
   {
     "text": "Пост 1"
   }
   ```

2. Пример ответа:

   ```json
   {
     "id": 2,
     "author": "Katya",
     "text": "Пост 1",
     "pub_date": "2025-03-27T12:00:22.021094Z",
     "image": null,
     "group": null
   }
   ```

Комментирование поста пользователя

Отправить POST-запрос на адрес `api/v1/posts/{post_id}/comments/` и передать обязательные поля `post` и `text`, в заголовке указать `Authorization`:`Bearer <токен>`.

1. Пример запроса:

   ```json
   {
     "post": 1,
     "text": "Пост 1"
   }
   ```

2. Пример ответа:

   ```json
   {
     "id": 1,
     "author": "Katya",
     "text": "Пост 1",
     "created": "2025-03-27T12:06:13.146875Z",
     "post": 1
   }
   ```

## Ресурсы

```python
# Документаия проекта
http://127.0.0.1:8000/redoc/
```

```python
# ПО для тестирования API, Postman
https://www.postman.com/
```
