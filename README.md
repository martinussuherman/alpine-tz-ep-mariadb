# martinussuherman/alpine-tz-ep-mariadb

[![](https://img.shields.io/badge/%20%20FROM%20%20-martinussuherman%2Falpine--tz--ep-lightgray.svg)](https://hub.docker.com/r/martinussuherman/alpine-tz-ep)  [![](https://images.microbadger.com/badges/image/martinussuherman/alpine-tz-ep-mariadb.svg)](https://microbadger.com/images/martinussuherman/alpine-tz-ep-mariadb "Get your own image badge on microbadger.com")  [![](https://images.microbadger.com/badges/commit/martinussuherman/alpine-tz-ep-mariadb.svg)](https://microbadger.com/images/martinussuherman/alpine-tz-ep-mariadb "Get your own commit badge on microbadger.com")  [![](https://images.microbadger.com/badges/license/martinussuherman/alpine-tz-ep-mariadb.svg)](https://microbadger.com/images/martinussuherman/alpine-tz-ep-mariadb "Get your own license badge on microbadger.com")  [![](https://images.microbadger.com/badges/version/martinussuherman/alpine-tz-ep-mariadb.svg)](https://microbadger.com/images/martinussuherman/alpine-tz-ep-mariadb "Get your own version badge on microbadger.com")

---

## What is this image for ?

This is an [Alpine Linux](https://hub.docker.com/_/alpine/) based image for MariaDB database server.

## What is MariaDB?

[MariaDB](https://hub.docker.com/_/mariadb/) is a community-developed fork of the MySQL relational database management system intended to remain free under the GNU GPL. Being a fork of a leading open source software system, it is notable for being led by the original developers of MySQL, who forked it due to concerns over its acquisition by Oracle. Contributors are required to share their copyright with the MariaDB Foundation.

The intent is also to maintain high compatibility with MySQL, ensuring a "drop-in" replacement capability with library binary equivalency and exact matching with MySQL APIs and commands. It includes the XtraDB storage engine for replacing InnoDB, as well as a new storage engine, Aria, that intends to be both a transactional and non-transactional engine perhaps even included in future versions of MySQL.

More info on [Wikipedia](https://en.wikipedia.org/wiki/MariaDB)

## Why use this image?

*MariaDB* service on this container will run as `non-root` (`mysql`) user. This add an extra layer of security and are generally recommended for production environments. This container also allow mapping of the `user id` dan `group id` of the user running docker to `mysql` user and group, which will enable the use of more restrictive file permission.

## How to use this image?

### *Using docker run*

```bash
$ docker run --name mariadb -v /path/to/mariadb-data-on-host:/var/lib/mysql -e TZ=Asia/Jakarta -e EUID=$(id -u) -e EGID=$(id -g) martinussuherman/alpine-tz-ep-mariadb
```
This will set the `timezone` to Asia/Jakarta (you will want to change it to your own timezone) and map the `user id` dan `group id` of the current user to `mysql` user and group.

### *Using docker-compose*

```yaml
version: '3'

services:
  mariadb:
    image: martinussuherman/alpine-tz-ep-mariadb
    environment:
      - TZ=Asia/Jakarta
      - EUID=1001
      - EGID=1001
    volumes:
      - /path/to/mariadb-data-on-host:/var/lib/mysql
```

*Note:* you will want to change the value for `EUID` and `EGID` with your current user `user id` dan `group id`.
