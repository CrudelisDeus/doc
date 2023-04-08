# Script

## Uploading backups to one database on the selected port


**Description:** The script sets the working directory where the backups are located, and selects them in a loop and uploads schema and table backups to the raised db.

```bash
#!/bin/bash

backupDir="/path"

backupNames=($(ls "${backupDir}"/*.sql))

for name in "${backupNames[@]}"
do
  echo "Restore schema, table ${name}..."
  psql -U postgres -f "${name}" -p 5432 nameBD
done
```

### Parameters

Need to set parameters:

- nameBD - name database 

- backupDir - Directory where backups are located

- -p - port select