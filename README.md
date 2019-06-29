# PHP with Extensions

This PHP image is based on official [ `php:alpine`](https://hub.docker.com/_/php/) image with additional extensions support.

## Supported tags

- [`7.2-fpm-alpine`](https://github.com/MilesPong/docker-php/blob/master/7.2/fpm/Dockerfile)

## Extensions

From source of `Dockerfile`:

- mysqli
- pdo_mysql
- zip
- opcache
- gd

Result:

```
$ docker run --rm milespeng/php:$tag php -m
[PHP Modules]
Core
ctype
curl
date
dom
fileinfo
filter
ftp
gd
hash
iconv
json
libxml
mbstring
mysqli
mysqlnd
openssl
pcre
PDO
pdo_mysql
pdo_sqlite
Phar
posix
readline
Reflection
session
SimpleXML
sodium
SPL
sqlite3
standard
tokenizer
xml
xmlreader
xmlwriter
Zend OPcache
zip
zlib

[Zend Modules]
Zend OPcache
```

## ARG

| Name | Description | Default |
|--|--|--|
| `ALPINE_URL` | Alpine mirror | `dl-cdn.alpinelinux.org` |
| `TZ` | Timezone | `UTC` |

## ENV

| Key | Description | Example |
|--|--|--|
| `TZ` | Timezone | `UTC` |

## Docker compose

Now we use php as a seperate docker service via docker compose. Since the external named network is defined, it's easy to 'join' with other docker services such as `nginx`, `mysql` and so on.

From the beginning, prepare some config file as follow,

```bash
cp 7.2/config/templates/php.ini.production 7.2/config/php.ini
cp 7.2/config/templates/php-fpm.conf.default 7.2/config/php-fpm.conf
cp 7.2/config/templates/www.conf.default 7.2/config/www.conf
```

Then modify above files depends on your condition.

```bash
cp .env.example .env
docker network create php-network
docker-compose up -d
```