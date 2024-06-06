# CurrencyExchange

# Название проекта
Добавьте краткое описание проекта, опишите какую задачу он решает. 1-3 предложения будет достаточно. Добавьте бейджи для важных статусов проекта: статус разработки (в разработке, на поддержке и т.д.), статус билда, процент покрытия тестами и тд.

### Содержание
- [Технологии](#технологии)
- ...

### Технологии
- [FastApi](https://fastapi.tiangolo.com/)
- ...

### Использование
Расскажите как установить и использовать ваш проект, покажите пример кода:

```sh

```

### Разработка

### Требования

### Установка зависимостей
Для установки зависимостей, выполните команду:
windows:
```sh
pip insatll reguirements.txt
```
linux:
```sh
pip3 insatll reguirements.txt
```
mac:
```sh
python -m pip install requirements.txt
```

### Запуск Development сервера
Чтобы запустить сервер для разработки, выполните команду:
```sh

```

### Создание билда
Чтобы выполнить production сборку, выполните команду: 
```sh

```

### Тестирование
Какие инструменты тестирования использованы в проекте и как их запускать. Например:

Наш проект покрыт юнит-тестами Jest. Для их запуска выполните команду:
```sh

```

### Deploy и CI/CD
Расскажите, как развернуть приложение. Как запустить пайплайны и т.д.

## Contributing
### Отправить предложение или баг-репорт:
#### <a href="https://t.me/K_1_R_1_1_1">Телеграм</a>
#### <a href="mailto:n17k17@yandex.ru">Почта</a>

### Зачем вы разработали этот проект?
Чтобы был...

## To do
- [x] Добавить крутое README
- [ ] Всё переписать
- [ ] ...


## Источники
Если вы чем-то вдохновлялись, расскажите об этом: где брали идеи, какие туториалы смотрели, ссылки на исходники кода. 

# Краткий обзор структуры:
    1) В папке endpoints лежат файлы с конечными точками (как минимум две группы конечных точек);
    2) В папке models лежат модели Pydantic;
    3) В ядре (core) лежат файлы, касающиеся настроек приложения и безопасности;
    4) В папке utils размещена логика работы с внешним API.

# Задачи для реализации (техническое задание)
1) Аутентификация пользователя (JWT) - файлы users.py, security.py:
   - Создайте конечную точку регистрации (/auth/register/) пользователя с именем пользователя и паролем. Вместо базы данных можете использовать словарь / массив, как было у нас в курсе. 
   - Реализовать конечную точку входа пользователя в систему (/auth/login/) для генерации токенов JWT для аутентификации.
   - В файле security.py расположены схема аутентификации (OAuth2 - OAuth2PasswordBearer), функция по созданию JWT-токена, функция по декодированию JWT-токена и функция по извлечению информации о юзере из полезной нагрузки.

2) Обмен валюты - файлы currency.py, external_api.py:
   - Внедрить защищенную конечную точку для получения свежих обменных курсов для различных валют из открытого API обменных курсов (/currency/exchange/).
   - Разрешить пользователям выполнять конвертацию валют на основе выбранных обменных курсов в случае подтверждения валидности JWT-токена (используйте класс Depends).
   - Внедрить обработку ошибок для таких случаев, как недопустимые коды валют.
   - Вынесите логику осуществления запроса с внешнего ресурса (API) в отдельный сервис/функции в отдельном файле (как минимум, потребуются функции запросить текущий курс по валютной паре, и запросить список валют (кодов) для получения курса). Обращаться к внешнему сервису из вашего приложения можно с использованием библиотеки requests или aiohttp. 

3) Дополнительные маршруты - файл currency.py:
   - Создайте защищенную конечную точку для отображения списка поддерживаемых валют и их кодов (/currency/list/).

4) Модели Pydantic - файлы в папке models (альтернативное название этой папки - schemas):
   - Создайте модели Pydantic для автоматической валидации получаемых данных (например, модель юзера - юзернейм/пароль, модель валют - валюта 1, валюта 2, количество для обмена - по умолчанию 1).

5) Тестирование - файлы в папке tests:
   - Напишите модульные тесты для реализованных маршрутов и функций.
   - Обеспечьте тестовое покрытие для аутентификации и функциональности обмена валюты.

6) Конфигурация среды - файлы .env, config.py:
   - Храните конфиденциальные переменные конфигурации (например, открытый ключ API обменных курсов, секретные настройки для JWT-токена) в файле `.env`. Загрузить настройки приложения можете в файле config.py, например с применением библиотек python-dotenv, environs или pydantic-settings. 

8) Руководство по прочтению и использованию:
   - Предоставьте четкие инструкции в README о том, как настроить и запустить проект.
   - Включите примеры запросов API и ответов в README.
   - Перечислите используемые (применяемые в проекте) фичи.

П.С. для включения в main.py ваших маршрутов из /app/api/endpoints/ примените знания из урока 8.1 об APIRouter'ах. 
# API:
### <a href="https://apilayer.com/marketplace/currency_data-api">API обмена валют</a>
