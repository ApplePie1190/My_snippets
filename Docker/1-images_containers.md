# Образы и контейнеры Docker

Загрузить образ с docker hub

```
docker pull <image_name>
```

Запустить образ

```
docker run <image_name>
```

Запустить образ в интерактивном режиме

```
docker run -it --name <container_name> <image_name>
```

- `Ctrl O` — Выход из запущенного контейнера

Запустить контейнер

```
docker start <container_name>
```

Остановить контейнер

```
docker stop <container_name>
```

Убить контейнер

```
docker kil <container_name>
```
