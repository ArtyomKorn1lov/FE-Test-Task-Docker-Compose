# Docker compose для приложения FeTestTask

## Рекомендуется разворачивать в Unix-подобных ОС, в том числе WSL под Windows

### Cсылка на репозиторий с frontend - https://github.com/ArtyomKorn1lov/FE-Test-Task-Frontend

### Cсылка на репозиторий с backend - https://github.com/ArtyomKorn1lov/FE-Test-Task-Backend

## Краткая информация:

- мануальная установка миграций через интерактивный режим
- поддержка разработки внутри контейнера, через volumes (требуется указать другую команду для запуска в соответствующем
  dockerfile)
- образ node js 22, для frontend-приложения и backend-приложения
- образ mysql 9.3
- образ phpmyadmin 5.2.1
- конфигурации к данным образам
- в папку `/frontend` склонировать репозиторий с frontend'ом
- в папку `/backend` склонировать репозиторий с backend'ом

## Общий список команд:

1. Первичная сборка приложения и установка приложения и миграций:
    - `docker compose build --no-cache`
    - `docker compose up -d --remove-orphans`
    - `docker compose exec --user root backend /bin/sh`
    - `sh install.sh`
    - `exit`
    - `docker compose stop backend`
    - `docker compose start backend`
2. Cборка приложения без выполнения миграций:
    - `docker compose build --no-cache`
    - `docker compose up -d --remove-orphans`
3. Остановить контейнеры:
    - `docker compose stop`
4. Запуск контейнеров:
    - `docker compose start`
5. Список контейнеров:
    - `docker compose ps`
6. Логи контейнеров:
    - `docker compose logs`
7. Пересобрать приложение:
    - `docker compose stop`
    - `docker compose pull`
    - `docker compose rm --force frontend`
    - `docker compose rm --force backend`
    - `docker compose build --no-cache`
    - `docker compose up -d --force-recreate`
8. Удалить образы и контейнеры:
    - `docker compose down -v`
    - `docker compose down`
9. Интерактивный режим контейнеров:
    - `docker compose exec --user root frontend /bin/sh`
    - `docker compose exec --user root backend /bin/sh`
10. Установка приложения и миграций для БД, внутри интерактивного режима контейнера:
- `sh install.sh`