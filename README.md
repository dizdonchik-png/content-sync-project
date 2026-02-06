# Content Sync Project

Полноценная инфраструктура для тестового задания: WordPress (Bedrock) + Next.js  16 + Nginx + Docker Compose. Проект реализует синхронизацию контента, REST API и фронтенд‑интерфейс для отображения постов.

## Стек технологий
**Компонент - Технология**<br>
Backend - WordPress (Bedrock), PHP 8.2, Composer<br>
Frontend - Next.js 16, React 18, Node.js 20<br>
Reverse Proxy - Nginx<br>
База данных - MariaDB<br>
Инфраструктура - Docker, Docker Compose<br>
API - Custom WP REST API endpoint<br>

## Запуск проекта

### 1. Клонировать репозиторий
git clone https://github.com/dizdonchik-png/content-sync-project.git
cd content-sync-project

### 2. Создать файл окружения
cp .env.example .env<br><br>
Заполнить переменные для WordPress, MariaDB и URL проекта.

### 3. Запустить проект
docker compose up -d --build

### 4. Доступы
- Frontend: http://localhost:8080  
- WordPress admin: http://localhost:8080/wp/wp-admin  
- API: http://localhost:8080/wp-json/content-sync/v1/posts  

## Структура проекта
backend/   — WordPress (Bedrock)<br>
frontend/  — Next.js  16<br>
docker/     — конфигурация Nginx<br>
.gitignore<br>
.dockerignore<br>
.editorconfig<br>
docker-compose.yml

## Функционал
- Кастомный REST API endpoint: /wp-json/content-sync/v1/posts. Возвращает список постов с полями: id, external_id, title, body. created_at
- В проекте реализован кастомный Gutenberg‑блок, который отображает данные из API и используется для демонстрации интеграции WordPress → Frontend
- Страницы Next.js:
  - `/` — последние 10 постов
  - `/posts` — все посты
  - `/posts/[id]` — детальная страница

## API‑клиент
Фронтенд получает данные из WordPress через:<br>
http://content_sync_nginx/wp-json/content-sync/v1/posts<br>
Используется серверный рендеринг (Next.js App Router).
