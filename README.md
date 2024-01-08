# Домашнее задание к занятию «Работа с данными (DDL/DML)»

### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

1.2. Создайте учётную запись sys_temp. 

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

1.4. Дайте все права для пользователя sys_temp. 

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос: 
```sql
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.7. Восстановите дамп в базу данных.

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*


### Решение 1

1.1.  Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

![Commit Task1](https://github.com/AndrewZnamenskiy/DDL_DML/blob/main/img/task1p1.png)


1.2. Создайте учётную запись sys_temp.

#### Команда для создания учётной записи sys_temp:

`mysql> CREATE USER 'sys_temp'@'%' IDENTIFIED BY 'pass123';`

![Commit Task1](https://github.com/AndrewZnamenskiy/DDL_DML/blob/main/img/task1p2.png)


1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

#### Команда вывода списка пользователей MySQL:

`SELECT User FROM mysql.user;`

![Commit Task1](https://github.com/AndrewZnamenskiy/DDL_DML/blob/main/img/task1p3.png)


1.4. Дайте все права для пользователя sys_temp.

#### Команда для повышения прав учётной записи sys_temp:

```
	mysql> GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'%';	
	mysql> FLUSH PRIVILEGES;
```

![Commit Task1](https://github.com/AndrewZnamenskiy/DDL_DML/blob/main/img/task1p4.png)


1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

#### Команда для просмотра прав пользователя sys_temp:

`SHOW GRANTS FOR sys_temp \G`

![Commit Task1](https://github.com/AndrewZnamenskiy/DDL_DML/blob/main/img/task1p5.png)


1.6. Переподключитесь к базе данных от имени sys_temp. Сменить тип аутентификации с sha2.

#### Команды смены типа аутентификации пользователя sys_temp:

```
	SELECT CURRENT_USER();
	ALTER USER 'sys_temp'@'%' IDENTIFIED WITH mysql_native_password BY 'pass123';
```

![Commit Task1](https://github.com/AndrewZnamenskiy/DDL_DML/blob/main/img/task1p6.png)


1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.7. Восстановите дамп в базу данных.

#### Команды импорта схемы и БД:

```
	mysql -uroot -p < sakila-schema.sql
	mysql -uroot -p < sakila-data.sql
```

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. (скриншот)


![Commit Task1](https://github.com/AndrewZnamenskiy/DDL_DML/blob/main/img/task1p7.png)


### Решение 2

![Commit Task2](https://github.com/AndrewZnamenskiy/DDL_DML/blob/main/img/task2p1.png)


## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 3*
3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.

3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*
