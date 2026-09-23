# Fiches événement

Chaque événement a **une fiche** : `/evenements/<id>/fiche.json`, avec ses images dans le même dossier.
Tous les outils la lisent : le hub, l'app mobile (`/app/`), l'outil liens (`/liens/`) et les badges (`/badges/`).

- `index.json` contient la liste des événements et l'événement **courant**, celui qui s'ouvre sans `?evt=` dans l'adresse.
- `_modele/` est une fiche vierge à copier. Les dossiers qui commencent par `_` ne sont jamais utilisés.
- `cd2026/` est la fiche de la Célébration du Dharma 2026. Elle sert de référence et d'archive.

## Préparer un nouvel événement (ex. `printemps2027`)

1. **Fiche.** Copiez `_modele/` en `printemps2027/`, puis remplissez `fiche.json`. Ne gardez pas « _modele » dans le champ `id` : mettez-y le nom du dossier.
2. **Images.** Déposez dans le dossier :
   - `visuel.jpg` : bandeau de l'app, environ 800 × 330 px ;
   - `fond.jpg` ou `chateau-bg.jpg` : fond de la page streaming.
   Les noms doivent correspondre au bloc `images` de la fiche.
3. **Firebase.** Créez une base Realtime Database pour l'app et un projet Firestore pour les liens (voir `/app/LISEZMOI.md` et `/liens/LISEZMOI.md`). Collez leurs adresses et clés dans les blocs `app` et `streaming` de la fiche.
4. **Liste des événements.** Dans `index.json`, ajoutez l'événement à `evenements`. Le jour où il doit devenir celui par défaut, mettez son id dans `courant`.
5. **Vérification.** Ouvrez le hub avec `https://kmcfrance.github.io/?evt=printemps2027`, puis chaque outil depuis ses tuiles.
6. **App.** Dans l'admin de l'app, cliquez sur « Initialiser depuis la fiche » pour reprendre le programme, les infos et le café. Ensuite, tout se modifie dans l'admin, comme d'habitude.
7. **Liens.** Dans l'admin des liens, créez le mot de passe à la première connexion, puis cliquez sur « Pré-remplir les séances ».
8. **Après l'événement (RGPD).** Supprimez les participants du streaming, ou le projet Firebase, après la date `streaming.finDiffere` plus un délai raisonnable.

## Les champs de la fiche

Les textes bilingues s'écrivent `{ "fr": "…", "en": "…" }`.

Les dates s'écrivent `AAAA-MM-JJ` et les heures `HH:MM`, en heure de Paris.

| Champ | Rôle |
|---|---|
| `id`, `code` | Identifiant (nom du dossier) et code court (ex. `CD2026`) |
| `nom`, `nomAffiche`, `sousTitre` | Nom, nom sur l'écran d'accueil de l'app (`<br>` autorisé), thème |
| `debut`, `fin` | Premier et dernier jour. Les onglets de jours de l'app en découlent. |
| `lieu`, `enseignant`, `pageWeb`, `presentation` | Informations générales |
| `charte` | Couleurs : `principale`, `principaleFoncee`, `principaleClaire`, `secondaire`, `secondaireClaire`, `accent` |
| `images` | `visuel` (bandeau de l'app, page streaming), `visuelHD`, `fond` |
| `app.firebaseUrl` | Base Realtime Database de l'app |
| `app.url` / `app.admin` | **À laisser vide pour un nouvel événement** : les outils génériques `/app/?evt=…` sont alors utilisés. Seule la fiche CD2026 les remplit, pour pointer vers ses anciens outils. |
| `streaming.firebase`, `streaming.emailjs` | Configuration Firebase (web) et EmailJS de l'outil liens |
| `streaming.finDiffere`, `expediteur`, `contact` | Fin du différé, nom de l'expéditeur, adresse de contact |
| `programme[]` | `jour`, `debut`, `fin`, `titre`, `type` (`teaching`, `meditation`, `ceremony`, `meal`, `practical`), `desc`, `badge`. Ajouter `seance` (nom) pour que l'élément devienne une séance de streaming. |
| `infos[]` | Rubriques « Infos pratiques » de l'app (`contenu` en HTML simple) |
| `cafe.carte[]`, `cafe.horaires[]`, `cafe.note` | Carte et horaires du café. Si le bloc est absent, l'onglet est masqué. |
| `boutique[]` | Articles de la boutique |
| `datesCles[]` | Frise et compte à rebours du hub |
| `liens[]`, `contacts[]` | Liens utiles et contacts du hub (adresses de service seulement : la page est publique) |

**Ne jamais mettre de mot de passe ni de donnée personnelle dans une fiche** : elle est publique.
