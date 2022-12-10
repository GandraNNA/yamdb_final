# yamdb_final

![Build status](https://github.com/GandraNNA/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Описание

Групповой проект API YaMDb. Социальная сеть, в которой хранятся
произведения (книги, фильмы или музыка) с возможностью оставить отзыв.

## Установка

Клонировать репозиторий и перейти в него в командной строке:

```
$ git clone https://github.com/GandraNNA/infra_sp2.git
$ cd infra_sp2
```

Создайте в папке "infra" файл ".env" и добавьте туда:

```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```

А так же сгенерируйте секретный ключ и вставьте его в формате:

```
SECRET_KEY='your_key'
```

Сгенерировать и получить секретный ключ можно выполнив такой код:

```
$ from django.core.management.utils import get_random_secret_key
print(get_random_secret_key())
```

Перейти в директорию с файлом docker-compose и выполнить:
```
$ cd infra
$ sudo docker-compose up -d --build
```

Выполнить миграции внутри контейнера, создайте пользователя и соберите статику:

```
$ docker-compose exec web python manage.py migrate
$ docker-compose exec web python manage.py createsuperuser
$ docker-compose exec web python manage.py collectstatic --no-input
```

Создайте резервную копию БД:

```
$ docker-compose exec web python manage.py dumpdata > fixtures.json
```

## Некоторые примеры запросов.

Можно поcмотреть после установки проекта по ссылке:
http://localhost/redoc/

## Автор

[Анна Гандрабура](https://github.com/GandraNNA)
