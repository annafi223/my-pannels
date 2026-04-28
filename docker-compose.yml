version: '3.8'

services:
  database:
    image: mariadb:10.11
    restart: always
    volumes:
      - db_data:/var/lib/mysql
    environment:
      MYSQL_DATABASE: "panel"
      MYSQL_USER: "pterodactyl"
      MYSQL_PASSWORD: "panelfree"
      MYSQL_ROOT_PASSWORD: "panelfree"

  cache:
    image: redis:alpine
    restart: always

  panel:
    image: ghcr.io/pterodactyl/panel:latest
    restart: always
    ports:
      - "80:80"
    depends_on:
      - database
      - cache
    volumes:
      - panel_var:/app/var/
      - panel_logs:/app/storage/logs
    environment:
      APP_URL: "https://GANTI_DENGAN_DOMAIN_ZEABUR_KAMU"
      APP_TIMEZONE: "Asia/Jakarta"
      APP_SERVICE_AUTHOR: "admin@faridesu.com"
      TRUSTED_PROXIES: "*"
      APP_ENV: "production"
      CACHE_DRIVER: "redis"
      SESSION_DRIVER: "redis"
      QUEUE_DRIVER: "redis"
      REDIS_HOST: "cache"
      DB_HOST: "database"
      DB_PORT: "3306"
      DB_DATABASE: "panel"
      DB_USERNAME: "pterodactyl"
      DB_PASSWORD: "panelfree"

volumes:
  db_data:
  panel_var:
  panel_logs:
