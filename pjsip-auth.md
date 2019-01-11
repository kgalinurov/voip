# PJSIP AUTH

Секция pjsip auth отвечает за авторизацию sip устройства \(абонента\) на сервере Asterisk. Данная секция также отвечает авторизацию сервера Asterisk на стороне SIP провайдера \(при совершении вызовов или при регистрации\). Несколько endpoint или registration могут иметь одну секцию авторизации. пароль может быть задан как в открытом виде, так и в md5.

```text
[auth6001]
type=auth
auth_type=userpass
password=6001
username=6001
```

```text
[auth6001]
type=auth
auth_type=md5
md5_cred=51e63a3da6425a39aecc045ec45f1ae8
username=6001
```



