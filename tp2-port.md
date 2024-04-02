# TP2 : Ports de service

1. **Importance des numéros de ports :**

Les numéros de ports jouent un rôle crucial dans la communication réseau en permettant d'identifier de manière unique les différents services ou applications sur un même hôte. Sans les numéros de ports, il serait impossible de distinguer, par exemple, le trafic HTTP (web) du trafic SSH (accès à distance sécurisé) sur un même serveur.

Les ports permettent essentiellement de :

- **Multiplexer plusieurs services sur une seule adresse IP :** Plusieurs services peuvent fonctionner simultanément sur un même hôte, chacun associé à un port différent.
- **Identifier le destinataire correct :** Lorsqu'un paquet arrive sur un hôte, le numéro de port permet d'acheminer le paquet vers le service ou l'application approprié.
- **Permettre plusieurs connexions simultanées :** Les ports permettent également de différencier plusieurs connexions simultanées pour un même service, chacune associée à un port différent.

2. **Numéros de ports courants :**

Voici quelques numéros de ports couramment utilisés pour les protocoles et services populaires :

- **HTTP (HyperText Transfer Protocol) :** Port 80
- **HTTPS (HTTP Sécurisé) :** Port 443  
- **FTP (File Transfer Protocol) :** Port 21
- **SSH (Secure Shell) :** Port 22
- **SMTP (Simple Mail Transfer Protocol) :** Port 25
- **DNS (Domain Name System) :** Port 53
- **DHCP (Dynamic Host Configuration Protocol) :** Ports 67 et 68
- **TFTP (Trivial File Transfer Protocol) :** Port 69
- **POP3 (Post Office Protocol v3) :** Port 110
- **NTP (Network Time Protocol) :** Port 123
- **IMAP (Internet Message Access Protocol) :** Port 143
- **SNMP (Simple Network Management Protocol) :** Ports 161 et 162
- **LDAP (Lightweight Directory Access Protocol) :** Port 389
- **RDP (Remote Desktop Protocol) :** Port 3389

Il est important de noter que les ports inférieurs à 1024 sont généralement réservés pour les services système et nécessitent des privilèges d'administrateur pour y avoir accès. Les ports supérieurs à 1024 peuvent être utilisés par des applications utilisateur.