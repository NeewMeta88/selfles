# selfles — Tilda code blocks

Этот репозиторий хранит HTML/CSS/JavaScript-код, вынесенный из HTML-кодовых блоков сайта **selfles** на Tilda.

Репозиторий нужен как читаемая и версионируемая копия кастомного кода сайта: здесь удобнее смотреть историю изменений, ревьюить код и передавать поддержку другому разработчику, чем работать только внутри редактора Tilda.

## Как связаны Tilda и файлы в репозитории

Каждый HTML-файл соответствует отдельному кодовому блоку в Tilda.

**Правило синхронизации:** название комментария/подписи у кодового блока в Tilda должно совпадать с именем файла **без `.html`**.

Пример:

- комментарий блока в Tilda: `sticky-menu`
- файл в репозитории: `main/sticky-menu.html`

Если файл переименовывается, комментарий соответствующего кодового блока в Tilda нужно переименовать одновременно.

> Порядок блоков в Tilda не кодируется номером файла. Источник истины для сопоставления — имя блока и имя файла.

## Структура

| Папка / файл | Страница / область Tilda | Назначение |
| --- | --- | --- |
| `main/` | Главная страница. В коде определяется как page id `94832776`, aliases `main` / `home` / `index` | Кодовые блоки главной страницы |
| `catalog/` | Каталог (`/catalog`, alias `catalog`) | Код каталога и карточек каталога |
| `catalog_footer/` | Общий footer/runtime каталога и товарных страниц | Общая логика доступности, маршрутизации, карточки товара и связанные товары |
| `footer/` | Общий Footer сайта | Глобальная логика, которая подключается через footer |
| `styles.css` | Общие стили | Общий CSS сайта, не привязанный к одному HTML-блоку |

### Что нужно подтвердить в Tilda перед публичной передачей

GitHub позволяет уверенно определить назначение `main/` и `catalog/` по runtime-проверкам URL/page id, но не хранит точные пользовательские названия служебных страниц в редакторе Tilda.

Перед окончательной передачей разработчику стоит сверить и при необходимости уточнить в этой таблице **точные названия страниц Tilda**, соответствующие `catalog_footer/` и `footer/`.

## Главная страница — `main/`

| Файл | Имя комментария блока в Tilda | Назначение |
| --- | --- | --- |
| `preset-product-mapping.html` | `preset-product-mapping` | Подключение маппинга товаров для готовых сетов / кнопок `js-set1`…`js-set4` |
| `sticky-menu.html` | `sticky-menu` | Фиксация меню и смена его состояния после скролла |
| `set-constructor-styles.html` | `set-constructor-styles` | Стили конструктора собственного сета |
| `set-constructor-part-1.html` | `set-constructor-part-1` | Данные и первая часть логики конструктора |
| `set-constructor-part-2.html` | `set-constructor-part-2` | Вторая часть логики конструктора |
| `zero-block-slider.html` | `zero-block-slider` | Слайдер Zero Block на базе Slick/VORON |
| `cart-icon.html` | `cart-icon` | Кастомная иконка корзины |
| `hover-fill-text.html` | `hover-fill-text` | Hover-анимация заполнения текста цветом |
| `preset-set-toast-styles.html` | `preset-set-toast-styles` | Стили toast-уведомлений для готовых сетов |
| `preset-set-cart-handler.html` | `preset-set-cart-handler` | Добавление готовых сетов в корзину и показ уведомления |
| `floating-button-before-footer.html` | `floating-button-before-footer` | Фиксированная кнопка, скрывающаяся при появлении footer |
| `main-catalog-rows.html` | `main-catalog-rows` | Логика товарных рядов / навигации каталога на главной |

### Важный порядок конструктора

`set-constructor-part-1.html` должен находиться **выше** `set-constructor-part-2.html`: вторая часть использует данные, опубликованные первой через `window.SELFLES_CONSTRUCTOR_SHARED`.

## Каталог — `catalog/`

| Файл | Имя комментария блока в Tilda | Назначение |
| --- | --- | --- |
| `catalog-sticky-menu.html` | `catalog-sticky-menu` | Фиксированное меню каталога |
| `catalog-product-runtime.html` | `catalog-product-runtime` | Runtime каталога/товарных карточек: нормализация названий, SKU и опций |
| `disable-sold-out-cards.html` | `disable-sold-out-cards` | Блокировка карточек недоступных товаров |
| `home-catalog-pager.html` | `home-catalog-pager` | Навигация по товарным рядам главной страницы; исторически лежит в `catalog/` |

