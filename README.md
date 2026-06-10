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
![image](https://github.com/user-attachments/assets/184e3fcc-9a71-49d4-a251-cfaffc5ca2a3)

pgtest01: примонтировать shared backup директорию
> mkdir /backup && mount -t virtiofs pgbackup /backup  && chown postgres:postgres /backup
![image](https://github.com/user-attachments/assets/4fed5c2b-b7a1-4081-8c92-d282de803150)

Выставить параметры и перезапустить кластер
```
postgres@pgtest01:~$ diff  /etc/postgresql/17/main/postgresql.conf /etc/postgresql/17/main/postgresql.conf_bkp4Jub2025
60c60
< listen_addresses = '*'                # what IP address(es) to listen on;
---
> #listen_addresses = 'localhost'               # what IP address(es) to listen on;
268c268
< archive_mode = on             # enables archiving; off, on, or always
---
> #archive_mode = off           # enables archiving; off, on, or always
274,275c274
<                               # placeholders: %p = path of file to archi
< archive_command = 'test ! -f /backup/archives/%f && cp %p /backup/archives/%f'
---
>                               # placeholders: %p = path of file to archive
```

## (1) Настройте бэкапы PostgreSQL с использованием WAL-G, pg_probackup или любого другого аналогичного ПО для базы данных "Лояльность оптовиков".

Делаем инкрементальный бэкап средствами pg_basebackup





