FROM php:8.2-fpm

# 必要なパッケージとPHP拡張モジュールをインストール
RUN apt-get update && apt-get install -y \
    zip unzip git curl libpq-dev \
    && docker-php-ext-install pdo pdo_pgsql

# Composerのインストール
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# 作業ディレクトリの設定
WORKDIR /workspace
