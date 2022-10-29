# Dockerfile

Создаем докерфайл, на образе python последней версии,
копируем файл зависимостей, устанавливаем библиотеки из
файла зависимостей, копируем все файлы проекта,
запускаем проект.

```
touch Dockerfile
```

```
FROM python:latest

WORKDIR /telebot

COPY requirements.txt ./

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD [ "python", "./main.py" ]
```

Создание образа, из папки где лежит Dockerfile запускаем терминал

```
docker build -t <image_name> .
```

Проверим наш образ

```
docker images
```

Запуск проекта

```
docker run <image_id>
```

Удаление проекта

```
docker rm <image_id>
```
