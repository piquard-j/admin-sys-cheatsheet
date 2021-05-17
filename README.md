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
### Récupérer le numéro de série en ligne de commandes
```
WMIC BIOS GET SERIALNUMBER
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
## ESXi (<6.0)

Consulter les composants physique du serveur hôte

```
smbiosDump
```
## VMware
Réduire la taille des fichiers d'une VM
```
Dans la VM
vmware-toolbox-cmd disk skrink /
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
remote           refid      st t when poll reach   delay   offset  jitter
=============================================
*IP-DU-SERVEUR IP-DU-SERVEUR  2 u 54 64 377 28.682 -3.649   9.792


date
mardi 16 février 2021, 02:20:53 (UTC+0100)
```
