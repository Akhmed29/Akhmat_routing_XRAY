# Akhmat Routing XRAY

Автоматически обновляемые базы геоданных для Xray-core.

Файлы собираются на основе правил Loyalsoldier. Скрипт GitHub Actions каждый день забирает свежие версии, сжимает их с максимальной компрессией в формат `.gz` и публикует в релизах. Это экономит трафик мобильных клиентов и ускоряет запуск прокси.

## Прямые ссылки на актуальные версии

В ссылках используется тег `latest`, поэтому они всегда ведут на самую свежую ночную сборку:

* [geoip.dat.gz](https://github.com/Akhmed29/Akhmat_routing_XRAY/releases/latest/download/geoip.dat.gz)
* [geosite.dat.gz](https://github.com/Akhmed29/Akhmat_routing_XRAY/releases/latest/download/geosite.dat.gz)

## Использование в Xray

Ядро Xray (начиная с версии 1.8.0) умеет скачивать и распаковывать `.gz` архивы на лету. 

Добавьте этот блок `geodata` в серверный или клиентский `config.json`. Xray будет сам проверять обновления раз в сутки:

```json
  "geodata": {
    "cron": "0 4 * * *",
    "assets": [
      {
        "url": "[https://github.com/Akhmed29/Akhmat_routing_XRAY/releases/latest/download/geoip.dat.gz](https://github.com/Akhmed29/Akhmat_routing_XRAY/releases/latest/download/geoip.dat.gz)",
        "file": "geoip.dat"
      },
      {
        "url": "[https://github.com/Akhmed29/Akhmat_routing_XRAY/releases/latest/download/geosite.dat.gz](https://github.com/Akhmed29/Akhmat_routing_XRAY/releases/latest/download/geosite.dat.gz)",
        "file": "geosite.dat"
      }
    ],
    "outbound": "direct"
  }
