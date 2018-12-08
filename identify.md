# IDENTIFY

Секция IDENTIFY отвечает за то каким именно образом будут сопоставлены SIP пакеты с endpoint\`ом. Возможны следующие варианты:

* username -  по полю FROM в SIP сообщении.
* ip - по ip адресу источника sip пакета
* anonymous -  данный идентификатор позволяет анонимные гостевые звонки. Аналогично параметру allowguest=yes в chan\_sip.
* auth\_username  - по auth\_username в INVITE
* Unnamed по параметру line в SIP-RURI входящего INVITE \(по line в поле TO\);
* header -по произвольному заголовку в INVITE

По умолчанию порядок в котором происходит сопоставление сип сообщения и endpoint определяется загруженными модулями, а также порядком их загрузки. Но порядок можно переопределить с помощью глобального параметра [`identifier_order`](https://wiki.asterisk.org/wiki/display/AST/Asterisk+13+Configuration_res_pjsip#Asterisk13Configuration_res_pjsip-global_endpoint_identifier_order)

 Доступные в данный момент методы идентификации, можно посмотреть командой:

> **pjsip show identifiers**

```text
aster-node2*CLI> pjsip show identifiers
Identifier Names:   
name not specified  
ip                  
username            
anonymous           
header              
auth_username  
```

По умолчанию данная секция не обязательна к настройке. Ее необходимо использовать в случае более сложных конфигураций. 

{% hint style="info" %}
Более подробно данная секция будет описана дальше
{% endhint %}



