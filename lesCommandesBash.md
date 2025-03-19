# Commandes bash (sans catégorie pour l'instant)


#### ls -l   ls -lb
#### ip address add 172.16.8.16/24 dev enp0s8
#### ip link set dev eno0s8 up
#### chmod
#### chown
#### lsblk  fdisk -l
#### ```useradd user_name```

#### en PS : ```New-LocalUser "nom_utilisateur" -Password (ConvertTo-SecureString "mot_de_passe" -AsPlainText -Force)```


#### ```cat /etc/passwd```
liste des users

#### en PS : ```Get-LocalUser```

#### ```sudo usermod -aG nom_groupe nom_utilisateur```
ajouter user à un groupe

#### en PS : ```Add-LocalGroupMember -Group "nom_groupe" -Member "nom_utilisateur"```



#### ```ps aux```
afficher processus en cours

#### en PS ``` Get-Process ```



#### ```netstat -tulnp```

Affiche toutes les connexions réseau actives sur le système, incluant les ports TCP et UDP, ainsi que les applications qui les utilisent (-t pour TCP, -u pour UDP, -l pour écouter, -n pour afficher les adresses et ports numériques, -p pour afficher les PID des processus).

#### en PS : ```netstat -an```

Affiche les connexions réseau actives avec leurs adresses et ports, mais sans lier les applications aux connexions.

#### ```df -h```

 Affiche l'espace disque utilisé et disponible sur les partitions, avec des valeurs lisibles pour l'humain (-h pour "human-readable").

#### en PS : ``` Get-PSDrive```


#### monter partition

sudo ```mount /dev/sdX1 /mnt```

en PS : ```Mount-DiskImage -ImagePath "C:\chemin\vers\image.iso"```

#### installer syst fichier ext 4 sur une partition

```mkfs.ext4 /dev/sdX1```


#### activer swap

sudo ```swapon /dev/sdX1```

#### GetEventLog -LogName ...

Sur Linux, les journaux système sont souvent consultés via des fichiers comme /var/log/syslog ou avec la commande journalctl pour les systèmes utilisant systemd.

``` journalctl -xe ```

Affiche les journaux système les plus récents, avec des informations détaillées sur les erreurs (-xe pour les logs d'erreurs et les messages détaillés).

en PS : ```Get-EventLog -LogName "Application"```

Affiche les événements du journal des applications sous Windows. Tu peux remplacer "Application" par d'autres noms de journaux, tels que "System" ou "Security".


#### 

