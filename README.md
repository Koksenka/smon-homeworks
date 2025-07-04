# Домашнее задание к занятию «Система мониторинга Zabbix»- Москаленко В.В.



### Задание 1
### Установите Zabbix Server с веб-интерфейсом.

### Решение

apt update
apt upgrade

apt install postgresql

wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
dpkg -i zabbix-release_6.0-4+debian11_all.deb
apt update
apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent

sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix

zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
nano /etc/zabbix/zabbix_server.conf (задать пароль DBPassword=password)

systemctl restart zabbix-server zabbix-agent apache2
systemctl enable zabbix-server zabbix-agent apache2
---

### Задание 2
### Установите Zabbix Agent на два хоста.

### Решение
apt update
apt upgrade

wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
dpkg -i zabbix-release_6.0-4+debian11_all.deb
apt update
apt install zabbix-agent

systemctl restart zabbix-agent
systemctl enable zabbix-agent

nano /etc/zabbix/zabbix_agentd.conf