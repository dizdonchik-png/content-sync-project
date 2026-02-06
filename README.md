# Content Sync Project

Проект состоит из:
- WordPress (Bedrock) — backend
- Next.js 16 — frontend
- Nginx — reverse proxy
- Docker Compose — инфраструктура

## 🚀 Запуск проекта

### 1. Клонировать репозиторий
git clone https://github.com/dizdonchik-png/content-sync-project.git
cd content-sync-project


### 2. Создать файл окружения
Скопировать `.env.example` → `.env` и заполнить переменные.

### 3. Запустить Docker
docker compose up -d --build

### 4. Доступы
- Frontend: http://localhost:8080  
- WordPress admin: http://localhost:8080/wp/wp-admin  
- API: http://localhost:8080/wp-json/content-sync/v1/posts  

## 🧱 Структура проекта
backend/   — WordPress (Bedrock)
frontend/  — Next.js  16
nginx/     — конфигурация Nginx
docker-compose.yml

## 🧪 Функционал
- Кастомный REST API endpoint для постов
- Gutenberg блок
- Страницы Next.js:
  - `/` — последние 10 постов
  - `/posts` — все посты
  - `/posts/[id]` — детальная страница

