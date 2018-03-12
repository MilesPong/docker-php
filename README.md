# PHP with Extensions

This PHP image is based on official [ `php:alpine`](https://hub.docker.com/_/php/) image with additional extensions support.

## Supported tags

- [`7.2-fpm-alpine`](7.2/fpm/Dockerfile)

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