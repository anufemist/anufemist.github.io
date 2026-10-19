# aXperience Design System — Variant 70's

Руководство по структуре проекта, компонентам, Sass/CSS API и JavaScript-поведению. Документация описывает исходники в `styles/src/` и `js/app.js`; `styles/style.css` — сгенерированный результат сборки, его следует обновлять через Sass, а не редактировать вручную.

## 1. Запуск и структура

Откройте `index.html` в браузере или запустите локальный статический сервер из корня проекта. Ссылки и ресурсы в HTML локальные; Google Fonts используются как внешний шрифт при наличии сети, с резервом на системные шрифты.

```powershell
npm install
npm run build       # сборка CSS
npm run watch:css   # пересборка CSS при изменении Sass
```

| Путь | Назначение |
|---|---|
| `index.html` | Интро, обзор компонентов и ссылок на примеры |
| `pages/base.html` | Палитра, типографика, отступы, границы, текстовые блоки |
| `pages/data-entry.html` | Кнопки и элементы ввода |
| `pages/data-display.html` | Навигация, таблицы, пагинация, карточки |
| `pages/notification.html` | Сообщения, всплывающие подсказки, диалоги и toast |
| `pages/grid.html` | Документация адаптивной сетки |
| `pages/login.html`, `pages/register.html` | Формы авторизации и регистрации |
| `pages/profile.html`, `pages/settings.html` | Примеры профиля и настроек |
| `pages/crud-list.html` | Табличный CRUD со строкой поиска и фильтрами |
| `pages/crud-list-modal.html` | CRUD-список с редактированием в диалоге |
| `pages/crud-create.html` | Форма создания/обновления записи |
| `styles/src/main.scss` | Sass entry point |
| `styles/src/_tokens.scss` | Палитра, темы и Sass-токены |
| `styles/src/_grid.scss` | Сетка и её breakpoint-классы |
| `styles/src/styles.scss` | Базовая тема и библиотека компонентов |
| `styles/src/pages.scss` | Стили страниц-примеров и сетки |
| `styles/src/_atoms.scss` | Дополнительные атомарные компоненты |
| `styles/src/_crud.scss` | Стили CRUD и профиля |
| `js/app.js` | Поведение интерактивных примеров |

Все страницы библиотеки подключают `../styles/style.css` и `../js/app.js`; корневой обзор использует `styles/style.css` и `js/app.js`. Тему страницы задаёт checkbox `#theme-toggle`, расположенный перед тематическим контейнером.

## 2. Страницы и наборы элементов

| Страница | Секции/элементы |
|---|---|
| `base.html` | `#colors` — семейства цветов и палитра; `#typography` — шкала текста; `#layout` — отступы, границы и разделители; `#text-blocks` — пять примеров контента |
| `data-entry.html` | `#buttons`, `#controls`, `#text-fields`, `#textareas`, `#selects`, `#choices`, `#steps`, `#rating`; также демонстрации компонентов в цветовых семействах |
| `data-display.html` | `#navigation` — навигация, `#tables` — таблицы, `#pagination` — пагинация, `#interactive` — аккордеоны и загрузка, `#cards` — карточки, `#badges` — статусы, `#sortable-table` — сортировка |
| `notification.html` | `#feedback` — сообщения, `#popups` — диалог и popover, `#tooltips` — подсказки, `#toast-examples` — уведомления, `#popup-types` — варианты диалогов |
| `grid.html` | 12-колоночная сетка, breakpoint-таблица, демонстрации `grid-col-*` |
| `login.html`, `register.html` | Компактные формы аутентификации; пароль можно показать или скрыть |
| `profile.html` | Карточка профиля, статистика и детали пользователя |
| `settings.html` | Навигация вкладками и настройки формы |
| `crud-list.html`, `crud-list-modal.html` | Таблица коллекций, фильтры, действия строки и диалоги |
| `crud-create.html` | Вкладки формы, поля модели и блок сохранения/метаданных |

### Базовые классы элементов

