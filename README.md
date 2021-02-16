# Mémo de commandes utiles pour administrateur système :technologist:

L'objectif de ce mémo est de recenser les commandes que j'utilise au quotidien :grinning:

## Windows

### Configuration du NTP :watch:
Ces lignes permettent de configurer la synchro NTP, de rédémarrer le service et de resynchroniser l'horloge.
```
w32tm /config /manualpeerlist:"IP-DU-SERVEUR-NTP" /syncfromflags:manual /update

net stop w32time
net start w32time

w32tm /resync
```

## Vcenter (6.7)

Rédémarrer tous les services d'un Vcenter VMware
```
service-control --stop --all
service-control --start --all
```
Arrêter le service Update Manager sur vCenter
```
service-control --stop vmware-updatemgr
```

## Linux

### Configuration du NTP :watch:

Modification du fichier de configuration :memo:
```
//etc/ntp.conf

server IP-DU-SERVEUR-NTP

```
Redémarrage du service ntp
```
systemctl restart ntpd.service
```
Vérification du fonctionnement :memo:
```
ntpq -p
date
```
