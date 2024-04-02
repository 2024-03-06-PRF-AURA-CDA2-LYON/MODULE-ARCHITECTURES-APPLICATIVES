# TP1 : Comprendre le processus de résolution DNS

**Contexte :** En réalité, le processus qui permet à votre navigateur d'identifier l'adresse IP d'un site internet n'est pas aussi simple.

**Consignes :**

1. **Décrivez le processus par lequel votre ordinateur arrive à identifier l'adresse IP publique d'un site internet au travers du DNS.**

   - Expliquez le mécanisme de résolution DNS
   - Expliquez tous les serveurs qui peuvent être impliqués dans le processus de résolution de nom

2. **Précisez le rôle de chaque type de serveur DNS impliqué dans le processus (serveur DNS récursif, etc).**

3. **Fournissez un schéma ou un diagramme illustrant le processus de résolution DNS, en incluant les différents serveurs impliqués et l'ordre dans lequel ils sont consultés.**

4. **Expliquez ce qui se passe lorsqu'un serveur DNS a déjà l'adresse IP correspondante dans son cache, et comment cela peut accélérer le processus de résolution.**

5. **Décrivez brièvement le rôle du fichier hosts local dans le processus de résolution DNS et comment il peut être utilisé pour contourner le processus de résolution DNS habituel.**

6. **Discutez des avantages et des inconvénients de l'utilisation du DNS par rapport à l'utilisation directe des adresses IP pour accéder aux sites web.**

7. **Expliquez les différents algorithmes de load balancing dans le contexte du Web.**
8. **Expliquez comment le DNS peut être utilisé pour équilibrer la charge entre plusieurs serveurs web en utilisant des enregistrements DNS de type Round Robin.**

9. **Décrivez brièvement le processus de résolution DNS inverse (reverse DNS lookup) et son utilité.**

**Livrables :**

- Un rapport détaillé répondant à toutes les consignes ci-dessus
- Un schéma ou un diagramme illustrant le processus de résolution DNS

**Réponse :**

1. **Processus de résolution DNS :**

Le processus de résolution DNS (Domain Name System) permet de traduire un nom de domaine lisible par l'humain (exemple: www.exemple.com) en une adresse IP numérique (exemple: 192.168.1.1) que les machines peuvent comprendre et utiliser pour établir une connexion.

**Mécanisme de résolution DNS :**

Voici les étapes du mécanisme de résolution DNS :

1. Lorsque vous entrez un nom de domaine dans votre navigateur, votre ordinateur vérifie d'abord son fichier hosts local pour voir s'il contient une entrée correspondante.
2. Si le fichier hosts ne contient pas l'entrée, votre ordinateur envoie une requête DNS au serveur DNS récursif configuré (généralement fourni par votre fournisseur d'accès Internet).
3. Le serveur DNS récursif vérifie d'abord son cache pour voir s'il a déjà l'adresse IP correspondante. S'il l'a, il renvoie immédiatement l'adresse IP à votre ordinateur.
4. Si le serveur DNS récursif n'a pas l'adresse IP dans son cache, il entame un processus itératif en interrogeant d'abord les serveurs racine DNS (Root Name Servers).
5. Les serveurs racine renvoient les adresses des serveurs DNS de domaine de premier niveau (Top-Level Domain - TLD) correspondant au domaine demandé (.com, .org, .fr, etc.).
6. Le serveur DNS récursif contacte les serveurs DNS TLD et récupère les adresses des serveurs DNS autoritaires pour le domaine demandé.
7. Le serveur DNS récursif contacte ensuite les serveurs DNS autoritaires pour le domaine demandé et récupère enfin l'adresse IP correspondante.
8. Le serveur DNS récursif renvoie l'adresse IP à votre ordinateur, et stocke l'adresse IP dans son cache pour accélérer les futures résolutions.
9. Votre ordinateur peut désormais utiliser l'adresse IP pour établir une connexion avec le site web demandé.

**Serveurs impliqués dans la résolution DNS :**

- **Serveurs DNS racine (Root Name Servers)** : Ce sont les serveurs de niveau supérieur qui connaissent les adresses des serveurs DNS TLD.
- **Serveurs DNS TLD (Top-Level Domain)** : Ils stockent les informations sur les domaines de premier niveau (.com, .org, .fr, etc.) et connaissent les adresses des serveurs DNS autoritaires pour ces domaines.
- **Serveurs DNS autoritaires** : Ce sont les serveurs faisant autorité pour un domaine spécifique. Ils contiennent les enregistrements DNS avec les adresses IP correspondantes.
- **Serveurs DNS récursifs** : Ils agissent comme des intermédiaires, envoyant des requêtes aux autres serveurs DNS pour résoudre les noms de domaine au nom des clients. Ils mettent en cache les résultats pour accélérer les futures résolutions.

