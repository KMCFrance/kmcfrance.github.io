# Outils des événements — CMK France

**En ligne : https://kmcfrance.github.io/** (dépôt `kmcfrance.github.io`)

Ce dépôt contient :

- `index.html` : le hub, c'est-à-dire la page d'accueil des outils. Il ne stocke rien.
- `evenements/` : **les fiches événement**, la seule source des informations propres à chaque événement (voir `evenements/LISEZMOI.md`).
- `commun/fiche.js` : le lecteur de fiche, partagé par tous les outils.

## Les dépôts

| Dépôt | Adresse | Rôle |
|---|---|---|
| `kmcfrance.github.io` | `/` | Hub, fiches, lecteur commun |
| `app` | `/app/?evt=<id>` | App mobile des participants + `admin.html` |
| `liens` | `/liens/admin.html?evt=<id>` | Liens de streaming personnels |
| `badges` | `/badges/?evt=<id>` | Badges PDF (listing lu dans le navigateur) |
| `cd2026-Appmobile`, `cd2026-liens`, `cd2026-creation_badge` | | **Outils de CD2026, figés** : on n'y touche plus jusqu'à la fin de la Célébration |

Quand l'adresse ne contient pas `?evt=`, les outils ouvrent l'événement « courant » indiqué dans `evenements/index.json`.

## Mettre à jour

- **Un événement** : modifier sa fiche `evenements/<id>/fiche.json` sur GitHub (icône crayon → Commit). Tous les outils suivent en 1 à 2 minutes.
- **Le hub** : remplacer `index.html`.

## Plus tard : adresse maison (ex. `outils.kadampafrance.org`)

Il suffit d'une seule manipulation, sur ce dépôt. Tous les outils suivent, et GitHub redirige les anciennes adresses `github.io`.

1. DSI : ajouter un enregistrement DNS **CNAME** `outils` → `kmcfrance.github.io`.
2. **Settings → Pages → Custom domain** : `outils.kadampafrance.org`, puis **Enforce HTTPS**.
3. Avant de faire le changement :
   - exporter les réglages de l'outil badges ;
   - vérifier dans Google Cloud que les clés API Firebase ne sont pas limitées à `kmcfrance.github.io` ;
   - choisir une période sans événement.
4. Ne plus jamais retirer ce domaine ensuite.
