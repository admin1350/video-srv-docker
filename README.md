# video-srv-docker

docker-compose.yml

```yaml
services:
  jellyfin:
    image: lscr.io/linuxserver/jellyfin:latest
    container_name: jellyfin
    environment:
      - PUID=1000 # ID вашего пользователя в системе (выяснить можно командой `id`)
      - PGID=1000 # ID группы вашего пользователя
      - TZ=Europe/Moscow # Ваш часовой пояс
    volumes:
      - ./config:/config # Путь к конфигурационным файлам Jellyfin
      - ./path/to/movies:/data/movies # Путь к вашей коллекции фильмов (замените на свой)
      - ./path/to/tvseries:/data/tvshows # Путь к сериалам (замените на свой)
      - /opt/cloud/data/super/files:/data/video
    ports:
      - 8096:8096 # Основной веб-интерфейс
#     - 8920:8920 # HTTPS порт (опционально, если не используется reverse-proxy)
      - 7359:7359/udp # Автообнаружение в локальной сети (опционально)
    restart: unless-stopped
```