Применяйте классы как композиционные блоки. Не заменяйте ими семантические HTML-теги: кнопки должны оставаться `<button>`, ссылки — `<a>`, поля — `<input>`, `<select>` или `<textarea>`.

| Назначение | Классы и варианты |
|---|---|
| Оболочка библиотеки | `.app-shell`, `.sidebar`, `.brand`, `.brand-mark`, `.brand-caption`, `.side-nav`, `.side-link`, `.sidebar-label`, `.sidebar-note`, `.main-content`, `.topbar`, `.page-wrap`, `.footer` |
| Заголовки/секции | `.intro`, `.intro-copy`, `.intro-art`, `.eyebrow`, `.eyebrow-line`, `.kit-section`, `.section-heading`, `.section-description`, `.component-label` |
| Палитра | `.palette-card`, `.palette-title`, `.swatch-row`, `.swatch`, `.usage-grid`, `.usage-item`, `.usage-page`, `.usage-surface`, `.usage-text`, `.usage-accent`, `.usage-danger`, `.usage-debug`, `.usage-warning`, `.usage-success`, `.usage-tip`, `.usage-info`, `.usage-stunt`, `.usage-harmony` |
| Типографика/контент | `.type-card`, `.type-row`, `.type-meta`, `.type-sample`, `.type-h1`–`.type-h6`, `.type-body`, `.type-small`, `.type-tiny`, `.copy-block`, `.copy-block-featured`, `.copy-list`, `.copy-quote`, `.inline-copy-link` |
| Карточки/контейнеры | `.component-card`, `.example-card`, `.example-cards`, `.feature-card`, `.quote-card`, `.stat-card`, `.layout-card`, `.family-showcase`, `.family-demo` |
| Кнопки | `.btn` плюс `.btn-primary`, `.btn-accent`, `.btn-info`, `.btn-success`, `.btn-warning`, `.btn-danger`, `.btn-red`, `.btn-orange`, `.btn-yellow`, `.btn-green`, `.btn-teal`, `.btn-blue`, `.btn-purple`, `.btn-pink`; `.btn-quiet` — малозаметное действие, `.btn-solid` — залитая кнопка |
| Поля/выбор | `.form-grid`, `.field`, `.input-wrap`, `.input-wrap-end`, `.input-clear-wrap`, `.input-clear`, `.input-error`, `.field-error`, `.choice-group`, `.choice`, `.custom-check`, `.custom-radio`, `.switch-choice`, `.toggle-track`, `.stepper`, `.range-tooltip`, `.rating-example`, `.rating-stars` |
| Навигация | `.breadcrumbs`, `.tabs`, `.tab`, `.tab-count`, `.tab-panels`, `.tab-panel`, `.pagination`, `.pagination-button`, `.pagination-ellipsis`, `.pagination-status` |
| Данные/статусы | `.data-table`, `.table-card`, `.table-title`, `.action-table`, `.plain-table`, `.hover-table`, `.selectable-table`, `.table-row-select`, `.crud-table`, `.table-action`, `.badge`, `.badge-neutral`, `.badge-accent`, `.badge-info`, `.badge-success`, `.badge-warning`, `.badge-danger`, `.count-badge`, `.status-chip`, `.status-red`, `.status-orange`, `.status-yellow`, `.status-green`, `.status-teal`, `.status-blue`, `.status-purple`, `.status-pink` |
| Загрузка | `.progress-item`, `.progress-caption`, `.progress-track`, `.progress-green`, `.progress-indeterminate`, `.spinner`, `.spinner-inline`, `.spinner-sm`, `.spinner-lg`, `.spinner-label` |
| Оповещения | `.alert`, `.alert-info`, `.alert-success`, `.alert-warning`, `.alert-danger`, `.alert-purple`, `.alert-pink`, `.alert-icon`, `.banner`, `.banner-info`, `.banner-accent`, `.banner-close`, `.toast-region`, `.toast-message`, `.toast-action` |
| Popover/dialog | `.has-tooltip` + `data-tooltip`, `.popover-content`, `.demo-dialog`, `.dialog-actions`, `.dialog-close`, `.dialog-mark`, `.edit-dialog`, `.delete-dialog` |
| Примеры страниц | `.sample-app-shell`, `.sample-topbar`, `.sample-brand`, `.sample-page-nav`, `.sample-content`, `.sample-heading`, `.sample-card`, `.sample-breadcrumbs`, `.sample-footer`, `.auth-page`, `.auth-card`, `.auth-form`, `.auth-password`, `.password-toggle`, `.profile-layout`, `.profile-summary`, `.profile-details`, `.settings-layout`, `.settings-tabs`, `.settings-panel` |
| CRUD | `.crud-layout`, `.crud-main`, `.crud-toolbar`, `.crud-page-size`, `.crud-table-tools`, `.crud-filters`, `.crud-filter-group`, `.crud-create-layout`, `.crud-form-tabs`, `.crud-create-aside`, `.crud-create-actions`, `.crud-record-meta`, `.crud-edit-form` |
| Сетка | `.grid-container`, `.grid-row`, `.grid-col`, `.grid-col-N`, `.grid-col-{sm,md,lg,xl}-N` |
| Вспомогательные классы | `.active`, `.selected`, `.last-section`, `.border-list`, `.border-sample`, `.border-strong`, `.border-subtle`, `.spacing-list`, `.spacing-item`, `.space-1`, `.space-2`, `.space-3`, `.space-4`, `.space-6`, `.space-8`, `.color-chip`, `.inline-hint`, `.required-mark`, `.form-field-wide` |
| Детали карточек и примеров | `.card-art`, `.card-art-label`, `.card-content`, `.card-sun`, `.quote-mark`, `.quote-credit`, `.quote-decoration`, `.stat-icon`, `.stat-number`, `.stat-footer`, `.tag`, `.author-avatar`, `.activity-icon`, `.activity-blue`, `.activity-yellow`, `.mini-avatar`, `.avatar-anna`, `.avatar-ilya`, `.avatar-maria`, `.person-cell`, `.table-swatches`, `.table-swatches-blue`, `.table-swatches-green` |
| Раскрываемый контент и состояния | `.accordion-list`, `.accordion-item`, `.accordion-chevron`, `.progress-green`, `.progress-indeterminate`, `.status-dot`, `.status-away`, `.count-accent`, `.count-muted`, `.icon-count`, `.is-selected`, `.is-half`, `.is-disabled` |
| Цветовые демонстрации | `.family-section`, `.family-showcase`, `.family-demo`, `.family-demo-items`, `.family-button`, `.family-group-button`, `.family-badge`, `.family-switch`, `.family-progress`, `.family-spinner`, `.family-count-badge`, `.family-accordion`, `.family-alert`, `.family-message-card`, `.family-message-items`, `.family-popup`, `.family-tip`, `.family-tip-anchor`, `.family-tabs`, `.family-crumbs`, `.family-pagination`, `.family-table-row`, `.family-view-items` |
| Внутренние блоки компонентов | `.layout-column`, `.control-examples`, `.interactive-card`, `.interactive-demo`, `.popup-actions`, `.popup-anchor`, `.table-examples`, `.table-scroll`, `.palette-foot`, `.palette-spacer`, `.alert-list`, `.banner-mark`, `.spinner-examples`, `.tooltip-demo`, `.tooltip-examples`, `.toast-examples` |
| Auth/profile/settings | `.auth-brand`, `.auth-wrap`, `.auth-description`, `.auth-extras`, `.auth-switch`, `.auth-terms`, `.auth-footer`, `.auth-submit`, `.profile-avatar`, `.profile-stats`, `.profile-stat`, `.profile-bio`, `.profile-actions`, `.profile-link`, `.profile-collections`, `.detail-list`, `.settings-options`, `.settings-option`, `.status-bar`, `.status-information`, `.status-actions`, `.list-pagination`, `.delete-action`, `.model-form-card`, `.model-form-section`, `.model-options`, `.field-help` |
| Страница сетки | `.grid-doc-content`, `.grid-reference`, `.grid-doc-card`, `.grid-doc-card-heading`, `.grid-doc-demo`, `.grid-demo-cell`, `.grid-demo-cell-featured`, `.grid-table-wrap`, `.grid-breakpoint-table`, `.grid-class-list`, `.grid-code` |

