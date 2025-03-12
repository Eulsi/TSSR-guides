# Subnetting calculs

## A. Trouver le masque de sous-réseau et le CIDR



## B. Calcul du nombre d'hôtes

  2^(32 - CIDR) -2 = nb hôtes



## C. Trouver l'intervalle dans lequel se trouve la plage d'adresse

  ### Exemple, pour 10.11.128.0/18 
  
  On a 1111 1111 . 1111 1111 . 1100 0000 . 0000 0000
       255.255.192.0  en masque de sous - réseau

  Sur l'octet qui divise le net en subnet, le 3e, il faut calculer sur quelle puissance de 2 nous sommes. 
  Avec 1100 0000 attribuons à chaque bit une échelle de la puissance 2 ( 128 64 32 16 8 4 2 1 ).
  Notre bit s'arrête à 64, ce qui signifie que nous somme sur des intervalles de 64.

  Dans notre cas, 10.11.128.0 , nous avons le 3eme octet à partir duquel se fait la subdivision qui est un multiple de 64.
  L'adresse réseau se situe donc bien à 10.11.128.0 et l'intervalle que prend le subnet se termine 64 blocs plus loin, la dernière adresse étant donc 10.11.191.255.


  ### Autre exemple pour calculer l'intervalle, solution issue de DeepSeek pour un autre exercice :

  **Exercice 4**

1. Nouveau masque : **/26** (255.255.255.192).
   - Chaque sous-réseau aura 64 adresses, dont 62 utilisables pour des hôtes.

2. Plage du 4e sous-réseau : **192.168.10.192 - 192.168.10.255**.


  
Pour déterminer la plage d’adresses du 4e sous-réseau, il faut calculer l'intervalle entre les sous-réseaux. Avec un masque de /27, chaque sous-réseau aura :

2^{(32 - 27)} = 2^5 = 32 adresses

Cela signifie que chaque sous-réseau a 32 adresses, dont 30 adresses utilisables (la première est l'adresse réseau et la dernière est l'adresse de broadcast).

Pour trouver la plage du 4e sous-réseau, on peut suivre ces étapes :

1. **Calculer l'incrément entre les sous-réseaux :** L'incrément est de 32 adresses (puisque chaque sous-réseau a 32 adresses).

2. **Déterminer les adresses réseau de chaque sous-réseau :**
   - **1er sous-réseau :** 192.168.10.0
   - **2e sous-réseau :** 192.168.10.32
   - **3e sous-réseau :** 192.168.10.64
   - **4e sous-réseau :** 192.168.10.96
   - **5e sous-réseau :** 192.168.10.128
   - **6e sous-réseau :** 192.168.10.160

3. **Plage d’adresses du 4e sous-réseau :**
   - **Adresse réseau :** 192.168.10.96
   - **Première adresse utilisable :** 192.168.10.97
   - **Dernière adresse utilisable :** 192.168.10.126
   - **Adresse de broadcast :** 192.168.10.127


