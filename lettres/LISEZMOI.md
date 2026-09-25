# Lettres KBS

Page : **https://kmcfrance.github.io/lettres/?evt=<id>** (tuile « Lettres KBS » du hub).

Elle produit les lettres automatiques à charger dans KBS, au format **.docx** (KBS n'accepte que ce format). Chaque lettre existe en quatre versions : présentiel et streaming, en français et en anglais.

Lettres de CD2026 : 01 Panier, 02 Arrhes non reçues (annulation en instance), 03 Annulation, 04 Confirmation. Les conditions générales (19) viendront plus tard.

## Principe

- Les **variables KBS** (`[DearOne]`, `[ref]`, `[yourCart]`…) restent telles quelles. KBS les remplace à l'envoi.
- Les **informations de l'événement** s'écrivent `{evenement}`, `{dates}`, `{lienNavettes}`… Elles viennent de la fiche de l'événement (page Préparer). L'onglet **Valeurs** permet de les remplacer pour les lettres seulement.
- Les **textes** sont dans `evenements/<id>/lettres.json`. Le bouton **Enregistrer sur GitHub** utilise le même jeton que la page Préparer. Tant que ce n'est pas enregistré, les modifications restent gardées sur l'ordinateur.

## Nouvel événement

1. Ouvrir `/lettres/?evt=<nouvel id>`.
2. Cliquer **Reprendre ces lettres** (à partir de CD2026, par exemple). Les textes sont copiés, et les nom, dates et liens viennent de la nouvelle fiche.
3. Onglet **Valeurs** : remplir ce qui est en rouge (horaires des navettes, etc.).
4. Onglet **Vérifier et tout télécharger** : corriger les lettres qui ne sont pas « Prête », puis télécharger le .zip.
5. **Enregistrer sur GitHub**.

## Balisage

Le bouton « Aide » de l'éditeur donne la liste complète. En bref :

- `@entete` : en-tête de la lettre.
- `# Titre` : titre de la lettre.
- `## Partie` : partie numérotée.
- `- puce` : ligne à puce.
- `!! alerte` : ligne mise en avant.
- `---` : trait de séparation.
- `@signature` et `@signature-kbs` : signature.
- `@pied` : bas de page.
- `**gras**`, `*italique*` : mise en forme.
- `[texte](adresse)` : lien caché derrière un texte.

## Vérifications automatiques

Une lettre ne peut pas partir tant qu'il reste une **erreur** :

- variable KBS inconnue ou mal écrite (`[ ref ]`) ;
- valeur `{…}` vide ;
- lien `/edit` ;
- adresse de lien invalide ;
- « Festival » ou « festivaliers » (on écrit « Célébration » et « participants ») ;
- texte à compléter (`>>> … <<<`, `TODO`).

Les **points à vérifier** ne bloquent pas l'envoi :

- adresse affichée en clair ;
- année différente de celle de l'événement ;
- gras ou italique mal fermé ;
- formulaire encore en test.
