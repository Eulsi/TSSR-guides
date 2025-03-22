# Concepts & Terminologie


* Sysprep (& ckpt 4 -oobe -generalization)
* les couches du modèles OSI
* les principaux protocoles et leur situation dans les couches (chkpt 4)
* les protocoles et leurs ports
* NAT
* différence entre addgroup et groupadd en bash
* ICMP OSPF
* revoir les éléments de la trame ethernet
* protocoles ICMP ARP
* RARP
* IPV6 unicast lien local / unicast locale, uniques, globales / anycast ...
* Les notions de conteneurisation
* Différences entre virtualisation, emulation et simulation
* DNS records
* CNAME
* SOA
* MX
* PTR
* NS
* LDAP
* Notions de l'AD  (ADGLP ou AGDLP?)
* JIT
* JEA
* topologie de réplication
* LAPS
* FSMO et ses 5 rôles
* EGP
* IGP
* Microsoft Tiering Model
* matrice des flux
* OSPF RIPD (contexte demo custom)
* stateless firewall / pare feu personnel / pare feu applicatif
* nslookup
* Clés GPG
* différences entre licences libre, free, open source
* les sauvegardes incrémentielles, différentielles etc... (voir les 2 corrections chkpt 4)
* PRA (sauvegardes?)
* concepts en VOIP
* RTC/RNIS
* PABX
* PBX
* IPBX FXS FXO
* Switch POE
* adaptateur ATA
* SIP et ports 5060 et 5061
* Asterisk
* Wificours WPA2
* CCMP
* CCMA/CP (?)
* WPS
* NIDS
* mode promiscuité
* port monitoring
* matrice de flux
* HIDS
* snort
* KIPS (les IPS)
* Fail2ban
* IDS
* TCPflood
* les ACL
* les RFC (? lesquels connaître?)
* Outils ITSM
* les pratiques ITIL
* VLAN
* Trunk
* protocole ceph (contexte gestion centralisée)
* principes de la haute disponibilité (PRA PCA , Failover, load balancing...)
* cisco, que sont les ACL


---

**Sysprep (& ckpt 4 -oobe -generalization)**  
Sysprep est un outil Windows pour préparer une image système en supprimant les informations spécifiques à une machine. Les options `-oobe` (Out-of-Box Experience) et `-generalization` permettent de redémarrer en mode configuration utilisateur et de généraliser l'image pour un déploiement sur plusieurs machines.

---

**Les couches du modèle OSI**  
Le modèle OSI comporte 7 couches : Physique, Liaison, Réseau, Transport, Session, Présentation et Application. Chaque couche a un rôle spécifique dans la communication réseau.

---

**Les principaux protocoles et leur situation dans les couches (chkpt 4)**  
- **Couche Application** : HTTP, FTP, DNS  
- **Couche Transport** : TCP, UDP  
- **Couche Réseau** : IP, ICMP, OSPF  
- **Couche Liaison** : Ethernet, ARP  

---

**Les protocoles et leurs ports**  
- HTTP : 80, HTTPS : 443  
- FTP : 21, SSH : 22, DNS : 53  
- SMTP : 25, RDP : 3389  

---

**NAT (Network Address Translation)**  
Le NAT permet de traduire des adresses IP privées en adresses IP publiques pour accéder à Internet. Il est souvent utilisé dans les routeurs.

---

**Différence entre addgroup et groupadd en bash**  
- `addgroup` : Commande plus conviviale pour ajouter un groupe (utilisée sur Debian/Ubuntu).  
- `groupadd` : Commande de bas niveau pour créer un groupe (utilisée sur RedHat/CentOS).  

---

**ICMP (Internet Control Message Protocol)**  
ICMP est utilisé pour envoyer des messages d'erreur et des informations de contrôle dans un réseau (ex : ping).

---

**OSPF (Open Shortest Path First)**  
OSPF est un protocole de routage dynamique qui utilise l'algorithme Dijkstra pour trouver le chemin le plus court dans un réseau.

---

