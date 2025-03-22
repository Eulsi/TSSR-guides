# quelques notes sur l'utilisation de com sécurisée en ssh
```bash
ssh-keygen
```
```bash
ssh-keygen -b 4096
```
```bash
root@itc-serveur-01:~# ls -al .ssh  (vérif les clés dans le repertoire perso)
```

```bash
ssh-copy-id utilisateur@adresse_ip_distante   //OU   ssh-copy-id -i ~/.ssh/id_rsa_groupeServeurA.pub root@192.168.240.132
```

### Renforcer la sécurité SSH

sudo nano /etc/ssh/sshd_config

![image](https://github.com/user-attachments/assets/d90c4e18-0223-4809-84f7-0df2d6aaf2f8)



### **Étapes pour configurer SSH sans partage de clés (Windows 10 et Linux)**

1. **Activer SSH sur Windows 10**  
   - Ouvrez les **Paramètres** > **Applications** > **Fonctionnalités optionnelles**.
   - Cliquez sur **Ajouter une fonctionnalité** et installez **Client OpenSSH** et **Serveur OpenSSH**.
   - Démarrez le service SSH :
     ```powershell
     Start-Service sshd
     Set-Service -Name sshd -StartupType Automatic
     ```

2. **Configurer SSH sur Windows 10**  
   - Ouvrez PowerShell en tant qu'administrateur et générez une paire de clés SSH :
     ```powershell
     ssh-keygen -t ed25519
     ```
   - Copiez la clé publique dans le fichier autorisé :
     ```powershell
     cat C:\Users\votre_utilisateur\.ssh\id_ed25519.pub | Out-File -FilePath C:\Users\votre_utilisateur\.ssh\authorized_keys -Encoding utf8
     ```

3. **Se connecter depuis Debian vers Windows 10**  
   Sur la machine Debian, utilisez la commande suivante pour vous connecter à Windows :
   ```bash
   ssh utilisateur_windows@adresse_ip_windows
   ```

4. **Se connecter depuis Debian vers d'autres appareils Linux**  
   Si l'authentification par mot de passe est activée, utilisez simplement :
   ```bash
   ssh utilisateur@adresse_ip_distante
   ```

---

### **Mesures de sécurité supplémentaires**

1. **Changer le port SSH par défaut (22)**  
   Modifiez le fichier `/etc/ssh/sshd_config` pour utiliser un port personnalisé (ex : 2222) :
   ```bash
   Port 2222
   ```

2. **Utiliser Fail2ban pour bloquer les attaques par force brute**  
   Installez Fail2ban sur les machines Linux :
   ```bash
   sudo apt install fail2ban
   ```
   Configurez-le pour surveiller les tentatives de connexion SSH.

3. **Configurer un pare-feu**  
   Utilisez `ufw` (Uncomplicated Firewall) pour limiter l'accès SSH :
   ```bash
   sudo ufw allow 2222/tcp  # Autoriser le port SSH personnalisé
   sudo ufw enable
   ```

4. **Désactiver les utilisateurs inutiles**  
   Assurez-vous que seuls les utilisateurs nécessaires peuvent se connecter via SSH :
   ```bash
   AllowUsers utilisateur1 utilisateur2
   ```
