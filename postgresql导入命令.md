```bash
root@test:~# cat auto_import.sh
#!/bin/bash
sudo -u appuser scp job1:cinema-data-backup/cinema-app.gz /data/
gunzip /data/cinema-app.gz
if [ -f "/data/cinema-app" ]; then
 chmod 777 /data/cinema-app
 sudo -u postgres psql -c "SELECT pg_terminate_backend(pg_stat_activity.pid) FROM pg_stat_activity WHERE datname='cinema-app-show' AND pid<>pg_backend_pid();"
 sudo -u postgres psql -c 'drop database "cinema-app-show"'
 sudo -u postgres psql -c 'create database "cinema-app-show"'
 cat /data/cinema-app |sudo -u postgres psql cinema-app-show
 for i in `sudo -u postgres psql -d 'cinema-app-show' -c "select 'alter table ' || tablename || ' OWNER TO "user";' from pg_tables where tableowner='postgres' and schemaname='public';"`;do sudo -u postgres psql -d 'cinema-app-show' -c $i;done
fi
mv /data/cinema-app /data/cinema-app.bak
#composer dumpautoload
sudo -u appuser php /var/www/cinema-admin-show/artisan db:seed --class=AuthAdmin
```
