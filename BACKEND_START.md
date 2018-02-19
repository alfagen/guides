Инструкция по запуску backend на ubuntu 16.04

## nvm

Устанавливаем по инструкции: https://github.com/creationix/nvm

## yarn

Устанавливаем по инструкции: https://yarnpkg.com/lang/en/docs/install/

## postgress

Добовляем ключ и официальный репозиторий

```sh
$ wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
$ echo "deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list
```

Устанавливаем postgresql-10

```sh
$ sudo apt-get update
$ sudo apt-get install postgresql-10
```

Нужно дать доступ всем пользователям в файле `pg_hba.conf`

```sh
$ sudo vim /etc/postgresql/10/main/pg_hba.conf
```
Добавьте строку

```diff
 # Database administrative login by Unix domain socket
 local   all             postgres                                peer

 # TYPE  DATABASE        USER            ADDRESS                 METHOD

 # "local" is for Unix domain socket connections only
 local   all             all                                     peer
 # IPv4 local connections:
+host    all             all             127.0.0.1/32            trust
 host    all             all             127.0.0.1/32            md5
 # IPv6 local connections:
 host    all             all             ::1/128                 md5
```

Запускаем postgresql

```sh
$ sudo service postgresql start
```

## redis

Вам понадобятся инструменты компиляции и тестирования:

```sh
$ sudo apt-get update
$ sudo apt-get install build-essential tcl
```

Устанавливаем redis по инструкции - https://redis.io/topics/quickstart#installing-redis

#### Возможные проблемы

* `make[2]: cc: Command not found`
        
  Решение: 
  ```sh
  sudo apt-get install build-essential tcl
  ```

* Ошибки вида `zmalloc.h:50:31: error: jemalloc/jemalloc.h: No such file or directory`
        
  Решение:
  ```sh
  $ cd deps
  $ make hiredis jemalloc linenoise lua
  $ cd ..
  $ make install
  ```

## Запуск бекенда

Нужно скопировать конфиг и поменять имя базы данных

```sh
$ cd change
$ cp config/example.json config/default.json
```
```diff
-    "database": "change_develop"
+    "database": "username"
```

Запускаем redis в отдельной консоли

```sh
$ redis-server
```

Запускаем установку в БД данных и запускаем бекенд

```sh
$ make setup
$ make seed
$ make start
```

#### Возможные проблемы

* `Error: /mnt/d/w/change/node_modules/bcrypt/lib/binding/bcrypt_lib.node: invalid ELF header`

  Решение:
  ```sh
  yarn add bcrypt
  ```