`N` в классах колонок — целое число от 1 до 12. Для включения адаптивной раскладки добавьте несколько классов, например `grid-col-12 grid-col-md-6 grid-col-lg-4`.

## 3. Как использовать компоненты

### Кнопки и группы

`.btn` задаёт общий контурный вид, размеры, focus-ring и отклик на нажатие. Добавьте ровно один вариант цвета. Используйте любой из трёх HTML-носителей: `<a class="btn …">`, `<button class="btn …" type="button">` или `<input class="btn …" type="submit">`. Для группы используйте контейнер `.button-group[aria-label="Выбор периода"]` и дочерние `.group-button`; атрибуты `aria-pressed` и класс `.active` отражают выбранный элемент.

```html
<button class="btn btn-accent" type="button">Сохранить</button>
<div class="button-group" role="group" aria-label="Выбор периода">
  <button class="group-button active" type="button" aria-pressed="true">Неделя</button>
  <button class="group-button" type="button" aria-pressed="false">Месяц</button>
</div>
```

### Формы и валидация

Поместите поле в `<label class="field">`: первый дочерний элемент — видимая подпись, далее native input/select/textarea. Для двух колонок используйте `.form-grid`; на узком экране сетка становится одноколоночной. HTML-атрибуты `required`, `disabled`, `placeholder`, `min`, `max`, `step` сохраняют нативную семантику и валидацию. Класс `.input-error` и `.field-error` показывают пример ошибки, но сами по себе не выполняют проверку.

