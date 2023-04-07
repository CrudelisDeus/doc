# Dump

### Full base

```bash
pg_dump -U postgres -p 5432 -f name.sql baseName
```

### Scheme

```bash
pg_dump -n schemeName -s -p 5432 -U postgres -f name.sql baseName
```

### Table

```bash
# full
pg_dump -U postgres -p 5432 -f new.sql -d baseName -t scheme.table

# only data
pg_dump -U postgres -p 5432 -f new.sql -d baseName -a -t scheme.table
```

## Paste

### Paste backup

```bash
psql -U postgres -f baseName.sql -p 5432 baseName
```