<p align="center">
  <img src="screens/main-logo.svg" width="200" alt="STOQ" />
</p>

<p align="center">Умное управление рестораном — в одной системе.</p>

<p align="center">
  <a href="https://lyaguh.site">Веб-приложение</a> ·
  <a href="https://lyaguh.site/swagger/">API</a> ·
  <a href="https://github.com/MissClickRND/stoq/releases">Android и Desktop релизы</a>
  <a href="https://t.me/stoqhelperbot">Telegram-бот</a> ·
 <a href="STOQ.pptx">Презентация</a>
</p>

STOQ связывает работу с продуктами и работу с блюдами. Поставка пополняет складские партии, состав блюда определяет расход ингредиентов, а остатки влияют на доступность меню. Администратор видит статистику и действия сотрудников, кладовщик работает с поставками и инвентаризацией, официант — с заказами.

## Список участников и роли

<p align="center">
  <img src="screens/MissClickTeam.png" alt="Команда Miss Click" />
</p>

## Возможности

| Раздел            | Что можно сделать                                                                                           |
| ----------------- | ----------------------------------------------------------------------------------------------------------- |
| Склад             | Посмотреть остатки по продуктам и партиям, сроки годности, историю списаний; провести инвентаризацию        |
| Поставки          | Создать или изменить поставку, указать цены, количество и сроки годности; отследить приёмку и отмену        |
| Распознавание УПД | Загрузить изображение или PDF и получить данные для формы поставки; проверить их перед сохранением          |
| Блюда             | Настроить состав и цену, посмотреть себестоимость и продажи; определить доступность по ингредиентам         |
| Заказы            | Создать заказ, добавить блюда, указать стол и гостей; изменить статус и увидеть автора                      |
| Аналитика         | Посмотреть выручку, расчётную прибыль, средний чек, динамику заказов, дефицит продуктов и состав стоп-листа |
| Команда           | Подтвердить сотрудника, назначить роль, заблокировать доступ, создать или отозвать приглашение              |
| Журнал            | Посмотреть действия сотрудников и изменения склада: сначала новые события, затем история с подгрузкой       |
| Telegram          | Выбрать уведомления, получить сводку по запросу или включить ежедневную отправку                            |

Просроченные партии списываются автоматически и исчезают из основных остатков. Они остаются в отдельном списке до подтверждения утилизации; история складских движений сохраняется. Изменения склада и доступности блюд поступают клиентам через websockets

## Приложения и репозитории

