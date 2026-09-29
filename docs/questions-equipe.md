# Questions à traiter avec Mingo et les développeurs

Répondre à ces points avant de publier l'application et compléter les autres pages avec les réponses vérifiées.

| Sujet | Question / décision | Responsable |
| --- | --- | --- |
| AWS | Quel compte, quelle région, quels ID d'instance/volume/Elastic IP et quel groupe de sécurité ? | Mingo / infrastructure |
| Projet | Où est le dépôt applicatif et qui peut le fusionner avec cette documentation ? | Développeur |
| Stack | Quels langages, versions, commandes de build et services ? | Développeur |
| Base | Quel moteur, quelles migrations, quel volume de données et quelle persistance ? | Développeur |
| Entrée web | Quel domaine, qui gère le DNS et les certificats HTTPS ? | Équipe |
| Configuration | Quelles variables et où stocker les secrets ? | Équipe |
| Livraison | Qui déploie, avec quelle fréquence et par quel mécanisme ? | Équipe |
| Accès | Qui a besoin d'AWS, de SSH, de Docker et de sudo ? | Mingo / infrastructure |
| Disponibilité | Quelle charge attendue, quelle tolérance à l'arrêt et quels besoins de montée en charge ? | Produit |
| Reprise | Quelles données sauvegarder, quel RPO/RTO et qui teste la restauration ? | Produit / infrastructure |
| Budget | Confirmer la région, les tarifs, le trafic, les snapshots et les alertes budgétaires. | Mingo / infrastructure |

## Décisions de départ

- Démarrer avec une seule instance EC2 et Docker Compose, sous réserve que la charge et les exigences de disponibilité le permettent.
- Décrire web, API et base comme des **services séparés dans Compose**, si cette structure correspond à l'application. L'expression « un conteneur global » reçue initialement reste à clarifier avec le développeur.
- Reporter les choix de proxy, base de données, CI/CD, sauvegarde et accès au moment où l'équipe fournira les contraintes réelles.