- Иконка в начале: `.input-wrap` вокруг `svg` и input.
- Иконка справа: `.input-wrap.input-wrap-end`.
- Кнопка очистки: `.input-clear-wrap` и соседняя кнопка `[data-clear-input]`; контейнер должен включать input или textarea.
- Чекбокс/радио: `.choice` оборачивает input и `.custom-check` или `.custom-radio`; общее название группы поместите в `<fieldset class="choice-group"><legend>…</legend>`.
- Шаговый счётчик: `.stepper[data-stepper]` содержит числовой input и кнопки `[data-step="-1"]` / `[data-step="1"]`; для корректного нижнего ограничения задайте `min` и `step`.
- Слайдер: range input с `data-range-output="ID"` обновляет элемент с таким `id`.
- Рейтинг: см. контракт `data-rating` в разделе JavaScript.
- Несколько вариантов select на странице — native `<select>`; отдельные состояния загрузки/множественного выбора стилизованы как демонстрационные примеры, внешняя библиотека select не подключена.

### Таблицы, статусы и загрузка

- `.data-table` — таблица; `.action-table` добавляет первую колонку действий; `.plain-table` не требует `<thead>`; `.hover-table` подсвечивает строки.
- Для выбора строк добавьте `.selectable-table` и `.table-row-select` checkbox внутрь каждой строки.
- Для сортировки используйте `.crud-table` и кнопки `[data-sort-key]` в заголовках. `data-sort-key` — индекс столбца с нуля.
- `.badge` и `.status-chip` получают семантическую вариацию дополнительным классом из соответствующего семейства.
- `.progress-track > span` заполняется шириной (например, `style="width:60%"`). Для неопределённой загрузки используйте `.progress-indeterminate`.
- `.spinner`, `.spinner-sm`, `.spinner-lg`, `.spinner-inline` — варианты индикатора загрузки.
- Для списка страниц оставьте `.pagination` пустым: JavaScript создаст элементы управления (демо на 8 страниц). Вариант с подписью «Показано … из …» оформляется через `.table-pagination`.

