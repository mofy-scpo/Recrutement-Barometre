# Test technique — Chargé·e d'études enquêtes étudiants

**Présentation Quarto revealjs** (support d'entretien en visio, partage d'écran) pour le recrutement
du poste de chargé·e d'études quantitatives et qualitatives — enquêtes étudiants, Direction de la Scolarité.

Le code **R et Python s'exécute réellement** au rendu (résultats affichés au clic). Le rendu et la
publication sur GitHub Pages sont **automatisés par GitHub Actions** — aucun rendu manuel nécessaire.

## ⚠️ À lire avant de publier

Ce dépôt est destiné à être **public**. En conséquence :

- **Aucune réponse ni barème ne figure dans ce dépôt.** La présentation n'affiche que les questions
  (et les sorties de code, qui sont des résultats de calcul, pas des corrigés).
- La **grille d'évaluation** (réponses attendues, notation) est conservée **hors du dépôt**, en local,
  dans `GRILLE-EVALUATION-ne-pas-publier.md` au niveau du dossier parent. **Ne la committez jamais ici.**
- Toutes les données et graphiques sont **fictifs** (générés dans le script).

## Contenu

- `index.qmd` — la présentation (revealjs). Trois blocs : **A** statistiques (boxplot plotly interactif),
  **C** lecture de code (R + Python, 4 niveaux), **E** qualitatif & restitution.
- `theme-sciencespo.scss` — thème rouge Sciences Po.
- `_quarto.yml` — configuration du projet.
- `.github/workflows/publish.yml` — rendu (R + Python) et publication automatiques sur la branche `gh-pages`.

## Mise en ligne (une seule fois)

1. Créez un dépôt **public**, par ex. `test-technique-enquetes`, et poussez-y ce dossier.
2. À chaque `push` sur `main`, GitHub Actions installe R, Python, Quarto, **exécute le code**, rend la
   présentation et la publie sur la branche `gh-pages`.
3. Dans le dépôt : **Settings → Pages → Build and deployment → Source : Deploy from a branch**,
   branche **`gh-pages`**, dossier **`/ (root)`**. Enregistrez.
4. L'URL publique apparaît après ~1–2 min :
   `https://<votre-pseudo>.github.io/test-technique-enquetes/`.

> Le premier rendu Actions prend quelques minutes (installation des packages R). Les suivants sont mis en cache.

## Utilisation pendant l'entretien

- **Navigation** : flèches `←` `→` (ou `Espace`). `F` plein écran, `S` notes, `B`/`C` tableau (chalkboard), `Échap` vue d'ensemble.
- **Choix du langage** : onglets **R / Python** sur chaque exercice du Bloc C — le candidat choisit sa voie.
- **Sorties de code** : le résultat n'apparaît qu'après une flèche → le candidat explique d'abord, on révèle ensuite.
- **Graphique** : le boxplot est interactif (survol = valeurs).
- Gardez votre grille de correction à côté.

## Rendu en local (optionnel)

Nécessite [Quarto](https://quarto.org), R (packages `dplyr`, `tidyr`, `plotly`, `reticulate`) et
Python (`pandas`). Pointez reticulate vers votre Python (`RETICULATE_PYTHON`), puis :

```bash
quarto preview index.qmd   # aperçu live
quarto render index.qmd    # rendu unique
```
