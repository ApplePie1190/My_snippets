# Команды Docker

Запуск контейнера
run запуск и скачивание, если отсутстувет контейнер
-d запуск в фоне
-p соединить порты

```
docker run -d -p 80:80 docker/getting-started
```

Информация об образах и контейнерах

```
docker info
```

Информация об образах

```
docker images
```

Информация о контейнерах

```
docker ps
```

Остановить один или несколько контейнеров

```
docker stop <container_id>
```

Запустить один или несколько контейнеров

```
docker start <container_id>
```

Перезапуск один или несколько контейнеров

```
docker restart <container_id>
```

Поставить на паузу один или несколько контейнеров

```
docker pause <container_id>
```

Снять с паузы один или несколько контейнеров

```
docker unpause <container_id>
```
