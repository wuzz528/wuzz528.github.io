## PostgreSQL backup & restore

### Backup 
`pg_dump --file ${backup file}  --port "5432"  --format=c --blobs --schema ${schema} ${database} -U ${user}` 
### Restore
`pg_restore  -U ${user} --exit-on-error --verbose --dbname=${database} ${backup file}`
