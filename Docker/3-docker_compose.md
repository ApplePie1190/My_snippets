# Dockercompose

Создаем докеркомпоз, phpmyadmin с бд mysql.

```
touch docker-compose.yml
```

```
version: '3.1'

services:
  db:
    image: mysql
    command: --default-authentication-plugin=mysql_native_password
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: example

  phpmyadmin:
    image: phpmyadmin
    restart: always
    ports:
      - 8080:80
    environment:
      - PMA_ARBITRARY=1
```

Создание образа, из папки где лежит Dockerfile запускаем терминал

```
docker-compose build -t <image_name> .
```

Проверим наш образ

```
docker-compose images
```

Запуск проекта

```
docker-compose up <image_id>
```

Удаление проекта

```
docker-compose rm <image_id>
```
