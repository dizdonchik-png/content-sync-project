# Используем официальный образ PHP с FPM
FROM php:8.2-fpm

# Устанавливаем системные зависимости и расширения PHP для WordPress
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    zip \
    libzip-dev \
    unzip \
    git \
    curl \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd mysqli pdo_mysql zip

# Устанавливаем Composer внутрь контейнера
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Устанавливаем рабочую директорию
WORKDIR /var/www/html

# Копируем файлы Bedrock (они уже должны быть в папке backend или появятся там)
COPY . .

# Разрешаем запуск Composer от суперпользователя
ENV COMPOSER_ALLOW_SUPERUSER=1

# Права доступа
RUN chown -R www-data:www-data /var/www/html