FROM php:8.2-fpm

COPY php.ini /usr/local/etc/php/

# 必要なパッケージとPHP拡張モジュールをインストール
RUN apt-get update \
  && apt-get install -y git openssh-client zlib1g-dev mariadb-client vim libzip-dev libpq-dev libonig-dev zip unzip \
  && docker-php-ext-install zip pdo_pgsql mbstring bcmath


# php実行・デバッグで必要なライブラリをインストール
# RUN pecl install xdebug-3.1.5 && \
    # docker-php-ext-enable xdebug

# Composerのインストール
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin

# 作業ディレクトリの設定
WORKDIR /workspace

RUN composer global require "laravel/installer"