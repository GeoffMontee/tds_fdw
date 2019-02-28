# TDS Foreign data wrapper

* **Author:** Geoff Montee
* **Name:** tds_fdw
* **File:** tds_fdw/InstallOSX.md

## Installing on OSX

This document will show how to install tds_fdw on OSX.

### Install FreeTDS

The TDS foreign data wrapper requires a library that implements the DB-Library interface,
such as [FreeTDS](http://www.freetds.org).

```bash
brew install freetds
```

### Install PostgreSQL

If you need to install PostgreSQL, do so by following the [apt installation directions](https://wiki.postgresql.org/wiki/Apt). For example, to install PostgreSQL 9.5 on Ubuntu:

```bash
brew install postgres
```

Or use Postgres.app: <http://postgresapp.com/>

### Install tds_fdw

#### Build from release package

If you'd like to use one of the release packages, you can download and install them via something like the following:

```bash
wget https://github.com/tds-fdw/tds_fdw/archive/v1.0.7.tar.gz
tar -xvzf tds_fdw-1.0.7.tar.gz
cd tds_fdw-1.0.7
make USE_PGXS=1 PG_CPPFLAGS="-I./include/ -I/usr/local/include/ -fvisibility=hidden"
sudo make USE_PGXS=1 install
```

#### Build from repository

If you would rather use the current development version, you can clone and build the git repository via something like the following:

```bash
git clone https://github.com/tds-fdw/tds_fdw.git
cd tds_fdw
make USE_PGXS=1 PG_CPPFLAGS="-I./include/ -I/usr/local/include/ -fvisibility=hidden"
sudo make USE_PGXS=1 install
```

#### Start server

If this is a fresh installation, then start the server:

```bash
sudo /etc/init.d/postgresql start
```

#### Install extension

```bash
psql -U postgres
postgres=# CREATE EXTENSION tds_fdw;
```
