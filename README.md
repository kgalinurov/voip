---
description: Канальный драйвер  chan_pjsip в Asterisk
---

# Введениие

В первые CHAN\_PJSIP был представлен в 12 версии Asterisk. Окончательно поддержка была представлена широким массам в версии 13. Однако до сих пор многие избегают его использования. Почему? Думаю что он многом кажется излишне сложным. Но после прочтения данной документации, думаю все станет значительно яснее.

## ЗАЧЕМ ?



Многие спрашивают зачем? Ведь был простой и удобный chan\_sip. К сожалению chan\_sip имеет целый ряд недостатков

* chan\_sip имеет монолитную архитектуру. Содержит более 10 строчек кода.
* Проблемы с производительностью
* Проблемы с добавлением новых возможностей.

Думаю администратор asterisk рано или поздно сталкивался как минимум с двумя ограничениями chan\_sip.

1. В случае нескольких регистраций от одного провайдера все они попадают в один контекст
2.  Отсутствие множественной регистрации

Вообщем на AsterDevConf 2012 [http://lists.digium.com/pipermail/asterisk-dev/2012-November/057512.html](http://lists.digium.com/pipermail/asterisk-dev/2012-November/057512.html) было принято решение, что дальше так жить нельзя и нужно с этим что-то делать. Так как устаревший chan\_sip сдерживает дальнейшее развитие. Был выполнен обзор возможных решений \([https://wiki.asterisk.org/wiki/display/AST/SIP+Stack+Research](https://wiki.asterisk.org/wiki/display/AST/SIP+Stack+Research)\). И по итогу в качестве основы для нового канального драйвера sip был выбран pjsip \([https://wiki.asterisk.org/wiki/display/AST/New+SIP+channel+driver](https://wiki.asterisk.org/wiki/display/AST/New+SIP+channel+driver)\) от проекта [https://www.pjsip.org](https://www.pjsip.org)



