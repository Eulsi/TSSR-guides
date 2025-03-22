# Les outils de config de devices

## commandes des demos custom

* ?
* show ?
* enable
* configure terminal
* commande pour sauter les privilèges pour afficher commandes : do show
* (retour exit, quitte la config terminal)
* show running config
* show interface | include FastEthernet
* show ip interface brief
* show vlan
* Dans configure terminal, changer hostname avec hostname name
* copy running-config startup-config pour permettre les modifications courantes de persister après démarrage. /!\ peut être remplacé par write ou wr
* vérifier les modifs avec show startup-config
* show version pour afficher les paramètres du matériel
* donner un nom de domaine : ip domain-name ceci.local
  (créer un nom de domaine est nécessaire pour implémenter les clés ssh)
* pour sécurité, important de créer un vlan plutôt que de conserver celui par défaut.
* pour créer (dans conf t) : vlan 423
* configurer les interfaces (dans conf t) : interface fastEthernet 0/1
* pour configurer plusieurs interfaces en mm temps : interface range fastEthernet 0/1-24
* pour forcer tous les ports en mode access : ```switchport mode access``` après avoir choisi l'interface
* show running-config pour vérifier qu'elle a bien été placée en switchport mode access (ne pas oublier GigabitEthernet)
* ```show running-config | section int``` permet de filtrer en indiquant le switchport pour chaque interface
* switchport access vlan 423 pour permettre aux interfaces sélectionnées de communiquer depuis ce vlan. (config t et inteface range au préalable)
* le show vlan indique désormais les interfaces à l'intérieur du vlan créé

  ----
  ----

  // pour sortir de l'erreur "Translating ..." créée par une faute de frappe, faire ctrl maj 9

* configurer un vlan
* vlan 99 pour le créer ou y entrrer
* name www pour le renommer
* quitter exit et ```int vlan 99``` pour accéder à son ou ses interfaces
* supprimer un vlan (depuis conf t) : no interface vlan 99
* donner une adresse ip à l'interface d'un vlan (depuis config-if) : ip address 192.168.99.220 255.255.255.0
* show ip interface brief donne un visuel de vérification de la manip
* attribuer une gateway (conf t) : ip default-gateway 192.168.99.254
* vérifier avec show running-config (depuis end)
* pour sécuriser les interfaces puisqu'il y en a 24 d'ouvertes : accéder aux interfaces avec range
* puis faire shutdown, ce qui va les fermer administrativement


-----
-----

#### Recap demo suivante 

