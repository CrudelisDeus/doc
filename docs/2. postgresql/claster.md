# Claster

## Install PostgreSQL

Example: PostgreSQL 13.

```bash
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -sc)-pgdg main" > /etc/apt/sources.list.d/PostgreSQL.list'

sudo apt update

sudo apt-get install -y postgresql-13 postgresql-client-13
```

## Create claster

Standart port 5432.

```bash
service postgresql stop

mkdir -p /data && chown -R postgres /data

sudo -u postgres /usr/lib/postgresql/13/bin/initdb -E 'UTF-8' -D /data

sudo -u postgres /usr/lib/postgresql/13/bin/pg_ctl start -D /data
```