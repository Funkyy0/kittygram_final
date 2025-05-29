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
``` Для развертывания проекта необходимо выполнить следующие шаги:
sudo apt update
sudo apt install curl
curl -fSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo apt-get install docker-compose-plugin;
# Переходим в директорию проекта.
cd kittygram_final/
Заполнить файл `env` с необходимыми переменными окружения.
sudo docker compose -f docker-compose.production.yml pull
sudo docker compose -f docker-compose.production.yml down
sudo docker compose -f docker-compose.production.yml up -d
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collect_static/. /static_backend/static/
# Создаем суперпользователся. Следуем инструкциям при выполнении.
sudo docker compose -f docker-compose.production.yml exec backend python manage.py createsuperuser
```
Устанавливаем и настраиваем NGINX

```bash
# Устанавливаем NGINX
sudo apt install nginx -y
# Запускаем
sudo systemctl start nginx
# Настраиваем firewall
sudo ufw allow 'Nginx Full'
sudo ufw allow OpenSSH
# Включаем firewall
sudo ufw enable
# Открываем конфигурационный файл NGINX
sudo nano /etc/nginx/sites-enabled/default
# Заполняем файл конфигурации
# Проверяем корректность настроек
sudo nginx -t
# Запускаем NGINX
sudo systemctl start nginx
```
Настраиваем HTTPS

```bash
# Установка пакетного менеджера snap.
# У этого пакетного менеджера есть нужный вам пакет — certbot.
sudo apt install snapd
# Установка и обновление зависимостей для пакетного менеджера snap.
sudo snap install core; sudo snap refresh core
# При успешной установке зависимостей в терминале выведется:
# core 16-2.58.2 from Canonical✓ installed 

# Установка пакета certbot.
sudo snap install --classic certbot
# При успешной установке пакета в терминале выведется:
# certbot 2.3.0 from Certbot Project (certbot-eff✓) installed

# Создание ссылки на certbot в системной директории,
# чтобы у пользователя с правами администратора был доступ к этому пакету.
sudo ln -s /snap/bin/certbot /usr/bin/certbot

# Получаем сертификат и настраиваем NGINX следуя инструкциям
sudo certbot --nginx
# Перезапускаем NGINX
sudo systemctl reload nginx
```

## Что нужно для файла env

Вам нужно создать файл `.env` и заполнить его следующими переменными окружения:

```dotenv
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram
DB_PORT=5432
SECRET_KEY="secret_key"
DEBUG=False
ALLOWED_HOSTS=allowed_hosts,server_ip
```

### Автор
[Даян](https://github.com/Funkyy0)