### Сообщения и всплывающие окна

- `.alert` — закрываемое сообщение; цветовые классы задают тон. Кнопка внутри `.alert` удаляет сообщение.
- `.banner` — широкое сообщение; `.banner-close` закрывает его.
- `[data-toast]` на кнопке создаёт toast; необязательные `data-toast-action`, `data-toast-link`, `data-toast-icon` добавляют действие, переход или символ. Toast автоматически исчезает через 4 секунды.
- `.has-tooltip[data-tooltip]` показывает текст при наведении или клавиатурном фокусе.
- Для нативного popover укажите кнопке `data-open-popover="ID"` и этому элементу — `id="ID" popover`. Кнопка открывает/закрывает подсказку и задаёт её позицию рядом с триггером.
- Для `<dialog>` без цели используется первый `.demo-dialog`. Чтобы выбрать конкретное окно, укажите `data-dialog-target="ID"` на триггере. Внутри диалога `[data-close-dialog]` закрывает окно, `[data-confirm-dialog]` закрывает его и выводит toast. Клик по фону диалога тоже закрывает его.

### Страницы-примеры и CRUD

`pages/login.html` и `pages/register.html` используют `.auth-page`, `.auth-wrap`, `.auth-card`, `.auth-form`. Для кнопки показа пароля используйте `data-password-toggle="password-input-id"`. Формы с `[data-demo-form]` проходят `reportValidity()`, не отправляются на сервер, показывают toast и закрывают родительский диалог; текст успеха можно задать через `data-success-message`.

На CRUD-страницах:

- `[data-filter-table="table-id"]` ищет подстроку в текстовом содержимом строк таблицы; соответствующая кнопка очистки — `[data-clear-filter="table-id"]`.
- `[data-filter-search]` фильтрует видимость `.crud-filter-group` по тексту группы.
- `[data-filter-value]` на чекбоксах и кнопки `[data-apply-filters]` / `[data-reset-filters]` управляют фильтрами таблицы `#collections-table`.
- `[data-copy-row]` копирует значения ячеек строки, пропуская первую колонку действий.
- `[data-delete-dialog]` сохраняет строку `[data-model-row]` для удаления; `[data-confirm-delete]` удаляет её и показывает toast.
- `[data-edit-modal]` открывает `.edit-dialog` и подставляет имя из второй ячейки строки в `input[name="name"]`.
- `pages/crud-create.html?id=…` переключает форму из режима создания в демонстрационный режим редактирования.

Все CRUD-действия — клиентские демонстрации: данные не сохраняются в базе и не отправляются на сервер.

## 4. Темы, CSS-переменные и Sass

### Переменные цвета

Палитра задаётся в `:root` файла `_tokens.scss`. Используйте токены вместо захардкоженных hex-значений:

| Семейство | Доступные токены |
|---|---|
| Нейтральные | `--neutral-50`, `--neutral-100`, `--neutral-200`, `--neutral-300`, `--neutral-400`, `--neutral-600`, `--neutral-700`, `--neutral-800`, `--neutral-900` |
| Красные | `--red-50`, `--red-100`, `--red-200`, `--red-300`, `--red-400`, `--red-500`, `--red-600`, `--red-700`, `--red-900` |
| Оранжевые | `--orange-50`, `--orange-100`, `--orange-200`, `--orange-300`, `--orange-400`, `--orange-600`, `--orange-700` |
| Жёлтые | `--yellow-50`, `--yellow-100`, `--yellow-200`, `--yellow-400`, `--yellow-600`, `--yellow-700`, `--yellow-900` |
| Зелёные | `--green-50`, `--green-100`, `--green-200`, `--green-500`, `--green-600`, `--green-700`, `--green-900` |
| Бирюзовые | `--teal-50`, `--teal-100`, `--teal-200`, `--teal-300`, `--teal-400`, `--teal-600`, `--teal-700` |
| Синие | `--blue-50`, `--blue-100`, `--blue-200`, `--blue-500`, `--blue-600`, `--blue-700`, `--blue-900` |
| Фиолетовые | `--purple-50`, `--purple-100`, `--purple-200`, `--purple-300`, `--purple-400`, `--purple-600`, `--purple-700` |
| Розовые | `--pink-50`, `--pink-100`, `--pink-200`, `--pink-300`, `--pink-400`, `--pink-600`, `--pink-700` |

