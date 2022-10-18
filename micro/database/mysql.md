# MySQL Database
### Setup MySQL database
* Download mysql server 8 zip file and extract to a folder
* cd c:\mysql\bin\mysqld --initialize --console

A temporary password is generated for root@localhost: Ace2kddas

### Start and change the root password
```sql
$ start mysqld --console
$ mysql -u root -p
Enter your temporary password

sql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'pass123';
flush privileges;
exit;

$ mysql -u root -p
pass123
```

### Stop database
```sql
$ mysqladmin shutdown -u root -p
```

```sql
sql> show databases;
sql> create database amazon;
sql> use amazon;
sql> create table employee (id int(5) not null auto_increment, name varchar(20), salary double(6,2), doj date, dept int(5), primary key(id));
sql> alter table employee AUTO_INCREMENT=100;
```
