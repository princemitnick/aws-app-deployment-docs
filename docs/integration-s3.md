# Stockage de fichiers AWS S3 — Projet MEKS

Documentation technique d'intégration du stockage d'objets **Amazon S3** pour l'application **MEKS** (photos de profil utilisateurs et justificatifs de dépôts bancaires).

---

## 1. Architecture & Buckets disponibles

L'infrastructure repose sur **deux buckets S3 distincts et 100 % privés** (*Block All Public Access* activé) :

| Bucket S3 | Usage | Sécurité & Rétention |
| :--- | :--- | :--- |
| `meks-user-avatars` | Photos de profil des utilisateurs | Privé, chiffrement SSE-S3, CORS activé |
| `meks-bank-proofs` | Preuves de dépôts bancaires (fichiers sensibles) | Privé, chiffrement SSE-S3, **Versioning activé**, CORS activé |

> **Important :** Aucun fichier n'est accessible via une URL publique S3 directe. Tous les envois (*uploads*) et affichages (*downloads*) doivent passer par des **URLs présignées (*Presigned URLs*)** générées temporairement par le backend.

---

## 2. Configuration de l'environnement (`.env`)

Copiez le fichier `.env.example` vers `.env` et renseignez les identifiants transmis par l'équipe infrastructure (ne jamais commiter le fichier `.env`) :

```env
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=VOTRE_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY=VOTRE_SECRET_ACCESS_KEY

S3_BUCKET_AVATARS=meks-user-avatars
S3_BUCKET_PROOFS=meks-bank-proofs