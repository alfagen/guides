# alfa guides
Правила, инструкции и нотации по разработке

# Инструменты окружения разработчика

* rbenv - https://github.com/rbenv/rbenv
* nvm - https://github.com/creationix/nvm
* direnv - https://direnv.net

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
