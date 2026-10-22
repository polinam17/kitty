# Kittygram

Настроен запуск проекта Kittygram в контейнерах и CI/CD с помощью GitHub Actions.

## Что сделано

Проект запускается в Docker-контейнерах (gateway, backend, frontend, db). При пуше в ветку `main` GitHub Actions проверяет код, запускает тесты, собирает образы, отправляет их на Docker Hub и присылает уведомление в Telegram.

## Как запустить локально

```bash
cp .env.example .env
docker compose up --build
```

Проект будет доступен на http://localhost:9000

## Как проверить работу с помощью автотестов

В корне репозитория лежит файл `tests.yml` со следующим содержимым:

```yaml
repo_owner: albert-dvrk
kittygram_domain: http://localhost:9000
taski_domain: http://localhost:9000
dockerhub_username: darkalbert
```

Содержимое файла `.github/workflows/main.yml` скопировано в файл `kittygram_workflow.yml` в корневой директории проекта.

Для локального запуска тестов создайте виртуальное окружение, установите в него зависимости из `backend/requirements.txt` и запустите в корневой директории проекта `pytest`.

## Чек-лист для проверки перед отправкой задания

- Проект Kittygram запущен из контейнеров и доступен на localhost.
- Код проекта запушен на GitHub.
- Пуш в ветку `main` запускает тестирование и сборку образов, а после успешного выполнения приходит сообщение в Telegram.
- Образы `kittygram_backend`, `kittygram_frontend` и `kittygram_gateway` есть на Docker Hub.
- В корне проекта есть файл `kittygram_workflow.yml`.