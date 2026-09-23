# Outils des événements — CMK France

**En ligne : https://kmcfrance.github.io/** (dépôt `kmcfrance.github.io`)

Ce dépôt contient :

- `index.html` : le hub, c'est-à-dire la page d'accueil des outils. Il ne stocke rien.
- `preparer/` : la page **« Préparer un événement »** (`/preparer/`), qui crée et modifie les fiches et les enregistre sur GitHub.
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

- **Un événement** : page **https://kmcfrance.github.io/preparer/** (bouton « Préparer / modifier un événement » du hub). Elle enregistre la fiche, les images et `evenements/index.json` directement sur GitHub. Tous les outils suivent en 1 à 2 minutes.
  - Il faut une fois, sur chaque ordinateur, un **jeton GitHub** *fine-grained* : propriétaire `kmcfrance`, dépôt `kmcfrance.github.io` seulement, permission **Contents : Read and write** (la page explique la marche à suivre). Le jeton reste dans le navigateur et n'est envoyé qu'à `api.github.com` ; la page publique n'en contient aucun. En cas de perte : le supprimer sur GitHub (Settings → Developer settings → Personal access tokens).
  - Sans jeton, la page permet de télécharger les fichiers à déposer à la main.
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