* enable
* configure terminal
* hostname
* do show running-config
* ip domain-name yolo.local
* vlan 1xxx --> erreur car ne peut pas créer plus que (1005?)
* do show ip interface brief
* interface range fastEthernet 0/1-24
* switchport mode access
* switch access vlan 3000 (comme il n'existe pas, il va le créer)
* shutdown pour éteindre administrativement tout
* faire la même chose avec le gigabit
* * copy running-config startup-config
* conf t
* vlan 100
* do show vlan
* name NET
* exit
* interface vlan 100
* ip address 10.100.100.252 255.255.255.248
* exit
* ip default-gateway 10.100.100.254


--- sécurité pour pas brancher cable console tranquille sur notre matériel
-------------------------------------------------------------

* dans conf t , utliiser "enable ?" pour voir les options
* enable password *** (mdp)
* no enable password pour le retirer (mais il est vachement visible dans running-config)
* enable algorithm-type sha-256 secret yolo (mdp)   --> sauf que sha 256 fonctionne pas vraiment sur cette version
* donc plutôt utiliser secret (activer le service password encryption depuis conf t)
* service password-encryption
* enable secret yolo (mdp) (et le mdp sera alors caché ou au moins en md5 )


--- ssh et utilisateur admin
-------------------------------------------------------------

* username admin1 secret yolo (mdp)
* 

--- sécuriser la ligne console
-------------------------------------------------------------

(attention au EXEC time-out)

* line console ? (utiliser 0)
* login local
* exec-timeout 3
* end
// après temps écoulé, si branché avec un cable console sur le switch, le terminal pc exigera authentification

---
####♠ récap de démo 18 sécuriser line
* (do) show running-config | section line vty
* choisir les lignes sur lesquelles on ne veut pas de connexion : line vty 5 15
* (dans config-line) : no login
* transport output none (pour empêcher le rebond) (pas clair, à comprendre plus en profondeur)
* 


--- utiliser le ssh
-------------------------------------------------------------

* ip ssh version ? (1 ou 2
* ip ssh version 2
* crypto key gen rsa
* How many bits in the modulus? 2048
* ip ssh time-out 120
* ip ssh authentication-retries 4
*  



--- configurer vty
-------------------------------------------------------------

* line vty 0 2 (ligne virtuelle terminal y)
* (normalement s'ouvre le config-line)
* login local
* exec-timeout 3
* transport input ssh
* 
/!\ voir fin du cours (démo 17 lab réseau étape1 part2) et réf github ci dessous pour reprendre, mais je n'ai pas compris l'intérêt ici.


## Démo 18

* création de VLAN
* création de trunk
* A noter que pour qu'une communication fonctionne entre des appareils séparés par différents switch, il faut que ceux-ci disposent du vlan en question.
* Mais il faut également que les ports dédiés à cette communication soient activés en mode trunk (pour que d'autres vlan puissent passer). Et sur chacun des switch concernés.
* (donc retirer le switchport mode access, retirer le vlan exotique et no shutdown)
* 





# Copie de Rikya

## 1 - Sécurisation des équipements d'interconnexions

<p align="right"><a href="README.md">(Retourner au sommaire)</a></p>

**Description de l'étape :**  
Nous utiliserons un switch pour cet exemple et nous essaierons de réaliser les étapes dans un ordre chronologique logique.

**1 - Nommer l'équipement :**  
`Switch> enable`  
`Switch# configure terminal`  
`Switch(config)# hostname newNameSwitch`

**2 - Attribuer le domaine à l'équipement :**  
**Obligatoire pour créer une clé RSA nécessaire pour utiliser le SSH qu'on implémentera lus tard.**  
`Switch(config)# ip domain-name nonDedomaine.local`

**3 - Créer un VLAN aléatoire pour sortir toutes les interfaces du vlan par défaut :**  
`Switch(config)# vlan 3000`  
`Switch(config-if)# exit`

> Si tu ne parviens pas à créer le vlan 3000 c'est probablement dû au mode "Server" du protocole VTP. Tu peux soit modifier le mode VTP à "Transparent" avec ce que ça implique soit continuer sans tenir compte de l'étape 3 qui ne sera pas bloquante pour la suite.

**4 - Eteindre toutes les interfaces de l'équipement :**  
**Profitons-en avant de commencer la configuration des interfaces pour n'oublier aucune interface.**  
`Switch(config)# interface range FastEthernet 0/1-24`  
`Switch(config-if-range)# switchport mode access`  
`Switch(config-if-range)# switchport access vlan 3000`  
`Switch(config-if-range)# shutdown`  
`Switch(config-if-range)# exit`  
`Switch(config)# interface range GigabitEthernet 0/1-2`  
`Switch(config-if-range)# switchport mode access`  
`Switch(config-if-range)# switchport access vlan 3000`  
`Switch(config-if-range)# shutdown`  
`Switch(config-if-range)# exit`  

**5 - Créer un VLAN d'administration pour accéder depuis le réseau à l'équipement :**  
`Switch(config)# vlan 100`  
`Switch(config-vlan)# name NomVlan100`  
`Switch(config-vlan)# exit`  
`Switch(config)# interface vlan 100`  
`Switch(config-if)# ip address 10.100.100.252 255.255.255.248`  
`Switch(config-if)# no shutdown`  
`Switch(config-if)# exit`  
`Switch(config)# ip default-gateway 10.100.100.254`  

**6 - Configurer un mdp sur le "Mode Privilégié" (Privileged EXEC Mode) :**  
`Switch(config)# enable algorithm-type sha-256 secret motDePasse`  
> Si sha-256 non implémenté dans l'équipement alors commande suivante :

`Switch(config)# enable secret motDePasse`  

**7 - Implémentation du SSH :**  
`Switch(config)# username nonUser privilege 15 algorithm-type sha-256 secret motDePasse`  
> Si sha-256 non implémenté dans l'équipement alors commande suivante :

`Switch(config)# username nonUser secret motDePasse`  
`Switch(config)# ip ssh version 2`  
`Switch(config)# crypto key generate rsa`  
`Switch(config)# 2048`  
`Switch(config)# ip ssh time-out 120`  
`Switch(config)# ip ssh authentication-retries 3`  

**8 - Sécurisation des connexions :**  
`Switch(config)# line console 0`  
`Switch(config-line)# login local`  
`Switch(config-line)# exec-timeout 5`  
`Switch(config-line)# exit`  
`Switch(config)# line vty 0 15`  
`Switch(config-line)# login local`  
`Switch(config-line)# exec-timeout 5`  
`Switch(config-line)# transport input ssh`  
`Switch(config-line)# transport output none`  
`Switch(config-line)# end`  

**9 - Sauvegarde de la configuration :**  
`Switch# copy running-config startup-config`  

<a href="README.md">(Retourner au sommaire)</a>
