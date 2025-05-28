#  Проект Kittygram

[![Main kittygram workflow](https://github.com/Funkyy0/kittygram_final/actions/workflows/main.yml/badge.svg?branch=main)](https://github.com/Funkyy0/kittygram_final/actions/workflows/main.yml)

## Что такое Kittygram

Kittygram - социальная сеть для любителей кошатников.

## Описание

На этом сайте вы можете: 
 - Делиться фотографиями своих котиков
 - Смотреть котиков других пользователей
 - Присваивать достижения своему котику или использовать уже имеющиеся достижения

## Технологии 

- **Backend**: Django, PostgreSQL (используется в качестве базы данных)
- **Frontend**: JavaScript
- **Сборка и развертывание**: Docker, GitHub Actions

## Как запустить проект 

Для развертывания проекта необходимо выполнить следующие шаги:

1. Клонировать репозиторий.
2. Заполнить файл `env` с необходимыми переменными окружения.
3. Выполнить развертывание с помощью команды `docker-compose up`.

## Что нужно для файла env

Вам нужно создать файл `.env` и заполнить его следующими переменными окружения:

```dotenv
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram
DB_PORT=5432
```

### Автор
[Даян](https://github.com/Funkyy0)
