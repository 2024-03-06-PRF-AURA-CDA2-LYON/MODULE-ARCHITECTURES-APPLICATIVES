# TP4 : Machines virtuelles et conteneurs

1. **Machines virtuelles :**

Une machine virtuelle (VM) est un environnement d'exploitation logiciel émulant un système informatique complet avec ses propres ressources matérielles virtualisées (CPU, RAM, disque, carte réseau, etc.). Chaque machine virtuelle dispose de son propre système d'exploitation complet et isolé, comme s'il s'agissait d'un véritable ordinateur physique.

**Exemples de technologies de virtualisation :**

- **VMware vSphere/ESXi :** Pionnier de la virtualisation d'entreprise, VMware propose une suite complète de produits de virtualisation.
- **Microsoft Hyper-V :** Solution de virtualisation intégrée aux systèmes d'exploitation Windows Server.
- **Oracle VirtualBox :** Hyperviseur de virtualisation gratuit et open-source pour plusieurs systèmes d'exploitation hôtes.
- **KVM (Kernel-based Virtual Machine) :** Solution de virtualisation intégrée au noyau Linux, utilisée dans de nombreuses distributions.

**Contextes d'utilisation :**

- **Consolidation des serveurs :** Exécuter plusieurs machines virtuelles sur un seul serveur physique pour optimiser l'utilisation des ressources.
- **Environnements de développement et de test :** Créer des environnements isolés pour le développement et les tests d'applications.
- **Compatibilité des applications :** Exécuter des applications anciennes ou incompatibles avec le système d'exploitation hôte dans une machine virtuelle dédiée.
- **Sécurité et isolement :** Isoler des services ou applications sensibles dans des machines virtuelles distinctes pour des raisons de sécurité.

2. **Conteneurs (comme Docker) :**

Les conteneurs sont une forme de virtualisation au niveau du système d'exploitation, plutôt qu'au niveau matériel comme les machines virtuelles. Un conteneur partage le noyau du système d'exploitation hôte, mais offre un environnement isolé et dédié pour exécuter des applications.

**Différences avec les machines virtuelles :**

- **Légers et efficaces :** Les conteneurs sont plus légers que les machines virtuelles, car ils ne nécessitent pas de système d'exploitation complet, ce qui les rend plus rapides à démarrer et à provisionner.
- **Utilisation des ressources :** Les conteneurs partagent les ressources du système d'exploitation hôte, ce qui permet une meilleure utilisation des ressources matérielles.
- **Portabilité :** Les conteneurs sont très portables, car ils encapsulent l'application et toutes ses dépendances dans une image légère et autonome.
- **Isolation :** Les conteneurs offrent un niveau d'isolation suffisant pour la plupart des applications, bien que moindre que celui des machines virtuelles.

**Contextes d'utilisation :**

- **Déploiement d'applications :** Les conteneurs facilitent le déploiement d'applications dans différents environnements, car ils encapsulent toutes les dépendances nécessaires.
- **Environnements de développement :** Les développeurs peuvent utiliser des conteneurs pour créer des environnements de développement cohérents et reproductibles.
- **Microservices :** Les conteneurs sont souvent utilisés pour déployer et gérer des architectures de microservices, chaque service étant encapsulé dans un conteneur distinct.
- **Intégration continue et déploiement continu (CI/CD) :** Les conteneurs s'intègrent bien dans les pipelines CI/CD modernes.

3. **Reverse Proxy vs Forward Proxy :**

**Reverse Proxy :**

Un reverse proxy est un serveur intermédiaire qui se situe entre les clients (navigateurs web, applications, etc.) et les serveurs d'application back-end. Son rôle principal est de recevoir les requêtes des clients, de les transférer aux serveurs back-end appropriés, et de renvoyer les réponses aux clients.

Exemples d'utilisation :

- **Équilibrage de charge :** Répartir le trafic entrant entre plusieurs serveurs back-end pour améliorer les performances et la disponibilité.
- **Sécurité :** Masquer les adresses IP des serveurs back-end en les gardant à l'intérieur du réseau privé, réduisant ainsi la surface d'attaque.
- **Mise en cache :** Mettre en cache les réponses des serveurs pour réduire la charge et améliorer les temps de réponse.
- **Compression :** Compresser les réponses pour réduire la bande passante utilisée.
- **Routage et répartition du trafic :** Acheminer les requêtes vers les serveurs appropriés en fonction de règles prédéfinies.

Exemples de reverse proxies populaires : Nginx, Apache HTTP Server, HAProxy, Microsoft IIS Application Request Routing.

**Forward Proxy :**

Un forward proxy, également appelé proxy client, est un serveur intermédiaire qui se situe entre les clients (navigateurs web, applications, etc.) et les serveurs externes (sites web, services en ligne, etc.). Son rôle est de transférer les requêtes des clients vers les serveurs externes au nom de ces clients.

Exemples d'utilisation :

- **Contrôle d'accès :** Filtrer ou bloquer l'accès à certains sites web ou services en fonction de politiques prédéfinies.
- **Mise en cache :** Mettre en cache les réponses des serveurs externes pour réduire la bande passante et améliorer les temps de réponse.
- **Anonymat :** Masquer les adresses IP des clients pour préserver leur anonymat en ligne.
- **Contournement de restrictions géographiques :** Accéder à des contenus ou services restreints dans certaines régions en passant par un proxy situé dans une région autorisée.

Exemples de forward proxies populaires : Squid, Microsoft Forefront Threat Management Gateway, Zscaler Internet Access.

4. **Caching :**

Le caching est une technique d'optimisation des performances qui consiste à stocker temporairement des données fréquemment utilisées dans un emplacement de stockage rapide et facilement accessible. Cela permet de réduire la latence et la charge sur les serveurs d'origine en évitant de devoir récupérer les mêmes données à chaque requête.

Dans le contexte web, le caching peut être implémenté à différents niveaux :

- **Caching côté client :** Les navigateurs web mettent en cache les ressources (HTML, CSS, JavaScript, images, etc.) pour réduire le nombre de requêtes au serveur lors des futures visites.
- **Caching côté serveur :** Les serveurs web ou les reverse proxies peuvent mettre en cache les réponses générées dynamiquement pour les servir plus rapidement lors des prochaines requêtes identiques.
- **Caching côté réseau :** Des dispositifs réseau comme les proxies ou les CDN (Content Delivery Networks) peuvent mettre en cache le contenu à différents emplacements stratégiques pour le rapprocher des utilisateurs finaux.
- **Caching côté base de données :** Les bases de données peuvent mettre en cache les résultats des requêtes fréquemment utilisées pour accélérer les temps de réponse.

Le caching utilise généralement des algorithmes comme LRU (Least Recently Used) ou LFU (Least Frequently Used) pour gérer l'éviction des données obsolètes ou peu utilisées du cache.

Il est important de trouver un équilibre entre les avantages en termes de performances et les défis liés à la cohérence des données, car le contenu mis en cache peut devenir obsolète si les données d'origine changent.
