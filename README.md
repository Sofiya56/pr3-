# Інструкція зі створення тому та запуску контейнера

## Створення нового тому
Виконайте команду:
```bash
docker volume create mssql-storage

запуск контейнера:
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=YourStrongPassword" \
-v mssql-storage:/var/opt/mssql \
-p 1433:1433 --name mssql-study -d \
mcr.microsoft.com/mssql/server:2022-latest

скрипти:
docker exec -i sql_container /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "<your_password>" -d master -i /path/to/SETUP.sql
docker exec -i sql_container /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "<your_password>" -d master -i /path/to/INSERT.sql
docker exec -i sql_container /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "<your_password>" -d master -i /path/to/UPDATE.sql
