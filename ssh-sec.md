# quelques notes sur l'utilisation de com sécurisée en ssh

ssh-keygen

ssh-keygen -b 4096

root@itc-serveur-01:~# ls -al .ssh  (vérif les clés dans le repertoire perso)

ssh-copy-id utilisateur@adresse_ip_distante   OU   ssh-copy-id -i ~/.ssh/id_rsa_groupeServeurA.pub root@192.168.240.132

### Renforcer la sécurité SSH

sudo nano /etc/ssh/sshd_config

![image](https://github.com/user-attachments/assets/d90c4e18-0223-4809-84f7-0df2d6aaf2f8)
