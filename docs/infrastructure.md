# Infrastructure et budget

Dernière mise à jour : 29 septembre 2026. Les éléments non contrôlés sont indiqués explicitement.

## Inventaire

| Champ | Valeur / action |
| --- | --- |
| Compte AWS membre de l'organisation | **À RENSEIGNER** : ID ou alias du compte ; ne pas inscrire d'identifiants de connexion |
| Région | **À RENSEIGNER** ; estimation ci-dessous fondée sur `ca-central-1` |
| Instance EC2 | Créée ; **À RENSEIGNER** : ID, nom/tag, zone de disponibilité |
| Type d'instance | `t3.large` : 2 vCPU, 8 Gio |
| AMI / OS | Ubuntu 24.04 annoncé ; version effective à contrôler |
| Volume EBS | `gp3` de 30 Gio prévu ; **À RENSEIGNER** : ID, capacité et chiffrement effectifs |
| Elastic IP | Prévue ; **À RENSEIGNER** : adresse et association à l'instance |
| VPC / sous-réseau / groupe de sécurité | **À RENSEIGNER** après vérification dans EC2 |
| Domaine et DNS | **À RENSEIGNER** |
| Responsable AWS | Mingo ; contact technique de l'instance : **À RENSEIGNER** |

## Réseau et accès à contrôler

- SSH : l'utilisateur initial d'une AMI Ubuntu EC2 est généralement `ubuntu`. L'accès se fait avec la clé privée du `.pem` associé à l'instance : `ssh -i /chemin/vers/cle.pem ubuntu@IP_PUBLIQUE`. La clé reste hors du dépôt.
- Confirmer les personnes qui disposent d'un accès AWS via IAM Identity Center et leurs permission sets. Un accès à la console AWS ne crée pas un compte Linux sur l'instance.
- Vérifier les règles entrantes du groupe de sécurité : TCP 22 limité aux IP administratives nécessaires ; TCP 80/443 lorsque le site est effectivement exposé ; aucun port de base de données ouvert à Internet.
- L'accès au groupe `docker` donne de très larges privilèges sur l'hôte. Décider explicitement si le développeur en a besoin ; un compte Linux dédié et une clé SSH personnelle sont préférables au partage de la clé initiale.
- Confirmer le pare-feu au niveau AWS ainsi que les ports publiés par Compose. Les ports Docker publiés doivent être examinés même si `ufw` est actif ([note officielle Docker](https://docs.docker.com/engine/install/ubuntu/#firewall-limitations)).

**État des accès Linux développeur : À RENSEIGNER.** Ne pas supposer qu'un utilisateur a déjà été créé.

## Estimation mensuelle indicative

Hypothèse de travail discutée avec l'équipe : Linux à la demande, région **Canada (Central) `ca-central-1`**, fonctionnement continu pendant **730 h/mois**, un volume gp3 de **30 Gio**, une IPv4 publique. Tarifs unitaires repris de l'estimation préparatoire ; **à revérifier dans [AWS Pricing Calculator](https://calculator.aws/) après confirmation de la région, des dimensions réelles et des tarifs applicables au compte**.

| Poste | Calcul | Estimation USD/mois |
| --- | ---: | ---: |
| EC2 `t3.large` | 730 h × 0,0928 USD/h | 67,74 |
| EBS `gp3` 30 Gio | 30 × 0,088 USD/Gio-mois | 2,64 |
| Une IPv4 publique / Elastic IP | 730 h × 0,005 USD/h | 3,65 |
| **Total de base** | | **74,03 USD/mois** |

Ce chiffre n'est pas une facture garantie : taxes, trafic sortant, instantanés/sauvegardes, surveillance et crédits CPU excédentaires éventuels des instances T3 peuvent s'ajouter. Vérifier les éventuels avantages contractuels ou crédits AWS dans Billing. Le stockage EBS et l'IPv4 peuvent continuer à coûter même lorsque l'instance est arrêtée, selon les ressources conservées.

Sources pour mise à jour : [EC2 à la demande](https://aws.amazon.com/ec2/pricing/on-demand/), [EBS](https://aws.amazon.com/ebs/pricing/) et [IPv4 publiques VPC](https://aws.amazon.com/vpc/pricing/).
