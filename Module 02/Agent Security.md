# Настройка zabbix agent

Устанавливаем агента  на компьютеры, которые будут использоваться в рамках нашей инфраструктуры.

Уст

Прежде чем менять файл с настройками сгенерируем на своем компе psk фразу командой и записываем ее в файл
```
openssl rand -hex 32 > /etc/zabbix/zabbix_proxy.psk
```
Далее выводим этот ключ на экран командой 
```

tail /etc/zabbix/zabbix_proxy.psk
```
Сохраняем где нибудь у себя данный ключ он нам пригодиться при настройки серверной части заббикса
И вот теперь конфигурируем файл с настройками

```
nano /etc/zabbix/zabbix_proxy.conf
```

Меняем следующие значения:\
Server=    ваш ip adresss\
Hostname=  такой же нужно будет прописать на основном сервере\
DBName= /tmp/zabbix_proxy\
TLSAccept=psk
TLSConnect=psk\
TLSPSKFile=/etc/zabbix/zabbix_proxy.psk\
TLSPSKIdentity=test  - тут меняйте значение на свое - такое же должно использоваться на серверной части\

```
systemctl restart zabbix-proxy
systemctl enable zabbix-proxy
```

