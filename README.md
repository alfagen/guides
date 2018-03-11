# alfa guides
Правила, инструкции и нотации по разработке

# Структура директорий проекта

В любом проекте есть константа, которая указывает на корневой каталог (`ROOT_PATH`).

В проекте есть следующие папки:

`./app` - собственно приложение. Когда проект компилируемый, этот каталог могу называть `./src`

`./config` - конфиги. Конфиги доступа к базе, настройка проекта, локализация.

`./tmp` - временные файлы. Сам каталог лежит в репозитории, но его содержимое в `.gitignore`

`./log`  - логи.  Сам каталог лежит в репозитории, но его содержимое в `.gitignore`

`./vendor` - тут лежат модули сторонних поставщиков (vendors)

`./doc` - документация 

`./lib` - собственные библиотеки. Код, который часто используется, но не является состовной частью проекта.

`./test` - тесты

`./spec` - спецификации

`./bin` - бинарные файлы (утилиты, которые пригодятся в проекте). Иногда называют `./scripts` или `./utils`

`./dist` - для компилируемых проектов результат последний компиляции (от слова distributive - распространение), иногда называют `./build`, но, как правило, build означает временное хранение результатов build-а, не предназначенных для дистрибьюции.

`./public` - публичные файлы, которые отдаются веб-сервером "как-есть" без обработки. 

# Инструменты окружения разработчика

* rbenv - https://github.com/rbenv/rbenv (устанавливать только локально в домашний каталог)
* nvm - https://github.com/creationix/nvm (устанавливать только локально в домашний каталог)
* direnv - https://direnv.net (можно устанавливать системно через apt-ge)

# Правила работы с ветками в репозитории:

* (git flow) A successful Git branching model - http://nvie.com/posts/a-successful-git-branching-model/


# Замечания по ратое с кодом

## Строго:

* Не использовать относительные пути в импортах `import loadMessages from '../server/intl/loadMessages'`
* Стараться НЕ привязывать JS к классам и идентификаторам (использовать data или спец-атрибут)
* В package.json в dependencies лежать и dev зависимости и НЕ dev зависимости.

## Желательно:

*  Использовать константы для определения action-ов:
  src/verification/actions.js:    type: 'app/cards/INITIAL',
  src/verification/reducer.js:    case 'app/cards/INITIAL':


# Развертывание

* Отличное введение в docker - http://guides.hexlet.io/docker/
* Хорошое введение в capistrano - http://guides.beanstalkapp.com/deployments/deploy-with-capistrano.html


# Другие гайды

* hexlet - http://guides.hexlet.io


# Работа с git-ом

* Курс - https://ru.hexlet.io/courses/intro_to_git

В message комитов указываем номер задачи из Pivotal - `[(Finishes|Fixes|Delivers) #TRACKER_STORY_ID]`

# Прочее

* https://12factor.net/ru/

# Целевая ОС на серверах

* Ubuntu 16.04.3 LTS minimal

