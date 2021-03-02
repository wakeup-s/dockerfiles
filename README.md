# php7 flexible

php with additional php-extensions and utilities on demand.

## Supported tags

Actual versions:

*  [7-fpm-flexible](https://github.com/wakeup-s/dockerfiles/blob/master/php/7-fpm-flexible/Dockerfile)
*  [7-cli-flexible](https://github.com/wakeup-s/dockerfiles/blob/master/php/7-cli-flexible/Dockerfile)

Deprecated versions (will be removed in the future):

*  [7-fpm-extended](https://github.com/wakeup-s/dockerfiles/blob/master/php/7-fpm-extended/Dockerfile)
*  [7-cli-extended](https://github.com/wakeup-s/dockerfiles/blob/master/php/7-cli-extended/Dockerfile)

## Available options

All options below are disabled by default. Required options can be enabled with the value "true".

* INSTALL_GMP - GMP php-extension
* INSTALL_PDO_PGSQL - postgresql PHP pdo-client 
* INSTALL_INTL - INTL php-extension
* INSTALL_GD - php graphics library GD
* INSTALL_BCMATH - BCMATH php-extension 
* INSTALL_SOCKETS - SOCKETS php-extension
* INSTALL_FFMPEG - FFMPEG cli utility
* INSTALL_MEDIAINFO - mediainfo cli utility

## Usage

### By cli

Type command in the same directory as the `Dockerfile`.

```shell script
docker build \
  --tag 7-fpm-flexible \
  --build-arg INSTALL_GMP=true \
  --build-arg INSTALL_PDO_PGSQL=true \
  --build-arg INSTALL_INTL=true \
  --build-arg INSTALL_GD=true \
  --build-arg INSTALL_BCMATH=true  \
  --build-arg INSTALL_SOCKETS=true \
  --build-arg INSTALL_FFMPEG=true \
  --build-arg INSTALL_MEDIAINFO=true\ 
  .
```

### By docker-compose

Create local `Dockerfile` with content

````dockerfile
FROM wakeupscom/php:7-fpm-flexable
````

Then specify build options in the your `docker-compose.yml`.

```yaml
version: "3.8"
services:
    yourservice:
      build:
        context: ./
        args:
          - INSTALL_GMP=true
          - INSTALL_PDO_PGSQL=true
          - INSTALL_INTL=true
          - INSTALL_GD=true
          - INSTALL_BCMATH=true
          - INSTALL_SOCKETS=true
          - INSTALL_FFMPEG=true
          - INSTALL_MEDIAINFO=true    
```
