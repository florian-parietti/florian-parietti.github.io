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
| hero-face.jpg | Hero — face 2020 → 2025 |
| story-dos.jpg | Section "Pourquoi m'écouter" — dos 2020 → 2025 |
| m-vo2.jpg / m-fc.jpg / m-sommeil.jpg | Cartes métriques (gabarit identique 1200x560) |
| plan-face-3.jpg / plan-dos-3.jpg | Montages 3 étapes, utilisés dans plan.html |

Les deux montages 2020 → 2025 sont recomposés depuis tes PNG 2000x3000.
Règle d'échelle : même taille de tête dans les deux photos d'une paire, même niveau
de recadrage haut et bas. Quand deux repères anatomiques divergeaient, j'ai retenu
celui qui te désavantage. Aucune exagération.

## Ensuite
1. Vidéo 2 min → merci.html (bloc commenté)
2. Calendly : 20 min, "Appel diagnostic", 4 questions de qualification
3. Brevo : import + séquence 4 emails
