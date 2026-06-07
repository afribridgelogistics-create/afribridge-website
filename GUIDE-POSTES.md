# 💼 Guide — Gestion des postes ouverts AfriBridge

## Comment ça marche ?

La page Carrières charge automatiquement les postes depuis un fichier **`jobs.json`**
sur GitHub. Ce fichier est généré depuis un **Google Sheets** partagé avec l'équipe.

---

## Étape 1 — Créer le Google Sheets

1. Va sur **sheets.google.com** → Créer une nouvelle feuille
2. Importe le fichier **`template-postes.csv`** fourni :
   - Fichier → Importer → Upload → `template-postes.csv`
3. Partage la feuille avec toute l'équipe RH

---

## Étape 2 — Configurer GitHub Actions

1. Dans ton dépôt GitHub → **Settings** → **Secrets and variables** → **Actions**
2. Clique **"New repository secret"**
3. Nom : `GOOGLE_SHEET_ID`
4. Valeur : l'ID de ta feuille Google (dans l'URL : `.../spreadsheets/d/`**XXXXX**`/edit`)
5. Clique **Add secret**

⚠️ Le Google Sheets doit être **public** (Partager → Tout le monde avec le lien → Lecteur)

---

## Étape 3 — Gérer les postes (usage quotidien)

### Ajouter un poste
→ Ajouter une ligne dans le Google Sheets, mettre **OUI** dans la colonne `actif`

### Désactiver un poste
→ Mettre **NON** dans la colonne `actif` (la ligne est conservée pour référence)

### Supprimer un poste
→ Supprimer la ligne

### Colonnes importantes
| Colonne | Description |
|---|---|
| `id` | Identifiant unique (ex: job1, job2...) |
| `titre_fr` / `titre_en` | Titre du poste en FR et EN |
| `departement_fr` / `_en` | Département |
| `type` | CDI, CDD, Stage, Freelance... |
| `lieu_fr` / `lieu_en` | Localisation |
| `description_fr` / `_en` | Description courte (affichée sur la card) |
| `responsabilites_fr` / `_en` | Liste séparée par `\|` |
| `profil_fr` / `_en` | Liste séparée par `\|` |
| `actif` | **OUI** = affiché, **NON** = masqué |

---

## Étape 4 — Mettre à jour le site

Le site se met à jour automatiquement **tous les jours à 6h00 UTC**.

Pour une mise à jour **immédiate** :
1. Va sur GitHub → onglet **Actions**
2. Clique **"Update Jobs from Google Sheets"**
3. Clique **"Run workflow"** → **Run workflow**
4. Attends 1-2 minutes → le site est à jour ✅

---

## Si pas de Google Sheets (mode manuel)

Tu peux aussi éditer `jobs.json` directement sur GitHub :
- `"active": true` → affiche les postes
- `"active": false` → affiche le message "Aucun poste ouvert"
- Ajoute/retire des blocs dans `"jobs": [...]`