2. **Rôle des différents serveurs DNS :**

- **Serveur DNS récursif :** C'est le serveur DNS utilisé par les clients (ordinateurs, smartphones, etc.) pour résoudre les noms de domaine. Il interroge les autres serveurs DNS de manière récursive jusqu'à obtenir l'adresse IP finale. Il met en cache les résultats pour accélérer les futures résolutions.

- **Serveurs DNS racine :** Ils contiennent les informations sur les serveurs DNS de domaine de premier niveau (TLD) et guident les requêtes DNS vers les serveurs DNS TLD appropriés.

- **Serveurs DNS TLD :** Ils stockent les informations sur les domaines de premier niveau (com, org, fr, etc.) et connaissent les adresses des serveurs DNS autoritaires pour ces domaines.

- **Serveurs DNS autoritaires :** Pour un domaine donné, ces serveurs contiennent les enregistrements DNS avec les adresses IP correspondantes. Ils font autorité pour ce domaine.

3. **Schéma du processus de résolution DNS :**

```
                    +-----------------------+
                    |     Serveurs racine   |
                    +-----------------------+
                                |
                                |
                    +-----------------------+
                    | Serveurs DNS TLD      |
                    +-----------------------+
                                |
                                |
                    +-----------------------+
                    | Serveurs DNS          |
                    | autoritaires          |
                    +-----------------------+
                                |
                                |
                    +-----------------------+
                    | Serveur DNS récursif |
                    +-----------------------+
                                |
                                |
                    +-----------------------+
                    | Client (ordinateur,  |
                    | smartphone, etc.)    |
                    +-----------------------+
```

Le processus de résolution suit le chemin suivant :

1. Le client envoie une requête DNS à son serveur DNS récursif.
2. Le serveur DNS récursif interroge les serveurs racine pour obtenir les adresses des serveurs DNS TLD correspondants.
3. Le serveur DNS récursif interroge les serveurs DNS TLD pour obtenir les adresses des serveurs DNS autoritaires pour le domaine demandé.
4. Le serveur DNS récursif interroge les serveurs DNS autoritaires pour obtenir l'adresse IP finale.
5. Le serveur DNS récursif renvoie l'adresse IP au client et met en cache le résultat.

6. **Cache des serveurs DNS :**

Lorsqu'un serveur DNS a déjà l'adresse IP correspondante dans son cache, il peut immédiatement renvoyer cette adresse IP au client sans avoir à effectuer toutes les étapes de résolution DNS. Cela accélère considérablement le processus de résolution DNS en évitant les recherches inutiles auprès d'autres serveurs.

Les serveurs DNS mettent en cache les résultats des résolutions DNS pendant une durée limitée (déterminée par le champ "Time to Live" ou TTL dans les enregistrements DNS). Lorsque le TTL expire, le serveur DNS doit effectuer une nouvelle résolution pour obtenir les informations à jour.

5. **Rôle du fichier hosts local :**

Le fichier hosts est un fichier texte local présent sur la plupart des systèmes d'exploitation. Il permet d'associer manuellement des noms d'hôtes à des adresses IP, en contournant le processus de résolution DNS standard.

Avant d'envoyer une requête DNS, le système d'exploitation vérifie d'abord le fichier hosts pour voir s'il contient une entrée correspondante au nom de domaine demandé. Si c'est le cas, il utilisera l'adresse IP spécifiée dans le fichier hosts au lieu d'effectuer une résolution DNS.

Cela peut être utile dans certains cas, comme le débogage ou le blocage d'accès à certains sites web. Cependant, il est généralement recommandé de ne pas trop modifier le fichier hosts, car cela peut entraîner des conflits et des problèmes de résolution DNS.

6. **Avantages et inconvénients de l'utilisation du DNS :**

**Avantages :**

- **Facilité d'utilisation :** Les noms de domaine lisibles sont plus faciles à mémoriser et à utiliser que les adresses IP numériques.
- **Flexibilité :** Les enregistrements DNS peuvent être modifiés pour refléter les changements d'adresse IP sans avoir à mettre à jour tous les clients individuellement.
- **Équilibrage de charge :** Le DNS peut être utilisé pour répartir le trafic entre plusieurs serveurs, augmentant ainsi la disponibilité et les performances.
- **Gestion centralisée :** Les enregistrements DNS sont gérés de manière centralisée, ce qui facilite leur mise à jour et leur maintenance.

