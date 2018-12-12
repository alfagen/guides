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
 
