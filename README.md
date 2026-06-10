# Домашнее задание Сартисона Евгения №1 #

ДЗ: Необходимо написать к каким системам по CAP теореме относятся перечисленные БД и почему: MongoDB, MSSQL, Cassandra.


***Как настроить бэкапы так, чтобы они не влияли на производительность системы?***

Задание:

## MongoDB ##

создал 2 виртуальные машины в YC 
![image](https://github.com/user-attachments/assets/26e5d891-af2e-48ac-8084-7692d460eed1)


pgtest01: установка Postgres
```
sudo apt install curl ca-certificates
sudo install -d /usr/share/postgresql-common/pgdg
sudo curl -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.asc --fail https://www.postgresql.org/media/keys/ACCC4CF8.asc
sudo sh -c 'echo "deb [signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt noble-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
sudo apt update
sudo apt install postgresql-17 postgresql-client-17
```

## MSSQL ##


## Cassandra ##