| Репозиторий                                                    | Назначение                                                           | Основные технологии                                                         |
| -------------------------------------------------------------- | -------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| [stoq-frontend](https://github.com/MissClickRND/stoq-frontend) | Веб-интерфейс, гостевой заказ и приложение для Windows               | React, TypeScript, Vite, Mantine, Redux Toolkit / RTK Query, Electron       |
| [stoq-backend](https://github.com/MissClickRND/stoq-backend)   | API Gateway, бизнес-сервисы, распознавание документов и Telegram-бот | NestJS, TypeScript, PostgreSQL, Prisma, RabbitMQ, Redis                     |
| [stoq-mobile](https://github.com/MissClickRND/stoq-mobile)     | Нативное Android-приложение                                          | Kotlin, Jetpack Compose, Hilt, Retrofit, Coroutines / Flow, Room, DataStore |

```text
stoq/
├── stoq-frontend/    # Git submodule: веб и Windows
├── stoq-backend/     # Git submodule: сервер и фоновые сервисы
├── stoq-mobile/      # Git submodule: Android
├── screens/
│   ├── web/
│   └── mobile/
└── README.md
```

## Архитектура

<p align="center">
  <img src="screens/arch.png" width="800px" alt="STOQ" />
</p>

## Получение исходников

Нужен Git с поддержкой сабмодулей:

```bash
git clone --recurse-submodules https://github.com/MissClickRND/stoq.git
cd stoq
```

Если репозиторий уже клонирован без сабмодулей:

```bash
git submodule update --init --recursive
```

Сабмодуль хранит ссылку на конкретный коммит, а не автоматически меняющуюся «последнюю версию». Параметр `branch = main` задаёт ветку для явного обновления:

```bash
git submodule update --remote --merge
git add stoq-frontend stoq-backend stoq-mobile
git commit -m "chore: update application submodules"
```

После получения изменений корневого репозитория достаточно выполнить `git submodule update --init --recursive`, чтобы перейти именно к зафиксированным версиям. Изменения приложения коммитятся и публикуются в его собственном репозитории; затем обновляется ссылка в `stoq`.

## Скриншоты

### Веб-приложение

**Авторизация**

<p>
  <a href="screens/web/auth.png"><img src="screens/web/auth.png" width="49%" alt="Веб-приложение: Авторизация — auth" /></a>
  <a href="screens/web/auth2.png"><img src="screens/web/auth2.png" width="49%" alt="Веб-приложение: Авторизация — auth2" /></a>
</p>

<p>
  <a href="screens/web/auth3.png"><img src="screens/web/auth3.png" width="49%" alt="Веб-приложение: Авторизация — auth3" /></a>
</p>

**Аналитика и склад**

<p>
  <a href="screens/web/analytics.png"><img src="screens/web/analytics.png" width="49%" alt="Веб-приложение: Аналитика и склад — analytics" /></a>
  <a href="screens/web/product-exsist.png"><img src="screens/web/product-exsist.png" width="49%" alt="Веб-приложение: Аналитика и склад — product-exsist" /></a>
</p>

<p>
  <a href="screens/web/detailProduct.png"><img src="screens/web/detailProduct.png" width="49%" alt="Веб-приложение: Аналитика и склад — detailProduct" /></a>
  <a href="screens/web/inventory.png"><img src="screens/web/inventory.png" width="49%" alt="Веб-приложение: Аналитика и склад — inventory" /></a>
</p>

**Поставки**

<p>
  <a href="screens/web/supply.png"><img src="screens/web/supply.png" width="49%" alt="Веб-приложение: Поставки — supply" /></a>
  <a href="screens/web/createSupply.png"><img src="screens/web/createSupply.png" width="49%" alt="Веб-приложение: Поставки — createSupply" /></a>
</p>

<p>
  <a href="screens/web/detailSupply.png"><img src="screens/web/detailSupply.png" width="49%" alt="Веб-приложение: Поставки — detailSupply" /></a>
</p>

**Блюда и доступность меню**

<p>
  <a href="screens/web/dishes.png"><img src="screens/web/dishes.png" width="49%" alt="Веб-приложение: Блюда и доступность меню — dishes" /></a>
  <a href="screens/web/dish.png"><img src="screens/web/dish.png" width="49%" alt="Веб-приложение: Блюда и доступность меню — dish" /></a>
</p>

<p>
  <a href="screens/web/stoplist.png"><img src="screens/web/stoplist.png" width="49%" alt="Веб-приложение: Блюда и доступность меню — stoplist" /></a>
  <a href="screens/web/recommendation.png"><img src="screens/web/recommendation.png" width="49%" alt="Веб-приложение: Блюда и доступность меню — recommendation" /></a>
</p>

**Граф зависимостей**

<p>
  <a href="screens/web/graph1.png"><img src="screens/web/graph1.png" width="49%" alt="Веб-приложение: Граф зависимостей — graph1" /></a>
  <a href="screens/web/graph2.png"><img src="screens/web/graph2.png" width="49%" alt="Веб-приложение: Граф зависимостей — graph2" /></a>
</p>

**Заказы**

<p>
  <a href="screens/web/orders.png"><img src="screens/web/orders.png" width="49%" alt="Веб-приложение: Заказы — orders" /></a>
  <a href="screens/web/newOrder.png"><img src="screens/web/newOrder.png" width="49%" alt="Веб-приложение: Заказы — newOrder" /></a>
</p>

**Администрирование и журнал**

<p>
  <a href="screens/web/admin1.png"><img src="screens/web/admin1.png" width="49%" alt="Веб-приложение: Администрирование и журнал — admin1" /></a>
  <a href="screens/web/admin2.png"><img src="screens/web/admin2.png" width="49%" alt="Веб-приложение: Администрирование и журнал — admin2" /></a>
</p>

<p>
  <a href="screens/web/logs.png"><img src="screens/web/logs.png" width="49%" alt="Веб-приложение: Администрирование и журнал — logs" /></a>
</p>

### Android-приложение

**Аналитика**

<p>
  <a href="screens/mobile/01-dashboard.png"><img src="screens/mobile/01-dashboard.png" width="24%" alt="Android-приложение: Аналитика — 01-dashboard" /></a>
  <a href="screens/mobile/22-dashboard-metrics.png"><img src="screens/mobile/22-dashboard-metrics.png" width="24%" alt="Android-приложение: Аналитика — 22-dashboard-metrics" /></a>
  <a href="screens/mobile/23-dashboard-expiry.png"><img src="screens/mobile/23-dashboard-expiry.png" width="24%" alt="Android-приложение: Аналитика — 23-dashboard-expiry" /></a>
</p>

**Склад и инвентаризация**

<p>
  <a href="screens/mobile/02-inventory.png"><img src="screens/mobile/02-inventory.png" width="24%" alt="Android-приложение: Склад и инвентаризация — 02-inventory" /></a>
  <a href="screens/mobile/03-product-details.png"><img src="screens/mobile/03-product-details.png" width="24%" alt="Android-приложение: Склад и инвентаризация — 03-product-details" /></a>
  <a href="screens/mobile/04-add-product.png"><img src="screens/mobile/04-add-product.png" width="24%" alt="Android-приложение: Склад и инвентаризация — 04-add-product" /></a>
  <a href="screens/mobile/05-inventory-check.png"><img src="screens/mobile/05-inventory-check.png" width="24%" alt="Android-приложение: Склад и инвентаризация — 05-inventory-check" /></a>
</p>

<p>
  <a href="screens/mobile/24-inventory-list.png"><img src="screens/mobile/24-inventory-list.png" width="24%" alt="Android-приложение: Склад и инвентаризация — 24-inventory-list" /></a>
</p>

**Поставки и распознавание УПД**

<p>
  <a href="screens/mobile/06-supplies.png"><img src="screens/mobile/06-supplies.png" width="24%" alt="Android-приложение: Поставки и распознавание УПД — 06-supplies" /></a>
  <a href="screens/mobile/07-supply-details.png"><img src="screens/mobile/07-supply-details.png" width="24%" alt="Android-приложение: Поставки и распознавание УПД — 07-supply-details" /></a>
  <a href="screens/mobile/08-supply-drafts.png"><img src="screens/mobile/08-supply-drafts.png" width="24%" alt="Android-приложение: Поставки и распознавание УПД — 08-supply-drafts" /></a>
  <a href="screens/mobile/25-supply-scan.png"><img src="screens/mobile/25-supply-scan.png" width="24%" alt="Android-приложение: Поставки и распознавание УПД — 25-supply-scan" /></a>
</p>

<p>
  <a href="screens/mobile/26-new-supply.png"><img src="screens/mobile/26-new-supply.png" width="24%" alt="Android-приложение: Поставки и распознавание УПД — 26-new-supply" /></a>
</p>

**Заказы**

<p>
  <a href="screens/mobile/09-orders.png"><img src="screens/mobile/09-orders.png" width="24%" alt="Android-приложение: Заказы — 09-orders" /></a>
  <a href="screens/mobile/10-order-details.png"><img src="screens/mobile/10-order-details.png" width="24%" alt="Android-приложение: Заказы — 10-order-details" /></a>
  <a href="screens/mobile/11-new-order.png"><img src="screens/mobile/11-new-order.png" width="24%" alt="Android-приложение: Заказы — 11-new-order" /></a>
  <a href="screens/mobile/27-order-drafts.png"><img src="screens/mobile/27-order-drafts.png" width="24%" alt="Android-приложение: Заказы — 27-order-drafts" /></a>
</p>

<p>
  <a href="screens/mobile/28-order-dish-picker.png"><img src="screens/mobile/28-order-dish-picker.png" width="24%" alt="Android-приложение: Заказы — 28-order-dish-picker" /></a>
</p>

**Блюда и доступность меню**

<p>
  <a href="screens/mobile/12-dishes.png"><img src="screens/mobile/12-dishes.png" width="24%" alt="Android-приложение: Блюда и доступность меню — 12-dishes" /></a>
  <a href="screens/mobile/13-stop-list.png"><img src="screens/mobile/13-stop-list.png" width="24%" alt="Android-приложение: Блюда и доступность меню — 13-stop-list" /></a>
  <a href="screens/mobile/14-recommendations.png"><img src="screens/mobile/14-recommendations.png" width="24%" alt="Android-приложение: Блюда и доступность меню — 14-recommendations" /></a>
  <a href="screens/mobile/15-dish-details.png"><img src="screens/mobile/15-dish-details.png" width="24%" alt="Android-приложение: Блюда и доступность меню — 15-dish-details" /></a>
</p>

<p>
  <a href="screens/mobile/16-dish-ingredients.png"><img src="screens/mobile/16-dish-ingredients.png" width="24%" alt="Android-приложение: Блюда и доступность меню — 16-dish-ingredients" /></a>
  <a href="screens/mobile/17-add-dish.png"><img src="screens/mobile/17-add-dish.png" width="24%" alt="Android-приложение: Блюда и доступность меню — 17-add-dish" /></a>
</p>

**Заведение, команда и профиль**

<p>
  <a href="screens/mobile/18-admin-restaurant.png"><img src="screens/mobile/18-admin-restaurant.png" width="24%" alt="Android-приложение: Заведение, команда и профиль — 18-admin-restaurant" /></a>
  <a href="screens/mobile/19-admin-employees.png"><img src="screens/mobile/19-admin-employees.png" width="24%" alt="Android-приложение: Заведение, команда и профиль — 19-admin-employees" /></a>
  <a href="screens/mobile/20-admin-invitations.png"><img src="screens/mobile/20-admin-invitations.png" width="24%" alt="Android-приложение: Заведение, команда и профиль — 20-admin-invitations" /></a>
  <a href="screens/mobile/21-profile.png"><img src="screens/mobile/21-profile.png" width="24%" alt="Android-приложение: Заведение, команда и профиль — 21-profile" /></a>
</p>

**Вход и регистрация**

<p>
  <a href="screens/mobile/29-sign-in.png"><img src="screens/mobile/29-sign-in.png" width="24%" alt="Android-приложение: Вход и регистрация — 29-sign-in" /></a>
  <a href="screens/mobile/30-register-restaurant.png"><img src="screens/mobile/30-register-restaurant.png" width="24%" alt="Android-приложение: Вход и регистрация — 30-register-restaurant" /></a>
  <a href="screens/mobile/31-register-employee.png"><img src="screens/mobile/31-register-employee.png" width="24%" alt="Android-приложение: Вход и регистрация — 31-register-employee" /></a>
</p>

## Запуск

### Веб и Windows

Для frontend нужен Node.js 22.20+ и npm:

```bash
cd stoq-frontend
npm ci
```

Создайте `.env` по [примеру](stoq-frontend/.env.example). Для подключения к опубликованному backend:

```dotenv
API_PROXY_TARGET=https://lyaguh.site/api
VITE_API_URL=https://lyaguh.site/api
VITE_WEBSOCKET_API_URL=wss://lyaguh.site
```

В dev-режиме HTTP-запросы идут через `/api` и прокси Vite. `VITE_API_URL` используется в production-сборке. Для собственного backend замените адреса на его HTTP- и WebSocket-адреса.

```bash
npm run dev             # Веб-клиент
npm run desktop:dev     # Electron в режиме разработки
npm run build           # Веб-сборка в dist/
npm run desktop:build   # Установщик Windows x64 в release/
```

Windows-установщик собирается на Windows. На чистой машине Electron Builder может дополнительно загрузить инструменты упаковки.

### Backend

Зависимости устанавливаются отдельно в каталогах сервисов `stoq-backend/backend/`. Для полной системы нужны PostgreSQL, RabbitMQ, Redis и окружение каждого сервиса. Для распознавания нужен ключ OpenRouter, для бота — токен Telegram и ключ шифрования его сессий.

В корне backend находятся команды сборки и проверок; подробности подключения сервисов — в [документации backend](stoq-backend/README.md). Инструкция по совместному локальному запуску AI и Telegram — [LOCAL-SERVICES.md](stoq-backend/deploy/LOCAL-SERVICES.md).

Локальный supervisor использует заранее подготовленные SSH-ключ, настройки туннеля и env-файлы. Они не входят в репозиторий и не появляются после клонирования. Не подключайте новый экземпляр к рабочему окружению без этих настроек: конкурирующие процессы могут обрабатывать одни и те же команды или мешать Telegram long polling.

### Android

Откройте `stoq-mobile` в Android Studio. Проект использует JDK 17, Android SDK 36 и поддерживает Android 8.0+ (`minSdk 26`).

В `stoq-mobile/local.properties` укажите путь к Android SDK и адрес API с завершающим `/`:

```properties
sdk.dir=C:/Users/USERNAME/AppData/Local/Android/Sdk
BASE_API_URL=https://lyaguh.site/api/
```

Путь к SDK зависит от операционной системы. Затем можно запустить приложение из Android Studio или собрать debug APK:

```powershell
cd stoq-mobile
.\gradlew.bat assembleDebug
```

На macOS/Linux используйте `./gradlew assembleDebug`. APK появится в `app/build/outputs/apk/debug/`. Установка опубликованных версий описана в [мобильном репозитории](stoq-mobile/README.md#установка).

### Проверки

В корне frontend:

```bash
npm run typecheck
npm test
npm run build
```

В корне backend после установки зависимостей соответствующих сервисов:

```bash
npm run test:auth
npm run test:business
npm run test:ai
npm run test:telegram
```

Интеграционные проверки backend требуют отдельно настроенных тестовых БД и брокера. Для обычной работы клиентов прямой доступ к PostgreSQL не нужен — они обращаются к Gateway.
