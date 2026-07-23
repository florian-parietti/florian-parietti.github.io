# V2 — Déploiement

## Fichiers

```
index.html      → landing (formulaire prénom + email)
merci.html      → page de remerciement (accès plan + appel)
plan.html       → le guide (ex-contenu gaté)
styles.css      → CSS commun aux 3 pages
img/            → 3 photos de transformation
```

## Mise en ligne (5 min)

1. Repo `florian-parietti.github.io` → supprimer l'ancien `index.html`.
2. Uploader les 5 éléments ci-dessus **à la racine** (garder le dossier `img/` tel quel).
3. Commit. La page est en ligne sous ~1 min.

## Google Apps Script — 1 modification obligatoire

Le formulaire envoie maintenant un paramètre supplémentaire : `prenom`.

1. Ouvrir le Google Sheet → **Extensions → Apps Script**.
2. Ajouter `prenom` dans la ligne qui construit la row, en première position. Exemple :

```js
sheet.appendRow([
  e.parameter.prenom,        // ← NOUVEAU
  e.parameter.email,
  e.parameter.instagram,
  e.parameter.objectif_physique,
  e.parameter.objectif_sante,
  e.parameter.autre,
  e.parameter.date,
  e.parameter.statut
]);
```

3. Ajouter la colonne **Prénom** en A dans le Sheet.
4. **Déployer → Gérer les déploiements → modifier → Nouvelle version.**
   (Si tu ne redéploies pas, rien ne change.)
5. Tester : remplir le formulaire, vérifier qu'une ligne apparaît.

> Le champ Instagram est maintenant optionnel sur `merci.html`.
> Ces lignes arrivent avec `statut = Instagram` — dédoublonne par email.

## À faire ensuite (dans l'ordre)

1. Enregistrer la vidéo de 2 min → l'insérer dans `merci.html` (le bloc à remplacer est commenté dans le fichier).
2. Renommer l'événement Calendly en **« Appel diagnostic — 20 min »** et passer la durée à 20 min.
3. Ajouter les 4 questions de qualification sur Calendly.
4. Créer le compte Brevo, importer les emails du Sheet, brancher la séquence de 4 emails.
