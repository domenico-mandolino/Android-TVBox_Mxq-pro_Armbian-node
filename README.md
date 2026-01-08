# MXQ Pro (S905W) – Armbian Linux Node

Ce dépôt documente la transformation d’un boîtier TV Android MXQ Pro, basé sur un SoC Amlogic S905W, en un nœud Linux headless destiné à un usage homelab / réseau.

À l’origine conçu pour exécuter Android TV, ce type de matériel est aujourd’hui largement obsolète pour son usage initial. L’objectif de ce projet est de revaloriser ce boîtier en l’intégrant dans une infrastructure personnelle orientée services réseau, en particulier comme futur point d’accès VPN.

---

## Ce dépôt s’inscrit dans une démarche pédagogique et pratique, visant à :

- comprendre les contraintes des architectures ARM low-cost,

- manipuler les mécanismes de boot (u-boot, device tree),

- diagnostiquer et résoudre des problèmes système réels,

- documenter un processus technique de bout en bout.

Le système retenu est Armbian (Debian Bookworm), choisi pour sa stabilité, sa compatibilité avec les usages serveur et sa cohérence avec le reste du homelab (notamment un serveur Proxmox documenté dans un dépôt séparé).

---

## Le projet couvre :

l’identification du matériel (S905W),

les différentes méthodes de boot et de flash possibles,

le choix de l’OS en fonction des objectifs futurs,

les difficultés rencontrées lors de l’installation,

la résolution de problèmes critiques (alimentation, boot, SSH),

l’obtention d’un accès distant fonctionnel et stable.

L’ensemble du travail présenté ici correspond à un retour d’expérience complet.
Les captures d’écran, photos du matériel et étapes détaillées sont regroupées dans un document PDF complémentaire, publié séparément.

Ce dépôt constitue la première étape d’un projet plus large.

--- 

# TV Box → Linux Node  Sécurisation de l’accès SSH (UFW, Fail2ban)


Ce dépôt documente la **sécurisation d’un nœud Linux headless** issu du recyclage d’une TV box Android basée sur un SoC Amlogic (S905W).

Après la mise en place fonctionnelle du système (Armbian / Debian), l’objectif de ce travail est de transformer un accès distant par défaut, peu sécurisé, en une **configuration robuste, cohérente et adaptée à un usage réseau réel** dans un environnement de type homelab.

---

### Objectifs de la documentation

Cette documentation vise à :

- sécuriser l’accès SSH (suppression de root, clés, port non standard),
- réduire la surface d’attaque réseau,
- limiter le bruit lié aux scans automatisés,
- mettre en place une protection active contre les attaques par force brute,
- conserver une configuration simple, lisible et maintenable.

L’approche retenue privilégie les **bonnes pratiques classiques**, éprouvées, sans sur-ingénierie.

---

### Périmètre couvert

Le dépôt couvre les points suivants :

- désactivation de l’accès SSH en tant que `root`,
- authentification SSH par clé (Ed25519),
- changement du port SSH par défaut,
- configuration du pare-feu UFW (politique restrictive),
- désactivation d’IPv6 au niveau UFW,
- mise en place de Fail2ban (jail `sshd`),
- notifications locales via Postfix (*local only*),
- validation et tests fonctionnels.

Les aspects suivants sont volontairement **hors périmètre** :

- journalisation centralisée,
- supervision (Prometheus / Grafana),
- VPN (WireGuard / OpenVPN),
- installation sur eMMC.

Ces sujets feront l’objet de dépôts ou de documents séparés.

---

### Contexte technique

- Matériel : TV box Android Amlogic S905W (MXQ Pro ou équivalent)
- OS : Armbian (Debian Bookworm)
- Usage : nœud réseau léger, accès distant, futur VPN
- Environnement : homelab

---

### Public visé

Cette documentation s’adresse à :

- étudiants en systèmes et réseaux,
- administrateurs débutants ou intermédiaires,
- utilisateurs souhaitant recycler du matériel ARM à bas coût,
- passionnés de homelab cherchant une base saine et réaliste.

Un minimum de familiarité avec Linux et la ligne de commande est supposé.

---

### Philosophie

> Un système correctement sécurisé n’est pas celui qui fait le plus de bruit,  
> mais celui qui **expose peu**, **trace ce qu’il bloque**,  
> et **reste compréhensible six mois plus tard**.

---

### État du projet

- ✔ Accès SSH sécurisé
- ✔ Pare-feu opérationnel
- ✔ Protection active en place
- ✔ Système prêt pour une intégration VPN ultérieure

---

### Licence

Documentation fournie à des fins pédagogiques.  
Libre d’utilisation, d’adaptation et de redistribution.



