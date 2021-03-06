# MySQL/mariaDB
Initializes the data directory
```
mysql_install_db
mariadb-install-db
```

Set security settings
```
mysql_secure_installation
mariadb-secure-installation
```

Check & Repair
```
mysqlcheck --check-upgrade --all-databases --auto-repair
mysql_upgrade --force
```

Clear command history
```
rm $HOME/.mysql_history
```

## PostgreSQL
Login as a postgres user
```
su - postgres
sudo -u postgres psql
```

Connenct to console
```
psql
```

Exit
```
\q
```

## SQL
Create database
```
echo "CREATE DATABASE `my_db` CHARACTER SET utf8 COLLATE utf8_general_ci;" | mysql
```

Create user
```
echo "CREATE USER 'name'@'localhost' IDENTIFIED BY 'password';" | mysql
```

Give privileges for user
```
echo "GRANT ALL PRIVILEGES ON `db`.* TO 'name'@'localhost';" | mysql
```

Reloads the privileges
```
echo "FLUSH PRIVILEGES;" | mysql
```

Edit user account
```
echo "RENAME USER 'name'@'localhost' TO 'name'@'%';" | mysql
```

Last entry
```
SELECT MAX(`my_table`) FROM my_db;
SELECT TOP 10 * FROM my_db ORDER BY my_table DESC
```

Set password for user
```
echo "ALTER USER 'name'@'localhost' IDENTIFIED BY 'MyNewPass';" | mysql
```

Delete user
```
echo "DROP USER 'name'@'localhost';" | mysql
```

User as root privileges
```
echo "GRANT ALL PRIVILEGES ON *.* TO 'name'@'%' with GRANT OPTION;" | mysql
```

Give backup privileges for user
```
echo "GRANT SELECT, SHOW VIEW, EVENT, TRIGGER, RELOAD, PROCESS, LOCK TABLES, REPLICATION CLIENT ON *.* TO 'name'@'localhost'" | mysql
```

Import dump
```
gunzip < DUMP_FILE.sql.gz | mysql my_db --user= --password= --host=
```
```
USE database_name;
SOURCE path_to_sql_file;
```

Export dump
```
mysqldump  --skip-extended-insert my_db | gzip > DUMP_FILE.sql.gz
```

InnoDB warnings become errors instead
```
SET GLOBAL innodb_strict_mode=ON;
SET SESSION innodb_strict_mode=ON;
```

Check foreign key constraints for InnoDB tables
```
SET FOREIGN_KEY_CHECKS = 1
```

Show in which table the column
```
SELECT *
FROM information_schema.columns
WHERE column_name='column_name';
```

Show information about table
```
DESCRIBE table_name;
```

Show query information
```
EXPLAIN SELECT * FROM categories
```

Count rows in table
```
SELECT COUNT(*) FROM table_name
```

## MyTOP
Monitor the database
```
mytop --prompt -d database_name
```