Шкалы намеренно не содержат все возможные номера. Используйте только перечисленные оттенки.

### Семантические CSS-переменные

`.app-shell`, `.sample-app-shell` и `.auth-page` задают тему через переменные. Набор основного интерфейса: `--page` (фон страницы), `--surface` (поверхность карточки), `--surface-raised` (поднятая поверхность), `--text`, `--muted`, `--line`, `--field`, `--accent`. В тёмной теме checkbox `#theme-toggle:checked` меняет значения переменных автоматически.

Роли палитры для демонстрации: `--role-page`, `--role-surface`, `--role-text`, `--role-accent`, `--role-danger`, `--role-debug`, `--role-warning`, `--role-success`, `--role-tip`, `--role-info`, `--role-stunt`, `--role-harmony`. Для пользовательского цветового образца `.family-demo` использует `--family` (основной цвет) и `--family-soft` (мягкий фон). Переменные декора цветка: `--petal-color`, `--petal-angle`. Остальные runtime-токены: `--grid-gutter`, `--role-color`.

```css
.my-panel {
  background: var(--surface);
  border: 1px solid var(--line);
  color: var(--text);
}
```

### Sass-переменные и media queries

- `$flat-radius: 2px` — общий радиус интерфейса, встроен в базовые стили.
- `$control-radius: 10px` — скругление переключателя темы.
- `$grid-columns: 12` и `$grid-breakpoints`: `sm` 576px, `md` 768px, `lg` 992px, `xl` 1200px.
- Основная оболочка: брейкпоинты 1050px, 760px и 560px; вспомогательные компоненты/CRUD используют 980px, 760px, 600px, 575px и 540px в зависимости от компонента.
- `prefers-reduced-motion: reduce` сокращает CSS-переходы и отключает плавную прокрутку.

Не используйте старые радиусы `radius-sm`/`radius-md`: текущий базовый стиль — flat, с единственным общим `$flat-radius`.

### Полный перечень CSS-свойств, используемых исходниками

Ниже приведены имена декларативных CSS-свойств из `styles/src/*.scss`. Это справочник реализации, а не список обязательных свойств для каждого компонента. Значения и селекторы компонентов находятся в Sass-файлах выше.

| Группа | Свойства |
|---|---|
| Раскладка и позиционирование | `display`, `position`, `inset`, `top`, `right`, `bottom`, `left`, `z-index`, `width`, `min-width`, `max-width`, `height`, `min-height`, `max-height`, `aspect-ratio`, `overflow`, `overflow-x`, `overflow-y`, `pointer-events`, `vertical-align` |
| Flex и Grid | `flex`, `flex-basis`, `flex-direction`, `flex-wrap`, `align-content`, `align-items`, `align-self`, `justify-content`, `justify-items`, `justify-self`, `place-items`, `gap`, `grid-column`, `grid-row`, `grid-template-columns` |
| Размеры и границы | `box-sizing`, `margin`, `margin-top`, `margin-right`, `margin-bottom`, `margin-left`, `margin-inline`, `padding`, `padding-top`, `padding-right`, `padding-bottom`, `padding-left`, `border`, `border-top`, `border-right`, `border-bottom`, `border-left`, `border-width`, `border-style`, `border-color`, `border-top-color`, `border-collapse`, `border-radius`, `outline`, `outline-offset`, `box-shadow` |
| Фон и цвет | `color`, `background`, `background-color`, `background-image`, `background-position`, `background-size`, `background-clip`, `accent-color`, `opacity`, `fill`, `stroke`, `stroke-width`, `stroke-linecap`, `filter`, `backdrop-filter` |
| Текст и шрифты | `font`, `font-family`, `font-size`, `font-weight`, `font-synthesis`, `line-height`, `letter-spacing`, `text-align`, `text-decoration`, `text-overflow`, `text-rendering`, `text-transform`, `text-underline-offset`, `white-space`, `list-style` |
| Движение и интерактивность | `animation`, `transition`, `transition-duration`, `transform`, `transform-origin`, `cursor`, `resize`, `content`, `clip`, `clip-path`, `scroll-behavior`, `scroll-margin-top`, `scroll-padding-top`, `scrollbar-color`, `scrollbar-width`, `-webkit-background-clip`, `-webkit-tap-highlight-color` |

