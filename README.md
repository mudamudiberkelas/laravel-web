
git clone https://github.com/laravel/laravel.git laravel-web \
docker run --rm -v $(pwd):/app composer install \
sudo chown -R $USER:$USER ~/laravel-web \

docker-compose up -d \
docker ps \

### APP
docker-compose exec app bash \
php artisan key:generate \
php artisan config:cache  \

### MYSQL

docker-compose exec db bash \

mysql -u root -p \
show databases; \
GRANT ALL ON laravel_web.* TO 'laraveldocker'@'%' IDENTIFIED BY 'your_strong_laravel_docker_password'; \
FLUSH PRIVILEGES; \

docker-compose exec app bash \
php artisan migrate \
php artisan tinker \
\DB::select('show tables'); \
\DB::table('migrations')->get(); \