# Pjsip transport

Transport представляет собой точку входа и выхода  в Asterisk. Данная функциональность предоставляется модулем res\_pjsip.so  В транспорте определяется протокол, ip адрес, шифрование. Настройки описываются соответственно в секции с _**type=transport.**_ Имя секции может быть произвольным. 

```text
[simpletrans]
type=transport
protocol=udp
bind=0.0.0.0
```

Давайте разберем основные настройки транспорта.

### Протокол \(protocol\)

Определяет протокол по которому возможна работа. PJSIP поддерживает следующие протоколы:

* UDP
* TCP
* TLS
* WS

{% hint style="info" %}
Настройка TLS и WSS будет рассмотрена позднее
{% endhint %}

#### IP адрес \(bind\)

Определяет интерфейс на котором будет слушать PJSIP и с которого будут отправляться сообщения SIP. Может быть как ipv4 так и ip6v.   

```text
[transport-auto-ipv6]
type=transport
protocol=udp
bind=::
```

Это минимальная конфигурация транспорта.

После запуска asterisk проверяем что транспорт сконфигурирован и активен командой 

```text
asterisk16> pjsip list transports

Transport:  <TransportId........>  <Type>  <cos>  <tos>  <BindAddress....................>
==========================================================================================

Transport:  transport-udp             udp      0      0  0.0.0.0:5060

Objects found: 1

asterisk16> pjsip show transports

Transport:  <TransportId........>  <Type>  <cos>  <tos>  <BindAddress....................>
==========================================================================================

Transport:  transport-udp             udp      0      0  0.0.0.0:5060

Objects found: 1

*CLI> 
```

 Также можно проверить что сокет активен командой **`ss`**

```text
ss -u -a -p
UNCONN      0      0            *:sip            *:*         users:(("asterisk",pid=10202,fd=9))
```

Или более привычным способом

```text
 netstat -lptun
 udp        0      0 0.0.0.0:5060            0.0.0.0:*                           10202/asterisk 
```

Также в секции транспорт находятся часть настроек для работы с NAT Позже мы к ним вернемся.