В Sass также встречаются CSS custom properties (перечень выше), CSS-псевдоклассы (`:hover`, `:focus-visible`, `:disabled`, `:checked`, `[open]`) и at-rules (`@media`, `@keyframes`). Изменяйте исходник в подходящем partial и повторно запускайте `npm run build`.

## 5. JavaScript API

`js/app.js` загружается с `defer` и автоматически инициализирует компоненты, найденные на текущей странице. Большинство функций являются внутренними и вызываются при загрузке файла; вручную вызывать их из HTML не нужно.

### Функции

| Функция | Назначение |
|---|---|
| `initializeSidebarNavigation()` | Собирает библиотечную навигацию, список примеров и ссылки на секции текущей страницы; выставляет активную ссылку по имени файла |
| `initializePageSectionNavigation()` | Создаёт ссылки на `.kit-section[id]` по их заголовку `h2` |
| `initializeSidebar()` | Десктопное сворачивание панели, мобильное выдвижное меню, backdrop, Escape и aria-состояния |
| `initializeButtonGroups()` | Переключает `.active`/`aria-pressed` в группе «Выбор периода» |
| `initializePagination()` | Создаёт пагинацию с 8 демо-страницами, текущей страницей, многоточиями и переходом назад/вперёд |
| `initializeDialogs(showToast)` | Открывает/закрывает диалоги, обрабатывает подтверждение, редактирование и удаление CRUD-строки |
| `initializePopovers()` | Переключает нативный popover и позиционирует его около кнопки-триггера |
| `initializeMessages(showToast)` | Подключает кнопки toast и закрытие alert/banner |
| `activateTab(tab)` | Обновляет активную вкладку, `aria-selected`, `tabIndex` и связанные панели |
| `initializeTabs()` | Подключает мышь и клавиатуру (стрелки, Home, End) к `[role="tab"]` |
| `initializeDemoForms(showToast)` | Проверяет валидность демонстрационных форм, показывает toast и закрывает диалог без отправки данных |
| `initializeModelForm()` | При URL-параметре `?id=…` показывает пример режима редактирования коллекции |
| `initializePasswordToggles()` | Переключает `password`/`text` у поля, на которое указывает `data-password-toggle` |
| `copyText(value)` | Пытается использовать Clipboard API, при отказе вызывает резервное копирование |
| `copyTextFallback(value)` | Создаёт временное textarea и копирует значение через `document.execCommand("copy")` |
| `initializePaletteCopy(showToast)` | Делает образцы палитры доступными по клику/Enter/Space, копирует вычисленный цвет в HEX |
| `initializeRangeControls()` | Синхронизирует range с output и обрабатывает кнопки шагового счётчика |
| `initializeRatings()` | Обновляет выбранные звёзды, значение рейтинга и половинный шаг |
| `initializeInputClear()` | Очищает input/textarea, отправляет input event и возвращает фокус |
| `initializeTableRowSelection()` | Помечает строку `.is-selected` при выборе checkbox |
| `initializeCrud(showToast)` | Реализует поиск, фильтры, сортировку и копирование строки CRUD-таблицы |
| `showToast(message, options)` | Создаёт toast с необязательными `action`, `href`, `icon`; автоматически удаляет через 4 секунды |

