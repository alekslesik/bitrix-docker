## BITRIX DOCKER (ALPHA)
Контейнеры для развертывания\установки сайта на битрикс

## В сборке
- PHP 7.4.33 (cli) (gd, xdebug 3.1.6, )
- mysql 5.7

## Начало работы
- Склонируйте репозиторий bitrix-docker
```
git clone https://github.com/alekslesik/bitrix-docker
```

## Установка bitrix

Создать и заполнить файл `.env` (пример .env.example). ВСЕ ПОЛЯ ОБЯЗАТЕЛЬНЫ

<!-- TODO сделать -->
### Установка через `bitrixsetup.php`

1. Собрать контейнеры командой 

```
make run
```

или если нет поддержки Makefile:

```
docker-compose up --build -d
```
<!-- - Скачайте `bitrixsetup.php` (файл будет скачан с официального сайта автоматически)
```
make bitrix-setup
``` -->

2. В браузере ввести `http://localhost:80/bitrixsetup.php`
> При установке `bitrix` необходимо в окне создания базы данных в графе "Сервер" 
`localhost` заменить на `mysql` (так как контейнер поднятый в сети имеет название `mysql`)

### Востановление через `restore.php`
<!-- - Скачайте `restore.php` (файл будет скачан с официального сайта автоматически)
```
make bitrix-restore url=<ссылка для переноса>
``` -->

1. Скопировать бекап в папку `backup`

2. Собрать контейнеры командой 

```
make run
```

или если нет поддержки Makefile:

```
docker-compose up --build -d
```

3. В браузере ввести `http://localhost:80/restore.php`
> При востановлениии необходимо в окне создания базы данных в графе "Сервер" 
`localhost` заменить на `mysql` (так как контейнер поднятый в сети имеет название `mysql`)

#### TODO Сделать привязку к IP или доменному имени
#### TODO Сделать volume для  mysql
#### TODO Сделать настройку deploy
#### TODO Сделать настройку xdebug
#### TODO Сделать загрузку restore.php внутри контейнера через Makefile
