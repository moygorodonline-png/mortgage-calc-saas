# 🤖 Mortgage Calculator SaaS - Project Guide for Claude

**Project Name:** Ипотечный калькулятор для застройщиков  
**Type:** SaaS Lead Generation Tool  
**Owner:** Евгений Петров  
**Started:** 28.01.2025  

---

## 🎯 Project Overview

### Что мы делаем?

SaaS-платформа ипотечного калькулятора для сайтов застройщиков. **Не просто калькулятор**, а **инструмент лидогенерации** с автоматической передачей заявок в CRM.

### Ключевое отличие от конкурентов:

| Обычные калькуляторы | Наш калькулятор |
|----------------------|-----------------|
| Посмотрел → закрыл | Посмотрел → оставил заявку |
| Ознакомительная функция | Инструмент лидогенерации |
| Нет интеграций | CRM + Email + Telegram |

### Фишки продукта:

- 🔥 **Горячие лиды:** форма "Заявка с калькулятора" (имя + телефон)
- ❄️ **Холодные лиды:** форма "Отправить расчёт" (email / Telegram)
- 📊 **Полный контекст:** в CRM передаётся вся информация о расчёте
- 🏦 **Актуальные ставки:** мы обновляем данные банков централизованно
- 🔒 **Скрытые цены:** калькулятор работает, конкуренты не видят цены

---

## 🛠️ Tech Stack

### Backend
- **Language:** PHP 8.2+
- **Framework:** Laravel 11
- **Database:** MySQL 8.0
- **API:** RESTful JSON API
- **Cache:** Redis (опционально)

### Frontend
- **Widget:** Vanilla JavaScript (ES6+), no frameworks
- **Admin Panel:** Laravel Blade + Alpine.js
- **Styling:** Tailwind CSS
- **Build:** Vite

### Infrastructure
- **Server:** VPS Beget
- **Web Server:** Nginx
- **SSL:** Let's Encrypt
- **Deploy:** Git-based

### Integrations
- **CRM:** Bitrix24, Google Sheets (amoCRM - later)
- **Email:** SMTP (Yandex/Mail.ru)
- **Analytics:** Yandex.Metrika
- **Future:** Telegram Bot API

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────┐
│           НАШ СЕРВЕР (VPS Beget)                    │
├─────────────────────────────────────────────────────┤
│  Backend (Laravel)                                  │
│  ├── API банков и ставок (GET /api/v1/banks)        │
│  ├── API приёма лидов (POST /api/v1/leads)          │
│  ├── Интеграции CRM (Bitrix24, Sheets)              │
│  ├── Email отправка (SMTP)                          │
│  └── Личный кабинет (Auth + Dashboard)              │
│                                                     │
│  База данных (MySQL)                                │
│  ├── clients (клиенты SaaS)                         │
│  ├── projects (проекты клиентов)                    │
│  ├── banks (банки и ставки)                         │
│  ├── leads (лиды с сайтов клиентов)                 │
│  └── settings (настройки)                           │
└─────────────────────────────────────────────────────┘
                      │
                      │ CORS-enabled API
                      ▼
┌─────────────────────────────────────────────────────┐
│         САЙТ КЛИЕНТА (любая CMS)                    │
├─────────────────────────────────────────────────────┤
│  JS-виджет калькулятора                             │
│  ├── Инициализация через data-атрибуты               │
│  ├── Получает данные банков с нашего API            │
│  ├── Рассчитывает платежи клиентской                │
│  ├── Отправляет лиды на наш сервер                  │
│  └── Адаптирован под архитектуру клиента            │
└─────────────────────────────────────────────────────┘
```

---

## 📊 Current Status

**Phase:** Этап 1 - Backend + Demo Widget  
**Current Task:** Готовимся к 1.1.1 - установка инструментов  
**Progress:** Session 002 завершена (создана структура документации)  
**Last Updated:** 28.01.2025 (вечер)  

**Recent Activity:**
- ✅ Session 002: Создана структура документации (CLAUDE.md, PROGRESS.md, README.md)
- ✅ Session 001: Планирование, ROADMAP v2.0

**Next Steps:**
- Установка инструментов (VS Code, Git, Laragon)
- Задача 1.1.1: Выбор и покупка домена  

---

## 📚 Key Documents

| Документ | Назначение |
|----------|------------|
| `ROADMAP.md` | 📋 Детальный план задач и сроков |
| `PROGRESS.md` | ✅ Трекер выполнения задач |
| `CHANGELOG.md` | 📝 История важных изменений |
| `/sessions/` | 📂 Заметки рабочих сессий |
| `/docs/` | 📚 Референсная документация (Inkost) |

---

## 💻 Development Environment

### Локальная разработка:
- **OS:** Windows / macOS / Linux
- **Local Server:** Laragon (Windows) / Valet (macOS) / Docker
- **Editor:** VS Code
- **AI Assistant:** Claude Code (в терминале VS Code)
- **Version Control:** Git + GitHub

### Требования:
- PHP 8.2+
- Composer
- Node.js 18+
- MySQL 8.0+

---

## 📁 Project Structure

```
mortgage-calc-saas/
├── app/                        # Laravel application
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── API/            # API endpoints
│   │   │   └── Dashboard/      # Admin panel
│   ├── Models/                 # Eloquent models
│   ├── Services/               # Business logic
│   │   ├── CRM/                # CRM integrations
│   │   ├── Email/              # Email service
│   │   └── Calculator/         # Calculation logic
│   └── ...
├── database/
│   ├── migrations/             # Database migrations
│   └── seeders/                # Test data
├── public/
│   ├── widget/                 # JS widget для клиентов
│   │   ├── mortgage-calc.js
│   │   └── mortgage-calc.css
│   └── ...
├── resources/
│   ├── views/                  # Blade templates
│   │   ├── dashboard/          # Admin panel views
│   │   ├── landing/            # Landing page
│   │   └── emails/             # Email templates
│   └── js/                     # Frontend JS
├── routes/
│   ├── api.php                 # API routes
│   ├── web.php                 # Web routes
│   └── ...
├── tests/                      # Tests
└── ...
```

---

## 🎨 Code Style & Conventions

### PHP (Laravel):
- PSR-12 standard
- Eloquent ORM для БД
- Form Request для валидации
- Service classes для бизнес-логики
- Resources для API responses

### JavaScript:
- ES6+ syntax
- Модульная структура
- JSDoc comments
- Async/await вместо callbacks

### Database:
- Snake_case для таблиц и колонок
- Миграции для всех изменений БД
- Foreign keys с каскадным удалением
- Индексы на часто используемые поля

### Git Commits:
```
[Тип] Краткое описание

