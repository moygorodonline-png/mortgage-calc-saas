# 📋 Сессия 4: Инфраструктура + Backend

**Дата:** 20.03.2026  
**Продолжительность:** ~5 часов  

---

## ✅ Выполнено

### 1.1.1 — Домен
- Куплен `lead-calculator.ru` на reg.ru

### 1.1.2 — VPS
- IP: 45.144.178.31, Ubuntu 24.04
- Стек: Nginx 1.24, MySQL 8.0, PHP 8.3, Composer 2.9.5
- БД: `mortgage_calc`, пользователь: `mortgage`
- SSL: Let's Encrypt (https://lead-calculator.ru)
- SSH: PuTTY + beget_key.ppk (без пароля)

### 1.1.4 — Деплой
- Репозиторий склонирован в `/var/www/lead-calculator`
- Скрипт: `bash /var/www/lead-calculator/deploy.sh`

### 1.2.1 — Laravel
- Laravel 11 установлен
- .env настроен (MySQL, production)
- Миграции выполнены

### 1.2.2 — Структура БД
- Таблицы: clients, projects, banks, leads, api_keys
- Все миграции в `database/migrations/`

### 1.2.3 — Аутентификация API
- Middleware: `App\Http\Middleware\ValidateApiKey`
- Alias: `api.key`
- Модели: Client, Project, Bank, Lead, ApiKey
- Метод генерации ключа: `ApiKey::generate()` → префикс `lc_`

### 1.3.1 — API банков
- Эндпоинт: `GET /api/v1/banks?program=base`
- Аутентификация по заголовку `X-API-Key` или query `api_key`
- Кеширование: 1 час
- ✅ Протестировано в браузере

---

## 🔑 Тестовые данные

- **API ключ:** `lc_TDqtRD03LrYo55LgjNi7lxihB1gtJFC8NcQigqoO`
- **Клиент:** Тест (test@test.ru), id=1
- **Проект:** Тестовый проект (test.ru), id=1
- **Банки:** ПСБ (20.29%), Сбер (21.50%), ВТБ (22.00%)

---

## 🎯 Следующая задача

**1.3.2 — API расчёта ипотеки** `POST /api/v1/calculate`

Логика:
- Принимает: цену, взнос, срок, программу, маткапитал
- Считает сумму кредита
- Для каждого банка считает ежемесячный платёж
- Возвращает отсортированный список банков

---

## 📌 Важные детали

- PuTTY подключение: IP `45.144.178.31`, ключ `beget_key.ppk` с рабочего стола
- Рабочая директория на сервере: `/var/www/lead-calculator`
- Кириллица в JSON — нормально, браузер отображает корректно
- Контроллеры API в папке `app/Http/Controllers/Api/`
- Маршруты API в `routes/api.php`
