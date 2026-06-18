# Test technique — Chargé·e d'études enquêtes étudiants

**Présentation Quarto revealjs** (support d'entretien en visio, partage d'écran) pour le recrutement
du poste de chargé·e d'études quantitatives et qualitatives — enquêtes étudiants, Direction de la Scolarité.

Le code **R et Python s'exécute réellement** au rendu (résultats affichés au clic). Le rendu et la
publication sur GitHub Pages sont **automatisés par GitHub Actions** — aucun rendu manuel nécessaire.

- **Dépôt** : <https://github.com/mofy-scpo/Recrutement-Barometre>
- **Site publié** : <https://mofy-scpo.github.io/Recrutement-Barometre/>

## ⚠️ À lire — dépôt public

- **Aucune réponse ni barème ne figure dans ce dépôt.** La présentation n'affiche que les questions
  (et les sorties de code, qui sont des résultats de calcul, pas des corrigés).
- La **grille d'évaluation** (réponses attendues, notation) est conservée **hors du dépôt**, en local,
  dans `GRILLE-EVALUATION-ne-pas-publier.md` au niveau du dossier parent. **Ne la committez jamais ici.**
- Toutes les données et graphiques sont **fictifs** (générés dans le script).

## Contenu

- `index.qmd` — la présentation (revealjs). Trois blocs : **A** statistiques (boxplot plotly interactif),
  **C** lecture de code (R + Python exécutés, 4 niveaux), **E** qualitatif & restitution.
- `theme-sciencespo.scss` — thème rouge Sciences Po.
- `_quarto.yml` — configuration du projet (sortie de rendu dans `_site`).
- `requirements.txt` — dépendance Python (`pandas`), utilisée aussi pour le cache pip.
- `.github/workflows/publish.yml` — rendu (R + Python) puis publication automatique sur la branche `gh-pages`.

## Comment ça marche

À chaque `push` sur `main`, GitHub Actions :

1. installe Quarto, R (`knitr`, `rmarkdown`, `dplyr`, `tidyr`, `plotly`, `reticulate`) et Python (`pandas`) ;
2. **exécute le code** R et Python et **rend** la présentation dans `_site` (`quarto render`) ;
3. **déploie** `_site` sur la branche **`gh-pages`** (l'action crée la branche au premier passage).

Les dépendances sont **mises en cache** (packages R via `setup-r-dependencies`, pip via `requirements.txt`) :
seul le premier run installe tout, les suivants restaurent le cache.

## Activation de GitHub Pages (une seule fois)

**Settings → Pages → Build and deployment → Source : Deploy from a branch**,
branche **`gh-pages`**, dossier **`/ (root)`**, puis *Save*.
Le site apparaît au bout d'1–2 min sur <https://mofy-scpo.github.io/Recrutement-Barometre/>.

## Mettre le test à jour

Modifiez `index.qmd` (ou le thème), puis :

```bash
git add -A && git commit -m "maj du test" && git push
```

Le site se régénère et se republie automatiquement.

## Utilisation pendant l'entretien

- **Navigation** : flèches `←` `→` (ou `Espace`). `F` plein écran, `S` notes, `B`/`C` tableau (chalkboard), `Échap` vue d'ensemble.
- **Choix du langage** : onglets **R / Python** sur chaque exercice du Bloc C — le candidat choisit sa voie.
- **Sorties de code** : le résultat n'apparaît qu'après une flèche → le candidat explique d'abord, on révèle ensuite.
- **Graphique** : le boxplot est interactif (survol = valeurs).
- Gardez votre grille de correction à côté.

## Rendu en local (optionnel)

Nécessite [Quarto](https://quarto.org), R (packages `knitr`, `rmarkdown`, `dplyr`, `tidyr`, `plotly`,
`reticulate`) et Python (`pandas`). Pointez reticulate vers votre Python (variable `RETICULATE_PYTHON`), puis :

```bash
quarto preview index.qmd   # aperçu live
quarto render index.qmd    # rendu unique
```
