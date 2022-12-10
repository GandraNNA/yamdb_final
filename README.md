# yamdb_final

## _**Описание**_

Групповой проект API YaMDb. Социальная сеть, в которой хранятся
произведения (книги, фильмы или музыка) с возможностью оставить отзыв.

## _**Установка**_

### Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/GandraNNA/infra_sp2.git
```

```
cd infra_sp2
```

### Создайте в папке infra файл '.env' и добавте туда:

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

Сгенерировать и получить секретный ключ можно выполнив такой python
код:

```
from django.core.management.utils import get_random_secret_key
print(get_random_secret_key())
```

### Перейти в директорию с файлом docker-compose и выполнить:
```
cd infra
```
```
sudo docker-compose up -d --build
```

### Выполнить миграции внутри контейнера, создайте пользователя и соберите статику:

```
docker-compose exec web python manage.py migrate
```

```
docker-compose exec web python manage.py createsuperuser
```

```
docker-compose exec web python manage.py collectstatic --no-input
```

### Создайте резервную копию БД:

```
docker-compose exec web python manage.py dumpdata > fixtures.json
```

В PyCharm активировать виртуальное окружение в терминале можно так:

```
.\venv\Scripts\activate.ps1
```

### Обновить pip:

```
python -m pip install --upgrade pip
```

### Установить зависимости из файла requirements.txt:

```
pip install -r requirements.txt
```

### Выполнить миграции:

```
python manage.py migrate
```

### Запустить проект:

```
python manage.py runserver
```

## _**Некоторые примеры запросов.**_

Можно поcмотреть после установки проекта по ссылке:
http://localhost/redoc/

### _**Автор:**_

_**Анна Гандрабура**_