### Data-атрибуты и структура для JavaScript

| Атрибут/селектор | Значение и ожидаемая структура |
|---|---|
| `[data-open-dialog]` | Кнопка открытия; без цели открывает `.demo-dialog` |
| `data-dialog-target="dialog-id"` | `id` диалога, который нужно открыть |
| `[data-close-dialog]`, `[data-confirm-dialog]` | Кнопки внутри `<dialog>` для закрытия/подтверждения |
| `[data-delete-dialog]`, `[data-confirm-delete]` | Кнопка удаления в строке `[data-model-row]` и кнопка подтверждения |
| `[data-edit-modal]` | Кнопка редактирования в строке `[data-model-row]`; имя записи ожидается во второй ячейке, внутри `<strong>` |
| `data-open-popover="popover-id"` | Кнопка, связанная с элементом `id="popover-id" popover` |
| `data-toast="Сообщение"` | Кнопка, вызывающая toast |
| `data-toast-action="Отменить"` | Добавляет к toast текстовую кнопку действия (сама по себе callback не выполняет) |
| `data-toast-link="path"` | Добавляет ссылку к toast; подпись задаёт `data-toast-action` |
| `data-toast-icon="✓"` | Символ слева в toast |
| `[data-demo-form]`, `data-success-message` | Форма с клиентской проверкой и необязательным текстом успеха |
| `data-password-toggle="input-id"` | Кнопка переключения видимости указанного поля пароля |
| `data-range-output="output-id"` | Range input, значение которого копируется в элемент с указанным `id` |
| `[data-stepper]`, `[data-step="1"]` / `[data-step="-1"]` | Контейнер числового input и кнопок увеличения/уменьшения |
| `[data-page]`, `[data-page-step]` | Кнопки, которые создаёт пагинация: переход к заданной странице или на ±1; вручную добавлять их не нужно |
| `[data-rating]`, `data-rating-step="0.5"` | Контейнер рейтинга с input, звёздами `[data-rating-star="N"]` и output `[data-rating-value]`; половина выбирается нажатием на левую половину звезды |
| `[data-clear-input]` | Кнопка рядом с input или textarea в общем родительском контейнере |
| `[data-filter-table="table-id"]`, `[data-clear-filter="table-id"]` | Строковый поиск таблицы и её кнопка очистки |
| `[data-filter-search]` | Поиск по названиям/тексту групп фильтров внутри `.crud-filters` |
| `[data-filter-value="значение"]` | Чекбокс фильтра; проверяемое значение ищется в тексте строки |
| `[data-apply-filters]`, `[data-reset-filters]` | Применение/сброс фильтров таблицы `#collections-table` |
| `.crud-table [data-sort-key="0"]` | Сортировка таблицы по столбцу с индексом от нуля |
| `[data-copy-row]` | Копирование текстовых значений строки, кроме первой ячейки |
| `.selectable-table .table-row-select` | Checkbox, переключающий `.is-selected` на родительской строке |

## 6. Рекомендации по расширению и доступности

1. Добавляйте стили в соответствующий SCSS-модуль; не меняйте сгенерированный `styles/style.css` напрямую.
2. Используйте семантическую разметку, подписи `label`, состояния `disabled`/`required` и необходимые ARIA-атрибуты. Кастомные checkbox/radio должны сохранять настоящий input.
3. Для интерактивных элементов предусмотрите `:focus-visible`; навигационные группы синхронизируйте по `aria-selected`, `aria-pressed` или `aria-current`.
4. Новые секции библиотечных страниц оформляйте как `.kit-section` с уникальным `id` и заголовком `h2`: боковая навигация построится автоматически.
5. Не полагайтесь на демо CRUD/формы как на серверную функциональность: для реального продукта подключите собственную валидацию, API, сохранение данных и обработку ошибок.
6. После изменений Sass проверьте сборку `npm run build`; после изменений JavaScript — `node --check js/app.js`; вручную проверьте соответствующую страницу в светлой и тёмной теме и на узком экране.
