# PJSIP AORS

PJSIP AORS и PJSIP contact наверное самые сложные для понимания сущности для новичков которые мигрируют с chan sip на pjsip. Для того чтобы понять что такое AOR нужно обратиться к теории SIP вспомнить основные [компоненты сети в SIP](protokol-sip/osnovnye-komponenty-sip-seti.md) и процесс регистрации. В общем случае можно считать что AOR это идентификатор \(sip адрес\) пользователя \(номер телефона\) А Cоntact это идентификатор \(sip адрес\) устройства. И так как у пользователя может быть несколько устройств то и с AOR может быть связано несколько контактов.

```text
[100]
type=aor
max_contacts=1
```

В этом примере мы прописали AOR 100 и подразумеваем, что контакт будет сопоставлен с данным AOR в процессе регистрации. При этом можно зарегистрировать одно устройство.

Кроме того мы можем прописать контакт в явном виде. Это может быть полезно если вы выполняете миграцию абонентов с другой ATC на астериск или абонент находится за шлюзом

```text
[100]
type=aor
contact=sip:200@192.0.2.1:5060
```

Также в случае если у вас транк для исходящей связи можно указать только доменную часть:

```text
[mytrunk]
type=aor
contact=sip:203.0.113.1:5060
```



