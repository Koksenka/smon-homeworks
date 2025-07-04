# Домашнее задание к занятию «Система мониторинга Zabbix»- Москаленко В.В.



### Задание 1
### Установите Zabbix Server с веб-интерфейсом.

### Решение


!![alt text](https://github.com/Koksenka/smon-homeworks/blob/master/1.png)
![alt text](https://github.com/Koksenka/smon-homeworks/blob/master/2.png)

---


1. apt update
1. apt upgrade

1. apt install postgresql

1. wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
1. dpkg -i zabbix-release_6.0-4+debian11_all.deb
1. apt update
1. apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent

1. sudo -u postgres createuser --pwprompt zabbix
1. sudo -u postgres createdb -O zabbix zabbix

1. cat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
1. nano /etc/zabbix/zabbix_server.conf (задать пароль DBPassword=password)

1. systemctl restart zabbix-server zabbix-agent apache2
1. systemctl enable zabbix-server zabbix-agent apache2
---

### Задание 2
### Установите Zabbix Agent на два хоста.

### Решение
![alt text](https://github.com/Koksenka/smon-homeworks/blob/master/3.png)
![alt text](https://github.com/Koksenka/smon-homeworks/blob/master/4.png)
![alt text](https://github.com/Koksenka/smon-homeworks/blob/master/5.png)
---
1. apt update
1. apt upgrade

1. wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
1. dpkg -i zabbix-release_6.0-4+debian11_all.deb
1. apt update
1. apt install zabbix-agent

1. systemctl restart zabbix-agent
1. systemctl enable zabbix-agent

1. nano /etc/zabbix/zabbix_agentd.conf