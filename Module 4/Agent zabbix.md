Установить агента на red os
Установить агента на gate
Установка агента в Windows

Подключитсья к Gate по ssh:

Получить список элементов агента
```
# zabbix_agentd -p
```
```
# zabbix_agentd -p | grep agent.version
```
```
# zabbix_agentd -p | grep vm.memory.size
```
```
# zabbix_agentd -t vm.memory.size[available]
```
```
# cat /proc/meminfo | grep MemAvailable
```
```
# zabbix_agentd -t system.sw.packages
```

Добавить узлы в Zabbix

Не присоединять никакие шаблоны.
Создать простые проверки SSH и RDP для агентов
