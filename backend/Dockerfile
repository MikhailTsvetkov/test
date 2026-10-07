FROM php:7.4-cli-bullseye
RUN sed -i \
        's|http://deb.debian.org/debian-security|https://archive.debian.org/debian-security|g' \
        /etc/apt/sources.list \
    && apt-get update \
    && apt-get install -y --no-install-recommends libpq-dev \
    && docker-php-ext-install pgsql \
    && rm -rf /var/lib/apt/lists/*
WORKDIR /app
ENV PHP_CLI_SERVER_WORKERS=4
CMD ["php", "-d", "display_errors=0", "-S", "0.0.0.0:8080", "-t", "public", "public/router.php"]
