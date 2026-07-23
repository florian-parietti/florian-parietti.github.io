# V3 — Déploiement

## Fichiers
index.html · merci.html · plan.html · styles.css · img/ (à la racine du repo)

## 1. Apps Script — À CORRIGER EN PREMIER

Ton code actuel inverse Prénom et Date, et écrit "Nouveau" en 8e colonne au lieu de la 4e.
Remplace tout le contenu par :

```javascript
function doGet(e) {
  try {
    var sheet = SpreadsheetApp
      .openById("1N1HyFaykcNsPy5ESyrGHXHYGDGyYmkir81Jscg-AqB4")
      .getSheetByName("Leads");

    sheet.appendRow([
      e.parameter.date || new Date().toLocaleString("fr-BE"),  // A Date
      e.parameter.prenom || "",                                // B Prénom
      e.parameter.email || "",                                 // C Email
      e.parameter.statut || "Nouveau",                         // D Statut
      "",                                                      // E Relance
      "",                                                      // F Notes
      e.parameter.instagram || ""                              // G Instagram
    ]);

    return ContentService.createTextOutput("OK")
      .setMimeType(ContentService.MimeType.TEXT);
  } catch(err) {
    return ContentService.createTextOutput("Error: " + err.toString())
      .setMimeType(ContentService.MimeType.TEXT);
  }
}

function doPost(e) { return doGet(e); }
```

Puis : Déployer → Gérer les déploiements → crayon → Version : Nouvelle version → Déployer.
Sans cette dernière étape, rien ne change.

## 2. Mise en ligne
Dézipper, puis glisser les 5 fichiers + le dossier img/ sur GitHub (pas le dossier parent).
Tu dois voir 11 lignes dans la liste d'upload.

## 3. Vérifier
- Photo de face 2020→2025 visible sans scroller
- 3 cartes de métriques avec les captures Apple Santé
- Formulaire : prénom + email uniquement
- Soumission → merci.html → une ligne dans le Sheet, colonnes alignées

## Images
| Fichier | Usage |
|---|---|
| hero-face.jpg | Hero — montage face 2020→2025, recomposé depuis tes 4 originaux |
| story-dos.jpg | Section "Pourquoi m'écouter" — montage dos 2020→2025 |
| m-vo2.jpg | Carte VO₂ max (59 + niveau Élevé) |
| m-fc.jpg | Carte fréquence cardiaque au repos |
| m-sommeil.jpg | Carte sommeil profond |
| transfo-*.jpg | Utilisées dans plan.html |

Les deux montages sont recomposés depuis tes 4 PNG 2000x3000.
Règle d'échelle : les deux photos d'une paire sont mises à la même taille de tête,
même niveau de recadrage haut et bas. Aucune exagération.
hero-face.jpg fait 1738 px de large, affiché à 470 px : net même sur écran Retina.

## Ensuite
1. Vidéo 2 min → merci.html (bloc commenté)
2. Calendly : 20 min, "Appel diagnostic", 4 questions de qualification
3. Brevo : import + séquence 4 emails
