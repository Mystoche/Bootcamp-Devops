# Utiliser une image PHP avec Apache
FROM php:8.2-apache

# Installer les dépendances
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libpq-dev \
    && docker-php-ext-install pdo pdo_pgsql

# Installer Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Définir le répertoire de travail
WORKDIR /var/www/html

# Copier les fichiers du projet
COPY . .

# Installer les dépendances Symfony
#RUN composer install --no-dev --optimize-autoloader

# Donner les droits nécessaires à Symfony
#RUN chown -R www-data:www-data /var/www/html/var

# Exposer le port 80
EXPOSE 80

# Commande pour démarrer Apache
CMD ["apache2-foreground"]

