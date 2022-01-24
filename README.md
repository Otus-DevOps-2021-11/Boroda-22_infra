# Boroda-22_infra
Boroda-22 Infra repository

Bastion IP = 84.201.172.23,10.128.0.27 vm2-grey-ip = 10.128.0.14

Соедниение с хостом2 на серый IP через белый:

    ssh -A -J appuser@84.201.172.23 appuser@10.128.0.14
    ssh -i ~/.ssh/appuser -J appuser@84.201.172.23 appuser@10.128.0.14

Соединение через SSH-proxy:
    ~/.ssh/config:
    
    ### Main Host
    Host bastion_white
      HostName 84.201.172.23
      User appuser

    ### Second Host
    Host vm2-grey-ip
      HostName 10.128.0.14
      ProxyJump bastion_white