**Inconvénients :**

- **Overhead :** Le processus de résolution DNS ajoute une étape supplémentaire avant d'établir une connexion, ce qui peut entraîner un léger retard.
- **Dépendance :** Si le service DNS est indisponible, les utilisateurs ne pourront pas accéder aux sites web par leur nom de domaine.
- **Sécurité :** Le DNS peut être vulnérable à certaines attaques, comme le cache poisoning ou la redirection de domaine.

7. **Algorithmes de load balancing dans le contexte du Web :**

Les algorithmes de load balancing sont utilisés pour répartir le trafic web entre plusieurs serveurs, dans le but d'améliorer les performances, la disponibilité et la résilience de l'application.

Voici quelques algorithmes couramment utilisés :

- **Round Robin :** Les requêtes sont distribuées de manière séquentielle et cyclique entre les différents serveurs.
- **Least Connections :** Les requêtes sont envoyées vers le serveur ayant le moins de connexions actives à un instant donné.
- **IP Hash :** Les requêtes sont acheminées vers un serveur spécifique en fonction d'un hachage de l'adresse IP du client, garantissant que le même client accède toujours au même serveur (utile pour la persistance des sessions).
- **URL Hash :** Similaire à l'IP Hash, mais le hachage est effectué sur l'URL demandée plutôt que sur l'adresse IP du client.
- **Weighted Round Robin :** Une variante de Round Robin où chaque serveur se voit attribuer un poids différent, permettant de répartir le trafic de manière inégale en fonction des capacités des serveurs.
- **Least Response Time :** Les requêtes sont envoyées vers le serveur ayant le temps de réponse le plus rapide, basé sur des mesures de performance en temps réel.

8. **Équilibrage de charge avec le DNS Round Robin :**

Le DNS Round Robin est une technique d'équilibrage de charge qui utilise le système DNS pour répartir le trafic entre plusieurs serveurs web.

Voici comment cela fonctionne :

1. Pour un nom de domaine donné, le serveur DNS autoritaire contient plusieurs enregistrements A (ou AAAA pour IPv6) pointant vers différentes adresses IP de serveurs web.
2. Lorsqu'un client effectue une résolution DNS pour ce domaine, le serveur DNS ne renvoie pas toutes les adresses IP d'un coup, mais les distribue de manière cyclique (round-robin) à chaque nouvelle requête.
3. Ainsi, le premier client obtiendra la première adresse IP, le deuxième client la deuxième adresse IP, et ainsi de suite. Une fois que toutes les adresses IP ont été distribuées, le serveur DNS recommence depuis le début.
4. Le client se connecte alors à l'adresse IP renvoyée par le serveur DNS, répartissant ainsi le trafic entre les différents serveurs web.

Bien que simple à mettre en œuvre, le DNS Round Robin présente certaines limites, comme l'impossibilité de prendre en compte la charge réelle des serveurs ou de gérer les pannes de manière dynamique. Des solutions plus avancées d'équilibrage de charge, comme des load balancers dédiés, sont souvent préférées pour les environnements à haute disponibilité.

9. **Résolution DNS inverse (reverse DNS lookup) :**

La résolution DNS inverse, également appelée "reverse DNS lookup", est le processus inverse de la résolution DNS standard. Au lieu de traduire un nom de domaine en adresse IP, elle traduit une adresse IP en nom de domaine correspondant.

Ce processus est utile dans plusieurs cas :

- **Identification de l'expéditeur :** Lors de la réception d'un e-mail ou d'une connexion réseau, la résolution DNS inverse peut être utilisée pour identifier le nom d'hôte associé à l'adresse IP de l'expéditeur.
- **Validation d'adresses IP :** Elle permet de vérifier si une adresse IP donnée correspond bien au nom d'hôte attendu, ce qui peut aider à détecter les éventuelles usurpations d'identité.
- **Débogage et dépannage :** La résolution DNS inverse peut aider les administrateurs réseau à identifier les hôtes et les services associés à une adresse IP spécifique.

Pour effectuer une résolution DNS inverse, les serveurs DNS utilisent des enregistrements spéciaux appelés "enregistrements PTR" (Pointer Record) dans la zone DNS inverse correspondant au sous-réseau de l'adresse IP. Ces enregistrements PTR mappent une adresse IP à un nom de domaine.
