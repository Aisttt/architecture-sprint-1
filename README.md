# Проект Mesto - Декомпозиция на микрофронтенды

Этот проект представляет собой микрофронтенд-архитектуру приложения "Mesto", разделенного на несколько независимых микрофронтендов с использованием **Webpack Module Federation**.

## Описание проекта

Проект Mesto – это веб-приложение для обмена фотографиями, с возможностью регистрации и входа пользователя, редактирования профиля и аватара, а также управления карточками фотографий.

Для более гибкого развития и поддержки, фронтенд был разделен на микрофронтенды по функциональным областям.

## Выбранный подход: Module Federation

Было принято решение использовать **Webpack Module Federation** из-за следующих преимуществ:
- Позволяет независимую разработку отдельных частей приложения разными командами.
- Предоставляет возможность динамической загрузки и обмена модулями между микрофронтендами.
- Легко интегрируется с существующим проектом на React.

## Архитектура проекта
Каждый микрофронтенд выполняет свою уникальную роль разделенную по функциональным областям.  
Это позволяет легко масштабировать, поддерживать и развивать проект в будущем.  

### Главный микрофронтенд (`main-microfrontend`)
- **Роль**: Контейнер для остальных микрофронтендов. Отвечает за маршрутизацию и общий контекст.
- **Основные файлы**:
  - `App.js` - основной компонент приложения.
  - `Header.js` и `Footer.js` - общие компоненты навигации и футера.
  - `ProtectedRoute.js` - компонент для управления защищенными маршрутами.
  - **Стили**: Общие стили и структура проекта (`index.css`), `header.css`, `footer.css`.

### Микрофронтенд аутентификации (`auth-microfrontend`)
- **Роль**: Управление функциональностью регистрации и входа пользователя.
- **Основные файлы**:
  - `Login.js` и `Register.js` - компоненты для аутентификации.
  - `InfoTooltip.js` - компонент для вывода сообщений о статусе регистрации/входа.
  - `auth.js` - утилиты для работы с API аутентификации.
- **Стили**: `auth-form.css`

### Микрофронтенд профиля (`profile-microfrontend`)
- **Роль**: Управление профилем пользователя и аватаром.
- **Основные файлы**:
  - `EditProfilePopup.js` - компонент для редактирования профиля.
  - `EditAvatarPopup.js` - компонент для обновления аватара.
- **Стили**: `profile.css`

### Микрофронтенд карточек (`places-microfrontend`)
- **Роль**: Управление карточками фотографий и отображение контента на главной странице.
- **Основные файлы**:
  - `Main.js` - главный компонент для отображения профиля и карточек.
  - `Card.js` - компонент для отображения отдельной карточки.
  - `AddPlacePopup.js` - компонент для добавления новой карточки.
  - `ImagePopup.js` - компонент для отображения увеличенной карточки.
  - `api.js` - утилиты для работы с API карточек.
- **Стили**: `card.css`, `popup.css`

## Структура проекта

- **/auth-microfrontend**
  - **/src**
    - **/components**
      - `Login.js` – Компонент входа пользователя
      - `Register.js` – Компонент регистрации пользователя
    - **/styles**
      - `login.css` – Стили для компонента входа
      - `register.css` – Стили для компонента регистрации
    - **/utils**
      - `auth.js` – Утилиты для аутентификации
    - `index.js` – Точка входа микрофронтенда
  - `package.json` – Зависимости и скрипты микрофронтенда
  - `webpack.config.js`

- **/profile-microfrontend**
  - **/src**
    - **/components**
      - `EditProfilePopup.js` – Компонент для редактирования профиля
      - `EditAvatarPopup.js` – Компонент для обновления аватара
    - **/styles**
      - `profile.css` – Стили для компонента профиля
    - `index.js` – Точка входа микрофронтенда
  - `package.json` – Зависимости и скрипты микрофронтенда
  - `webpack.config.js`

- **/places-microfrontend**
  - **/src**
    - **/components**
      - `Main.js` – Главный компонент для отображения профиля и карточек
      - `Card.js` – Компонент для отображения карточки
      - `AddPlacePopup.js` – Компонент для добавления новой карточки
      - `ImagePopup.js` – Компонент для отображения увеличенной карточки
    - **/utils**
      - `api.js` – Утилиты для работы с API карточек
    - **/styles**
      - `card.css` – Стили для карточек
      - `popup.css` – Стили для всплывающих окон
    - `index.js` – Точка входа микрофронтенда
  - `package.json` – Зависимости и скрипты микрофронтенда
  - `webpack.config.js`

## Установка и запуск проекта
1. Клонируйте репозиторий;
2. Перейдите в директорию каждого микрофронтенда и установите зависимости:  
```bash
git clone https://github.com/Aisttt/architecture-sprint-1/tree/sprint_1


cd auth-microfrontend
npm install
npm start

cd ../profile-microfrontend
npm install
npm start

cd ../places-microfrontend
npm install
npm start

cd ../main-microfrontend
npm install
npm start
