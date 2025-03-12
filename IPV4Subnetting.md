# Subnetting calculs


## Diviser un réseau en sous réseaux

### Trouver le masque de sous-réseau et le CIDR



### Calcul du nombre d'hôtes

  2^(32 - CIDR) -2 = nb hôtes



### Trouver l'intervalle dans lequel se trouve la plage d'adresse

  Exemple, pour 10.11.128.0/18 
  On a 1111 1111 . 1111 1111 . 1100 0000 . 0000 0000
       255.255.192.0  en masque de sous - réseau

  Sur l'octet qui divise le net en subnet, le 3e, il faut calculer sur quelle puissance de 2 nous sommes. 
  Avec 1100 0000 attribuons à chaque bit une échelle de la puissance 2 ( 128 64 32 16 8 4 2 1 ).
  Notre bit s'arrête à 64, ce qui signifie que nous somme sur des intervalles de 64.

  Dans notre cas, 10.11.128.0 , nous avons le 3eme octet à partir duquel se fait la subdivision qui est un multiple de 64.
  L'adresse réseau se situe donc bien à 10.11.128.0 et l'intervalle que prend le subnet se termine 64 blocs plus loin, la dernière adresse étant donc 10.11.191.255.

