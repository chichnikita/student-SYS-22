# `Домашнее задание к занятию "Система мониторинга Zabbix"` - `Чичулин Никита SYS-22`



1. [Описание домашнего задания к занятию «Система мониторинга Zabbix»](https://github.com/netology-code/sdvps-homeworks/blob/main/8-03.md)

---

1. ### Задание 1

   Установите Zabbix Server с веб-интерфейсом.

   #### Процесс выполнения

   1. Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
   2. Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.
   3. Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.
   4. Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.



### Ответ 1

<img src = "img/Zabbix/1_1.png" width = 100%>

```bash
 sudo apt install -y postgresql-13
 wget https://repo.zabbix.com/zabbix/6.4/debian/pool/main/z/zabbix-release/zabbix-release_6.4-1+debian11_all.deb
 sudo dpkg -i zabbix-release_6.4-1+debian11_all.deb
 sudo apt update
 sudo apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
 sudo -u postgres createuser --pwprompt zabbix
 sudo -u postgres createdb -O zabbix zabbix
 zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
 sudo nano /etc/zabbix/zabbix_server.conf
 sudo systemctl restart zabbix-server zabbix-agent apache2
 sudo systemctl enable zabbix-server zabbix-agent apache2
```

--------

### Задание 2

1. ### Задание 2

   Установите Zabbix Agent на два хоста.

   1. Процесс выполнения
   2. Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
   3. Установите Zabbix Agent на 2 виртмашины, одной из них может быть ваш Zabbix Server
   4. Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов
   5. Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera
   6. Проверьте что в разделе Latest Data начали появляться данные с добавленных агентов

### Ответ 2

1. Раздел Configuration > Hosts - видно, что агенты подключены к серверу

<img src = "img/Zabbix/2_1.png" width = 100%>

1. Логи zabbix agent - видно, что он работает с сервером

[<img src = "img/Zabbix/2_2.png" width = 100%>

1. Раздел Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.

<img src = "img/Zabbix/2_3.png" width = 100%>

Используемые команды:

```bash
rpm -Uvh https://repo.zabbix.com/zabbix/6.4/rhel/7/x86_64/zabbix-release-6.4-1.el7.noarch.rpm
sudo yum clean all
sudo yum install zabbix-agent
sudo systemctl restart zabbix-agent
sudo systemctl enable zabbix-agent
sudo nano /etc/zabbix/zabbix_agentd.conf
sudo systemctl restart zabbix-agent
```