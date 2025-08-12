# Инфраструктура

Код инфраструктры хранится в своем [репозитортии](https://github.com/nice-pea/infra).

Рабочая директория на сервере - `/opt/npchat/infra`.

Для обновления кода используется ручной подход с `git pull`.

Резвертывание просходит вручную. Пример с запуском обновленной кофигурации traefik:
```sh
cd /opt/npchat/infra
git pull
docker compose -f traefik/docker-compose.yaml restart
```
# Ключевые компоненты

### Traefik - Reverse proxy

Документация: https://doc.traefik.io/traefik/

Доступ: https://traefik.dsaime.ru/


### Grafana - Мониторинг

Документация: https://grafana.com/docs/grafana/latest/

Доступ: https://grafana.dsaime.ru/


### Prometheus - Сбор и хранение метрик

Документация: https://prometheus.io/docs/introduction/overview/


### Loki - Сбор и хранение логов

Документация: https://grafana.com/docs/loki/latest/


### Adminer - Database management tool

Сайт: https://www.adminer.org/en/

Доступ: https://adminer.dsaime.ru/