# Infrastructure AWS

## Serveur

| Élément | Valeur |
| --- | --- |
| Nom de l'instance | `EC2-INS-DEV` |
| ID de l'instance | `i-067ff6830b1e522ab` |
| Adresse IP publique | `3.19.165.82` |
| Type | EC2 `t3.large` (2 vCPU, 8 Gio de RAM) |
| Système | Ubuntu 24.04 |
| Disque | EBS `gp3`, 30 Gio selon la configuration demandée ; à confirmer sur l'instance |
| Docker | Docker Engine et Docker Compose installés à partir de la [documentation officielle](https://docs.docker.com/engine/install/ubuntu/) |
| Ports exposés | SSH `22/TCP` et HTTPS `443/TCP`, selon la configuration communiquée |
| Région AWS | À confirmer dans la console |
| Elastic IP | Vérifier si `3.19.165.82` est associée en tant qu'Elastic IP |

Limiter l'accès SSH dans le groupe de sécurité aux adresses IP des personnes autorisées. Le fait que le port HTTPS soit ouvert ne confirme pas encore qu'un site ou un certificat y est configuré.

## Coût mensuel estimé

Hypothèse provisoire : région `ca-central-1`, instance allumée 730 h/mois, disque gp3 de 30 Gio et une adresse IPv4 publique. **La région réelle et les tarifs sont à valider dans [AWS Pricing Calculator](https://calculator.aws/).**

| Ressource | Estimation USD/mois |
| --- | ---: |
| EC2 `t3.large` | 67,74 |
| EBS gp3 30 Gio | 2,64 |
| IPv4 publique | 3,65 |
| **Total indicatif** | **74,03** |

Taxes, trafic sortant, sauvegardes et éventuels crédits CPU T3 supplémentaires ne sont pas inclus. Sources : [EC2](https://aws.amazon.com/ec2/pricing/on-demand/), [EBS](https://aws.amazon.com/ebs/pricing/) et [IPv4](https://aws.amazon.com/vpc/pricing/).