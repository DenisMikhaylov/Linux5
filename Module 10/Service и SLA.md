Материалы
URL Service and SLA create
https://www.youtube.com/watch?v=5N5uK4vJsAY


Добавляем теги к хостам

```
Host: Gate
  Tags
  Name: Monitoring
  Value: Gate

Host: Zabbix
  Tags
  Name: Monitoring

  Value: zabbix

Host: Windows
 Tags
  Name: Monitoring
  Value: windows

Host: ya.ru
 Tags
  Name: zabbix
  Value: Site

Host: google.com
 Tags
  Name: zabbix
  Value: Site
```
Создание Service 

```
Services-> services
в верхнем правом углу нажать Edit
Create service
  Name: Monitoring
  Tags:
    Name: zabbix
    Value: monitoring
  Advanced configuration: check
  Additional rules:
    add...
      Set status to High
      Contion: if at least n% of child servicesa have Status status or above
      N 50%
      Status: Warning
      Add
  Add
```

Зайти в Monitoring

```
Create service
Name: Site
  Tags:
    Name: zabbix
    Value: site
Problem Tags
  Name: zabbix
  Operation: equals
  Value: Site
Add
```

```
Create service
Name Server host
  Tags:
    Name: zabbix
    Value: host
  Additional rules:
    add...
      Set status to Disaster
      Contion: if at least n child servicesa have Status status or above
      N 2
      Status: Warning
      Add
Add
```
Зайти в Server host

```
Create service
Name: Gate
  Tags:
    Name: zabbix host
    Value: gate
Problem Tags
  Name: Monitoring
  Operation: equals
  Value: Gate
Add
```
```
Create service
Name: Zabbix
  Tags:
    Name: zabbix host
    Value: zabbix
Problem Tags
  Name: Monitoring
  Operation: equals
  Value: zabbix
Add
```
```
Create service
Name: Windows
  Tags:
    Name: zabbix host
    Value: window
Problem Tags
  Name: Monitoring
  Operation: equals
  Value: windows
Add
```
Создание SLA

```
Services-> SLA

Create SLA
  Name: Monitoring
  SLO: 90%
  Reporting period: Daily
  Schedule: Custom
    9:00-19:00
  Service tags
    name: zabbix
    Value: monitoring

    name: zabbix
    Value: site

    name: zabbix
    Value: host


```

```
Services-> SLA

Create SLA
  Name: Monitoring
  SLO: 95%
  Reporting period: weeks
  Schedule: Custom
    9:00-19:00
  Service tags
    name: zabbix
    Value: monitoring

    name: zabbix
    Value: site

    name: zabbix
    Value: host


```

Просмотр отчета
```
Services-> SLA report
Выбрать SLA 
```


