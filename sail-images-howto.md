# 🐳 Laravel Sail — настройка изображений и публичного доступа

## 1. Проверка структуры проекта

Убедись, что в проекте есть каталоги:
```
/public
/storage
/storage/app/public
```

---

## 2. Настройка `docker-compose.yml`

Открой файл `docker-compose.yml` и добавь монтирование каталогов:

```yaml
laravel.test:
  build:
    context: ./vendor/laravel/sail/runtimes/8.2
    dockerfile: Dockerfile
    args:
      WWWGROUP: '${WWWGROUP}'
  image: sail-8.2/app
  extra_hosts:
    - 'host.docker.internal:host-gateway'
  ports:
    - '${APP_PORT:-80}:80'
    - '${VITE_PORT:-5173}:${VITE_PORT:-5173}'
  environment:
    WWWUSER: '${WWWUSER}'
    LARAVEL_SAIL: 1
  volumes:
    - .:/var/www/html
    - ./storage:/var/www/html/storage
    - ./public:/var/www/html/public
  networks:
    - sail
  depends_on:
    - mysql
```

🟢 Эти строки гарантируют, что изображения сохраняются и видны на хосте:
```yaml
- ./storage:/var/www/html/storage
- ./public:/var/www/html/public
```

---

## 3. Перезапуск Sail

```bash
./vendor/bin/sail down -v
./vendor/bin/sail up -d
```

---

## 4. Создание симлинка

```bash
./vendor/bin/sail artisan storage:link
```

Проверка:
```bash
ls -l public | grep storage
# должно быть -> storage -> ../storage/app/public
```

---

## 5. Права доступа

```bash
./vendor/bin/sail artisan optimize:clear
sudo chmod -R 775 storage bootstrap/cache
sudo chown -R $USER:www-data storage bootstrap/cache
```

---

## 6. Тест загрузки

```php
Storage::disk('public')->put('test.jpg', file_get_contents('https://via.placeholder.com/150'));
```

Затем открой в браузере:
```
http://localhost/storage/test.jpg
```

---

## ✅ Результат

Теперь:
- все загружаемые файлы сохраняются в `storage/app/public`
- доступны по `/storage/...`
- не теряются при перезапуске контейнера