### Потенциальный legacy-дубликат

`catalog/home-catalog-pager.html` и `main/main-catalog-rows.html` оба содержат логику товарных рядов на главной странице, но являются разными версиями реализации.

Перед удалением одного из них нужно открыть Tilda и проверить, **какой именно кодовый блок сейчас подключён/активен на опубликованной главной странице**. Пока это не подтверждено, оба файла следует сохранять.

## Catalog footer / product runtime — `catalog_footer/`

| Файл | Имя комментария блока в Tilda | Назначение |
| --- | --- | --- |
| `catalog-footer-runtime.html` | `catalog-footer-runtime` | Общий runtime товарной страницы и связанных товаров |
| `footer-catalog-availability-from-st315n.html` | `footer-catalog-availability-from-st315n` | Живой индекс наличия товаров из Tilda ST315N |
| `footer-product-record-flow-fix.html` | `footer-product-record-flow-fix` | Исправление flow/инициализации товарных record-блоков |
| `product-router.html` | `product-router` | Маршрутизация и инициализация товарных страниц |
| `product-title-cleaner.html` | `product-title-cleaner` | Нормализация/очистка названий товаров |
| `products-manifest.html` | `products-manifest` | Манифест данных товаров / fallback-данные |

## Общий Footer — `footer/`

| Файл | Имя комментария блока в Tilda | Назначение |
| --- | --- | --- |
| `cart-name-sync.html` | `cart-name-sync` | Синхронизация названий товаров в корзине |
| `global-product-title-and-router.html` | `global-product-title-and-router` | Глобальная логика названий товаров и маршрутизации |
| `hover-links.html` | `hover-links` | Общие hover-эффекты ссылок |

## Как вносить изменения

1. Найти кодовый блок в нужной странице Tilda по комментарию блока.
2. Найти одноимённый `.html`-файл в соответствующей папке репозитория.
3. Вносить изменение в одной версии кода и полностью синхронизировать вторую.
4. Если меняется имя файла — одновременно изменить комментарий блока в Tilda.
5. Для split-блоков (`set-constructor-part-1` / `set-constructor-part-2`) сохранять порядок подключения.
6. После синхронизации опубликовать страницу Tilda и проверить страницу в браузере.

Рекомендуется делать изменения через отдельную git-ветку и Pull Request, особенно если код меняет корзину, каталог, наличие товаров или товарные страницы.

## Перед переводом репозитория в public

Перед открытием репозитория рекомендуется:

- подтвердить точные названия страниц `catalog_footer` и `footer` в редакторе Tilda и при необходимости поправить таблицу выше;
- проверить в Tilda, какой из блоков `home-catalog-pager` / `main-catalog-rows` реально используется;
- проверить внешние зависимости и ссылки на сторонние хостинги, особенно старые подключения `disk.nocodered.ru`;
- убедиться, что статические fallback-данные товаров не воспринимаются как актуальный источник наличия;
- повторно проверить историю репозитория на секреты перед публикацией;
- выбрать и добавить `LICENSE`, если код предполагается разрешать использовать третьим лицам. Публичный репозиторий сам по себе не задаёт лицензию на использование кода.

## Старые имена файлов

Для истории и поиска по старым обсуждениям:

| Старое имя | Новое имя |
| --- | --- |
| `main/1.html` | `main/preset-product-mapping.html` |
| `main/2.html` | `main/sticky-menu.html` |
| `main/3.html` | `main/set-constructor-styles.html` |
| `main/4-constructor-part-1.html` | `main/set-constructor-part-1.html` |
| `main/4-constructor-part-2.html` | `main/set-constructor-part-2.html` |
| `main/5.html` | `main/zero-block-slider.html` |
| `main/6.html` | `main/cart-icon.html` |
| `main/7.html` | `main/hover-fill-text.html` |
| `main/8.html` | `main/preset-set-toast-styles.html` |
| `main/9.html` | `main/preset-set-cart-handler.html` |
| `main/10.html` | `main/floating-button-before-footer.html` |
| `main/11.html` | `main/main-catalog-rows.html` |
| `catalog/catalog.html` | `catalog/catalog-product-runtime.html` |
| `catalog_footer/catalog-page.html` | `catalog_footer/catalog-footer-runtime.html` |
