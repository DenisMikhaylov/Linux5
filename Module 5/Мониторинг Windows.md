

Настройка авторегистрации систем с агентами, работающими в активном режиме

```
Alert - Actions - Auto registration 
  Name: Add Windows clients                                          # or Add Linux clients
  Conditions: Host name contains CLIENT                              # or client (lowercase) for linux
  Action operations: 
    Add to host groups: Windows clients                              # or Linux clients
    Link to templates: Windows by Zabbix agent active                # or Linux by Zabbix agent active
                 
  Set host inventory mode: Automatic
```
Подключиться к Windows сервер

Настройка агента на активный режим
Отредактировать файл конфигурации агента и перезапустить службу агента

C:\Program Files\Zabbix Agent\zabbix_agentd.conf

```
LogFile=C:\Program Files\Zabbix Agent\zabbix_agentd.log
#Server=<ip address zabbix or Name>
ListenIP=0.0.0.0
ServerActive=<ip address zabbix or Name>
Hostname=CLIENTN
```

Создание элемента мониторинга 

perf_counter[\"\Processor(_Total)% Processor Time\",60]