Примеры:
[Feature] Add banks API endpoint
[Fix] Resolve CORS issue in widget
[Refactor] Extract CRM integration to service
[Docs] Update PROGRESS.md
```

---

## 🔧 Development Rules

### 1. Работай локально
- ❌ НЕ делай изменения сразу на сервере
- ✅ Разрабатывай локально, тестируй, потом деплой

### 2. Тестируй каждый endpoint
- Создал API endpoint → протестируй в Postman/браузере
- Написал форму → заполни и отправь
- Добавил интеграцию → сделай тестовый запрос

### 3. Git workflow
```bash
# После каждой завершённой задачи:
git add .
git commit -m "[Feature] Task 1.2.3 - Description"
git push origin main
```

### 4. Обновляй документацию
- Завершил задачу → отметь в `PROGRESS.md`
- Приняли решение → запиши в session note
- Изменили архитектуру → обнови `CLAUDE.md`

### 5. Безопасность
- ❌ Никогда не коммить `.env` файл
- ❌ Никогда не хардкодить API ключи
- ✅ Все секреты в `.env`
- ✅ Валидация всех входящих данных

---

## 🎯 Current Sprint Goals

**Week 1-3:** Этап 1 - Backend + Demo Widget

**This Week Focus:**
- [ ] Инфраструктура (домен, VPS, Git)
- [ ] Базовая структура Laravel
- [ ] API банков и ставок

**Next Week:**
- [ ] API приёма лидов
- [ ] Интеграции CRM
- [ ] JS-виджет

---

## 🚨 Known Issues & Blockers

_None at the moment_

---

## 💡 Important Context

### Inkost vs SaaS Product

- **dev.новыйгород21.рф** - сайт Инкост на WordPress (в разработке)
  - Калькулятор встроен в тему
  - Полигон для тестирования идей
  - НЕ выделяем в плагин
  
- **Новый SaaS проект** - универсальное решение
  - Backend на Laravel
  - JS-виджет для любой CMS
  - Для всех клиентов

**Код Инкост** используем как **reference**, но **не переносим напрямую**.

### Обязательное условие для клиентов

Цена квартиры должна быть **в данных сайта** (технически):
- Открытая: показывается всем
- Скрытая: `data-price="5500000"` (hidden)
- По запросу: тоже hidden, но пишется "По запросу"

Пользователь **НЕ вводит цену вручную**. Виджет берёт из data-атрибутов.

---

## 🔗 Useful Links

- **ROADMAP:** См. `ROADMAP.md`
- **Progress:** См. `PROGRESS.md`
- **Inkost Docs:** `/docs/ПОЛНАЯ_ДОКУМЕНТАЦИЯ_КАЛЬКУЛЯТОР.md`
- **Laravel Docs:** https://laravel.com/docs/11.x
- **API Testing:** Postman / Insomnia

---

## 📞 Support & Questions

**Developer:** Евгений Петров  
**AI Assistants:** Claude (chat) + Claude Code (VS Code)  

**Workflow:**
- Claude Code → пишет код и выполняет команды
- Claude Chat → планирование, архитектура, сложные проблемы

---

**Last Updated:** 28.01.2025 (вечер)  
**Version:** 1.1
