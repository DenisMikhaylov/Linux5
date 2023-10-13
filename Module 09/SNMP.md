
Подключаемся к серверу zabbix

Установка snmp консоли
```
# apt install snmp snmp-mibs-downloader
# :> /etc/snmp/snmp.conf
```


Включение SNMP на Windows 

Добавить елмпонент Service SNMP и WMI for SNMP

Настроить службу SNMP

На вкладке безопасность добавить имя public

И выставить признак принимать запросы от люого узла

На вкладке Агент SNMP выставить чекбокс для всех служб


Настроить автоматичекое добавление
```
Discovery
New Discovery rules
  Name: Local network new
  IP range: 192.168.10.1-254
  Checks: 
    Check type: SNMPv2 agent 
    SNMP community: public
    SNMP OID .1.3.6.1.2.1.1.5.0
    Add
  Update interval: 3m



Alert->Actions-> Discovery action
  Create action
    Name: Action add snmp device to zabbix
    Conditions: 
      Discovery status: equals Up                 
      Add
    Operations: 
      Add to host groups: Discovered hosts            
      Link to templates:
              1. Windows by SNMP
             2.Template SNMP Device
             3.Template Module Generic SNMPv2
             4.Template Module Interfaces Simple SNMPv2
      Set host inventory mode: Automatic
    Add
```

Дождаться добавление host по SNMP
Проверить в LAtest data собранные данные по SNMP