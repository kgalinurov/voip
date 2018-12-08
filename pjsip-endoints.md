# PJSIP ENDOINTS

Что такое pjsip endpoint? С точки зрения Asterisk pjsipendpoint представляет собой конфигурационную сущность представляющую собой  абонента \(клиента\) либо описывающего asterisk, как клиента некого сип провайдера.  

Таким образом можно рассматривать ENDPOINT как некий контейнер который содержит настройки специфичные для данного клиента/провайдера.

 Весь входящий и исходящий SIP трафик сопоставляется с ENDPOINT. После сопоставления происходит применение настроек специфичных для клиента/провайдера. Например в данной секции настраиваются медиа кодеки. Также в данной секции указывается контекст для входящих звонков.



Пример секции endpoints

```text
[vasya]
type=endpoint
context=from-external
disallow=all
allow=ulaw
transport=transport-udp
auth=7000
aors=7000
```

Посмотреть сконфигурированные endpoint\`ы можно посмотреть командой:

```text
aster-node2*CLI> pjsip show endpoints
Endpoint:  <Endpoint/CID.....................................>  <State.....>  <Channels.>
    I/OAuth:  <AuthId/UserName...........................................................>
        Aor:  <Aor............................................>  <MaxContact>
      Contact:  <Aor/ContactUri..........................> <Hash....> <Status> <RTT(ms)..>
  Transport:  <TransportId........>  <Type>  <cos>  <tos>  <BindAddress..................>
   Identify:  <Identify/Endpoint.........................................................>
        Match:  <criteria.........................>
    Channel:  <ChannelId......................................>  <State.....>  <Time.....>
        Exten: <DialedExten...........>  CLCID: <ConnectedLineCID.......>
==========================================================================================

 Endpoint:  vasya                                                Unavailable   0 of inf
  Transport:  transport-udp             udp      0      0  0.0.0.0:5060
```

Детальную информацию по endpoint'у можно получить командой  

> **pjsip show endpoint &lt;ENDPOINT\_NAME&gt;**

```text

aster-node2*CLI> pjsip show endpoint vasya

 Endpoint:  <Endpoint/CID.....................................>  <State.....>  <Channels.>
    I/OAuth:  <AuthId/UserName...........................................................>
        Aor:  <Aor............................................>  <MaxContact>
      Contact:  <Aor/ContactUri..........................> <Hash....> <Status> <RTT(ms)..>
  Transport:  <TransportId........>  <Type>  <cos>  <tos>  <BindAddress..................>
   Identify:  <Identify/Endpoint.........................................................>
        Match:  <criteria.........................>
    Channel:  <ChannelId......................................>  <State.....>  <Time.....>
        Exten: <DialedExten...........>  CLCID: <ConnectedLineCID.......>
==========================================================================================

 Endpoint:  vasya                                                Unavailable   0 of inf
  Transport:  transport-udp             udp      0      0  0.0.0.0:5060


 ParameterName                      : ParameterValue
 =========================================================
 100rel                             : yes
 accept_multiple_sdp_answers        : false
 accountcode                        : 
 acl                                : 
 aggregate_mwi                      : true
 allow                              : (ulaw)
 allow_overlap                      : true
 allow_subscribe                    : true
 allow_transfer                     : true
 aors                               : 7000
 asymmetric_rtp_codec               : false
 auth                               : 7000
 bind_rtp_to_media_address          : false
 bundle                             : false
 call_group                         : 
 callerid                           : <unknown>
 callerid_privacy                   : allowed_not_screened
 callerid_tag                       : 
 connected_line_method              : invite
 contact_acl                        : 
 context                            : from-external
 cos_audio                          : 0
 cos_video                          : 0
 device_state_busy_at               : 0
 direct_media                       : true
 direct_media_glare_mitigation      : none
 direct_media_method                : invite
 disable_direct_media_on_nat        : false
 dtls_auto_generate_cert            : No
 dtls_ca_file                       : 
 dtls_ca_path                       : 
 dtls_cert_file                     : 
 dtls_cipher                        : 
 dtls_fingerprint                   : SHA-256
 dtls_private_key                   : 
 dtls_rekey                         : 0
 dtls_setup                         : active
 dtls_verify                        : No
 dtmf_mode                          : rfc4733
 fax_detect                         : false
 fax_detect_timeout                 : 0
 follow_early_media_fork            : true
 force_avp                          : false
 force_rport                        : true
 from_domain                        : 
 from_user                          : 
 g726_non_standard                  : false
 ice_support                        : false
 identify_by                        : username,ip
 inband_progress                    : false
 incoming_mwi_mailbox               : 
 language                           : 
 mailboxes                          : 
 max_audio_streams                  : 1
 max_video_streams                  : 1
 media_address                      : 
 media_encryption                   : no
 media_encryption_optimistic        : false
 media_use_received_transport       : false
 message_context                    : 
 moh_passthrough                    : false
 moh_suggest                        : default
 mwi_from_user                      : 
 mwi_subscribe_replaces_unsolicited : no
 named_call_group                   : 
 named_pickup_group                 : 
 notify_early_inuse_ringing         : false
 one_touch_recording                : false
 outbound_auth                      : 
 outbound_proxy                     : 
 pickup_group                       : 
 preferred_codec_only               : false
 record_off_feature                 : automixmon
 record_on_feature                  : automixmon
 refer_blind_progress               : true
 rewrite_contact                    : false
 rpid_immediate                     : false
 rtcp_mux                           : false
 rtp_engine                         : asterisk
 rtp_ipv6                           : false
 rtp_keepalive                      : 0
 rtp_symmetric                      : false
 rtp_timeout                        : 0
 rtp_timeout_hold                   : 0
 sdp_owner                          : -
 sdp_session                        : Asterisk
 send_diversion                     : true
 send_pai                           : false
 send_rpid                          : false
 set_var                            : 
 srtp_tag_32                        : false
 sub_min_expiry                     : 0
 subscribe_context                  : 
 suppress_q850_reason_headers       : false
 t38_udptl                          : false
 t38_udptl_ec                       : none
 t38_udptl_ipv6                     : false
 t38_udptl_maxdatagram              : 0
 t38_udptl_nat                      : false
 timers                             : yes
 timers_min_se                      : 90
 timers_sess_expires                : 1800
 tone_zone                          : 
 tos_audio                          : 0
 tos_video                          : 0
 transport                          : transport-udp
 trust_id_inbound                   : false
 trust_id_outbound                  : false
 use_avpf                           : false
 use_ptime                          : false
 user_eq_phone                      : false
 voicemail_extension                : 
 webrtc                             : no
```

 