**Revoir les éléments de la trame Ethernet**  
Une trame Ethernet contient : Préambule, Adresse MAC source/destination, Type, Données, et FCS (Frame Check Sequence).

---

**Protocoles ICMP ARP**  
- **ICMP** : Gestion des erreurs et contrôle.  
- **ARP** (Address Resolution Protocol) : Associe une adresse IP à une adresse MAC.

---

**RARP (Reverse Address Resolution Protocol)**  
RARP permet à une machine de trouver son adresse IP à partir de son adresse MAC (inverse d'ARP).

---

**IPv6 Unicast (lien local, locale, globale, anycast)**  
- **Lien local** : Communication sur le même lien (préfixe `fe80::`).  
- **Locale** : Communication dans un site.  
- **Globale** : Adresse publique routable.  
- **Anycast** : Envoi de données au nœud le plus proche.

---

**Les notions de conteneurisation**  
La conteneurisation permet d'isoler des applications dans des environnements légers et portables (ex : Docker).

---

**Différences entre virtualisation, émulation et simulation**  
- **Virtualisation** : Crée des machines virtuelles sur un matériel physique.  
- **Émulation** : Imite un système complet (ex : émulateur de console).  
- **Simulation** : Reproduit le comportement d'un système sans en être une copie exacte.

---

**DNS Records**  
- **CNAME** : Alias pour un nom de domaine.  
- **SOA** (Start of Authority) : Informations sur la zone DNS.  
- **MX** (Mail Exchange) : Serveur de messagerie.  
- **PTR** (Pointer) : Résolution inverse IP vers nom.  
- **NS** (Name Server) : Serveur DNS autoritaire.

---

**LDAP (Lightweight Directory Access Protocol)**  
LDAP est un protocole pour accéder et gérer des annuaires (ex : Active Directory).

---

**Notions de l'AD (ADGLP ou AGDLP?)**  
ADGLP (ou AGDLP) est une méthode pour gérer les permissions dans Active Directory : Compte (Account) -> Groupe Global -> Groupe Local -> Permissions.

---

**JIT (Just-In-Time)**  
Le JIT est une méthode pour accorder des accès temporaires et à la demande, souvent utilisée pour la sécurité.

---

**JEA (Just Enough Administration)**  
JEA est un modèle de sécurité PowerShell qui limite les permissions des utilisateurs au strict nécessaire.

---

**Topologie de réplication**  
La topologie de réplication définit comment les données sont copiées entre serveurs (ex : Active Directory).

---

**LAPS (Local Administrator Password Solution)**  
LAPS gère les mots de passe des administrateurs locaux de manière centralisée et sécurisée.

---

**FSMO et ses 5 rôles**  
FSMO (Flexible Single Master Operations) dans Active Directory comprend 5 rôles : Schema Master, Domain Naming Master, RID Master, PDC Emulator, et Infrastructure Master.

---

**EGP (Exterior Gateway Protocol)**  
EGP est utilisé pour échanger des informations de routage entre différents systèmes autonomes (ex : BGP).

---

**IGP (Interior Gateway Protocol)**  
IGP est utilisé pour le routage interne dans un système autonome (ex : OSPF, RIP).

---

**Microsoft Tiering Model**  
Modèle de sécurité Microsoft qui classe les ressources en niveaux (Tier 0, 1, 2) pour limiter les accès.

---

**Matrice des flux**  
Une matrice des flux représente les interactions entre les composants d'un système (ex : réseau).

---

**OSPF RIP (contexte demo custom)**  
OSPF et RIP sont des protocoles de routage. OSPF est plus efficace pour les grands réseaux, RIP pour les petits.

---

**Stateless firewall / pare-feu personnel / pare-feu applicatif**  
- **Stateless** : Filtre les paquets sans suivre les connexions.  
- **Personnel** : Protège un seul ordinateur.  
- **Applicatif** : Filtre les trafics au niveau applicatif.

---

**nslookup**  
Outil pour interroger les serveurs DNS et résoudre les noms de domaine en adresses IP.

---

**Clés GPG**  
GPG (GNU Privacy Guard) utilise des clés publiques et privées pour chiffrer et signer des données.

---

**Différences entre licences libre, free, open source**  
- **Libre** : Liberté d'utilisation, modification, et distribution.  
- **Free** : Gratuit mais pas nécessairement libre.  
- **Open Source** : Code source disponible, mais pas toujours libre.

---

**Les sauvegardes incrémentielles, différentielles, etc.**  
- **Incrémentielle** : Sauvegarde uniquement les changements depuis la dernière sauvegarde.  
- **Différentielle** : Sauvegarde les changements depuis la dernière sauvegarde complète.

---

**PRA (Plan de Reprise d'Activité)**  
Le PRA est un plan pour restaurer les systèmes après une panne, souvent basé sur des sauvegardes.

---

**Concepts en VoIP**  
La VoIP (Voice over IP) permet de transmettre la voix via des réseaux IP (ex : SIP, RTP).

---

**RTC/RNIS**  
- **RTC** (Réseau Téléphonique Commuté) : Réseau téléphonique traditionnel.  
- **RNIS** (Réseau Numérique à Intégration de Services) : Réseau numérique pour voix et données.

---

**PABX / PBX / IPBX**  
- **PABX** : Autocommutateur téléphonique privé.  
- **PBX** : Version moderne du PABX.  
- **IPBX** : PBX basé sur IP.

---

**FXS / FXO**  
- **FXS** : Interface pour connecter des téléphones.  
- **FXO** : Interface pour connecter à une ligne téléphonique.

---

**Switch POE**  
Un switch POE (Power over Ethernet) fournit de l'électricité via le câble Ethernet pour alimenter des appareils (ex : caméras IP).

---

**Adaptateur ATA**  
Un adaptateur ATA (Analog Telephone Adapter) permet de connecter des téléphones analogiques à un réseau VoIP.

---

**SIP et ports 5060 et 5061**  
SIP (Session Initiation Protocol) est un protocole pour établir des sessions VoIP. Les ports 5060 (non chiffré) et 5061 (chiffré) sont utilisés.

---

**Asterisk**  
Asterisk est un logiciel open source pour créer des serveurs VoIP.

---

**WiFi (WPA2, CCMP, WPS)**  
- **WPA2** : Protocole de sécurité WiFi.  
- **CCMP** : Protocole de chiffrement utilisé par WPA2.  
- **WPS** : Wi-Fi Protected Setup pour simplifier la connexion.

---

**NIDS (Network Intrusion Detection System)**  
Un NIDS surveille le trafic réseau pour détecter des activités suspectes.

---

**Mode promiscuité**  
En mode promiscuité, une interface réseau capture tous les paquets, pas seulement ceux qui lui sont destinés.

---

**Port monitoring**  
Surveillance des ports réseau pour analyser le trafic et détecter des anomalies.

---

**Matrice de flux**  
Une matrice de flux représente les interactions entre les composants d'un système (ex : réseau).

---

**HIDS (Host-based Intrusion Detection System)**  
Un HIDS surveille les activités sur un hôte spécifique pour détecter des intrusions.

---

**Snort**  
Snort est un outil open source de détection d'intrusions réseau.

---

**KIPS (Kernel-based Intrusion Prevention System)**  
Un KIPS surveille et bloque les activités malveillantes au niveau du noyau.

---

**Fail2ban**  
Fail2ban est un outil pour bannir les adresses IP après plusieurs tentatives de connexion infructueuses.

---

**IDS (Intrusion Detection System)**  
Un IDS détecte les activités suspectes sur un réseau ou un hôte.

---

**TCP flood**  
Une attaque TCP flood consiste à submerger un serveur avec des requêtes TCP pour le rendre indisponible.

---

**Les ACL (Access Control Lists)**  
Les ACL sont des listes de règles pour contrôler l'accès aux ressources réseau.

---

**Les RFC (Request for Comments)**  
Les RFC sont des documents décrivant les standards et protocoles Internet (ex : RFC 791 pour IPv4).

---

**Outils ITSM**  
Les outils ITSM (IT Service Management) aident à gérer les services informatiques (ex : ServiceNow, Jira).

---

**Les pratiques ITIL**  
ITIL (Information Technology Infrastructure Library) est un cadre de bonnes pratiques pour la gestion des services IT.

---

**VLAN**  
Un VLAN (Virtual LAN) segmente un réseau physique en plusieurs réseaux virtuels.

---

**Trunk**  
Un port Trunk transporte le trafic de plusieurs VLANs sur un seul lien.

---

**Protocole Ceph**  
Ceph est un système de stockage distribué et scalable, souvent utilisé pour le cloud.

---

**Principes de la haute disponibilité (PRA, PCA, Failover, Load Balancing)**  
- **PRA** : Plan de reprise d'activité.  
- **PCA** : Plan de continuité d'activité.  
- **Failover** : Basculer vers un système de secours en cas de panne.  
- **Load Balancing** : Répartir la charge entre plusieurs serveurs.

---

**Cisco, que sont les ACL**  
Les ACL (Access Control Lists) chez Cisco sont des listes de règles pour filtrer le trafic réseau.

---
 **RFC**, **ITIL**, ou **Ceph**, plus de recherche




| Protocole | Description (Acronyme) | Port(s) TCP/UDP | Couche(s) OSI |
|-----------|------------------------|-----------------|---------------|
| **HTTP**  | **HyperText Transfer Protocol** : Protocole de communication web pour transférer des données (pages HTML, images, etc.). | TCP 80 | Application |
| **HTTPS** | **HTTP Secure** : Version sécurisée de HTTP utilisant SSL/TLS pour chiffrer les données. | TCP 443 | Application |
| **FTP**   | **File Transfer Protocol** : Protocole pour transférer des fichiers entre un client et un serveur. | TCP 20 (données), 21 (contrôle) | Application |
| **FTPS**  | **FTP Secure** : Version sécurisée de FTP utilisant SSL/TLS. | TCP 989 (données), 990 (contrôle) | Application |
| **SSH**   | **Secure Shell** : Protocole pour accéder et gérer des systèmes à distance de manière sécurisée. | TCP 22 | Application |
| **TFTP**  | **Trivial File Transfer Protocol** : Version simplifiée de FTP sans authentification, souvent utilisé pour le démarrage réseau (PXE). | UDP 69 | Application |
| **SMTP**  | **Simple Mail Transfer Protocol** : Protocole pour envoyer des emails. | TCP 25 | Application |
| **IMAP**  | **Internet Message Access Protocol** : Protocole pour récupérer des emails depuis un serveur. | TCP 143 (IMAP), 993 (IMAPS) | Application |
| **LDAP**  | **Lightweight Directory Access Protocol** : Protocole pour interroger et modifier des services d'annuaire (ex : Active Directory). | TCP 389 (LDAP), 636 (LDAPS) | Application |
| **POP3**  | **Post Office Protocol v3** : Protocole pour récupérer des emails depuis un serveur (téléchargement local). | TCP 110 (POP3), 995 (POP3S) | Application |
| **DNS**   | **Domain Name System** : Protocole pour résoudre des noms de domaine en adresses IP. | UDP 53 (parfois TCP) | Application |
| **NTP**   | **Network Time Protocol** : Protocole pour synchroniser l'heure entre les systèmes. | UDP 123 | Application |
| **ICMP**  | **Internet Control Message Protocol** : Protocole pour envoyer des messages d'erreur et de contrôle (ex : ping). | - (fonctionne sur IP) | Réseau |
| **DHCP**  | **Dynamic Host Configuration Protocol** : Protocole pour attribuer des adresses IP automatiquement. | UDP 67 (serveur), 68 (client) | Application |
| **SNMP**  | **Simple Network Management Protocol** : Protocole pour surveiller et gérer les équipements réseau. | UDP 161 (requêtes), 162 (traps) | Application |
