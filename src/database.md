# База данных

Postgresql используется как основная база банных, на момент написания документации версия `13.20`.

Кластер работает без контейнеризации, pgsql установлен в системе.

Приложение npchat подключается к БД без пароля, так работает только на `localhost`. Для возможности подключаться извне сервера (из интернета), был создан firwalld-сервис `npcdbservice`, открывающий порт `5444` и установлены соответствующие настройки в `/var/lib/pgsql/data/postgresql.conf`.

### Миграции

Посмотреть актуальную версию схемы БД: `SELECT * FROM "schema_migrations"`.

Для применения миграций используется cli-приложение [migrate](https://github.com/golang-migrate/migrate), а также для создания пустых up/down файлов в директории [npchat/infra/pgsql/init](https://github.com/nice-pea/npchat/tree/master/infra).

Также `migrate` умеет генертровать файлов с нужным названием под миграции, а порядок использования такой - в проекте npchat перейти в директорию `npchat/infra/pgsql/` и выполнить команду:
```sh
migrate create -ext sql -seq migration_name
```
После чего будут созданы два файла: `000042_migration_name.down.sql` и `000042_migration_name.up.sql`.
 
Перед применением миграций ознакомиться с правилами выполнения и [документацией migrate](https://github.com/golang-migrate/migrate). Для применения миграций, перейти в директорию `npchat/infra/pgsql/` и выполнить команду:
```sh
migrate -path ./ --database datasourcename up
```