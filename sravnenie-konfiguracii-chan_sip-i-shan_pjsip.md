# Сравнение конфигураций Chan\_sip и Сhan\_pjsip

В Chan\_sip все довольно просто и за конфигурацию отвечал один файл sip.conf. В данном файле у нас есть глобальная секция \(general\) В которой настраиваются общие настройки для sip. А также секции \(пиры\) в которых настраиваются телефоны и транки. Регистрации для провайдеров настраиваются также в секции general.

Вот типовой конфигурационный файл sip.conf

```text
[general]
transport=udp
udpbindaddr=0.0.0.0
externaddr = 12.34.56.78
localnet=192.168.1.0/255.255.255.0
nat=comedia,auto_comedia,rport
register =>7XXXXXXXXXX:PaSSWoRD@multifon.ru:5060/7XXXXXXXXXX

[multifon]
type=peer
context=multifon
defaultuser=79XXXXXXXXX
secret=PaSSWoRD
fromuser=79XXXXXXXXX
host=multifon.ru
fromdomain=multifon.ru
disallow=all
allow=alaw,ulaw
dtmfmode=inband
nat=comedia,auto_comedia,rport
qualify=yes
directrtpsetup=no
directmedia=no
insecure=port,invite

[my_phone]
type = peer
context = local_office
disallow = all
allow = ulaw
host = dynamic
secret = super_secret
qualify = yes
dtmfmode = rfc2833

[friends_internal](!)
type=friend
host=dynamic
context=local_office
disallow=all
allow=ulaw

[demo-alice](friends_internal)
secret=verysecretpassword ; put a strong, unique password here instead

[demo-bob](friends_internal)
secret=othersecretpassword ; put a strong, unique password here instead

```

Все кажется очень просто и понятно.

И тут появляется PJSIP. Настройка одного лишь регистрации выглядит там так:

```text
[multifon]
type = endpoint
aors = multifon
outbound_auth = multifon
context = multifon
 
[multifon]
type = aor
contact = type=aor
contact=sip:7XXXXXXXXXX@multifon.ru:5060
qualify_frequency = 15
 
[multifon]
type = auth
auth_type = userpass
username = 7XXXXXXXXXX
password = PaSSWoRD
 
[multifon]
type = registration
outbound_auth=multifon
server_uri=sip:sbc.megafon.ru
client_uri=sip:7XXXXXXXXXX@multifon.ru
contact_user=7XXXXXXXXXX
transport=transport-udp-nat
 
[multifon]
type = identify
endpoint=multifon
match=193.201.229.35

```

  
 Естественно многие администраторы не поняли что это. Почему секций стало много? Что вообще происходит?

И так сначала ответим на вопрос почему секций стало так много? Если вспомнить архитектуру chan\_pjsip, то станет ясно что каждая секция представляет собой конфигурацию для отдельного модуля. Так например секция registartion -это модуль  res\_pjsip\_outbound\_registration.  А теперь попробуем разобраться что происходит и как с этим жить. 

