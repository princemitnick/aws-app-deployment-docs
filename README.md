# Déploiement AWS — documentation du projet

Documentation initiale de l'hébergement de l'application. Ce dépôt porte un nom générique afin de pouvoir intégrer ultérieurement ces documents au dépôt de l'équipe de développement.

**État au 29 septembre 2026 :** l'instance EC2 a été créée et Docker Engine ainsi que Docker Compose ont été installés sur Ubuntu à partir de la [procédure officielle Docker](https://docs.docker.com/engine/install/ubuntu/). Le déploiement de l'application, sa configuration et ses sauvegardes restent à documenter et à valider avec l'équipe.

## Repères rapides

| Élément | Information disponible |
| --- | --- |
| Hébergeur | AWS, compte membre de l'organisation de Mingo |
| Serveur | EC2 `t3.large`, 2 vCPU, 8 Gio de RAM |
| Système | Ubuntu 24.04 |
| Stockage prévu | EBS `gp3`, 30 Gio — capacité réelle à vérifier |
| Adresse publique | Elastic IP prévue — association effective à vérifier |
| Conteneurs | Docker Engine et Compose installés ; services applicatifs à définir |
| Région AWS | À confirmer ; `ca-central-1` utilisée uniquement pour l'estimation de coût |

## Lire et compléter

- [Infrastructure et budget](docs/infrastructure.md) : inventaire AWS, réseau, accès et estimation mensuelle.
- [Déploiement](docs/deploiement.md) : contrôles de Docker, architecture cible et procédure à compléter.
- [Exploitation](docs/exploitation.md) : suivi, accès, sauvegardes et incidents.
- [Questions à trancher](docs/questions-equipe.md) : informations nécessaires auprès de Mingo et des développeurs.

Les mentions **À RENSEIGNER** indiquent une information inconnue ou non vérifiée. Ne les remplacer qu'après contrôle dans AWS ou sur le serveur.

## Règles de contribution

1. Décrire l'état réellement constaté avec une date ; placer les souhaits dans « prévu » ou « à faire ».
2. Ne jamais committer de clé `.pem`, fichier `.env`, mot de passe, jeton ou sauvegarde de données. Utiliser un gestionnaire de secrets approuvé par l'équipe.
3. Faire relire les modifications d'accès, de réseau et de sauvegarde avant application.
4. Lorsque le dépôt applicatif sera connu, déplacer ou intégrer ces fichiers dans son répertoire `docs/`, en conservant leur historique si souhaité. Adapter alors les commandes Compose au vrai `compose.yaml` du développeur.

Ce dépôt documente l'environnement ; il ne contient pas encore l'application ni un `compose.yaml` exploitable.
