# Test technique — Chargé·e d'études enquêtes étudiants

**Présentation Quarto revealjs** (support d'entretien en visio, partage d'écran) pour le recrutement
du poste de chargé·e d'études quantitatives et qualitatives — enquêtes étudiants, Direction de la Scolarité.

Le code R / Python est présenté **en lecture seule** (test de lecture : le candidat explique ce que fait
le script, rien ne s'exécute). Le rendu et la publication sur GitHub Pages sont **automatisés par GitHub
Actions** — aucun rendu manuel nécessaire.

- **Dépôt** : <https://github.com/mofy-scpo/Recrutement-Barometre>
- **Site publié** : <https://mofy-scpo.github.io/Recrutement-Barometre/>

## ⚠️ À lire — dépôt public

- **Aucune réponse ni barème ne figure dans ce dépôt.** La présentation n'affiche que les questions et le code à lire.
- La **grille d'évaluation** (réponses attendues, notation) est conservée **hors du dépôt**, en local,
  dans `GRILLE-EVALUATION-ne-pas-publier.md` au niveau du dossier parent. **Ne la committez jamais ici.**
- Les chiffres et le graphique sont **fictifs**.

## Contenu

- `index.qmd` — la présentation (revealjs). Trois blocs : **A** statistiques (boxplot vertical + tableau d'indicateurs),
  **C** lecture de code (R / Python, 3 niveaux), **E** qualitatif & restitution.
- `theme-sciencespo.scss` — thème rouge Sciences Po.
- `_quarto.yml` — configuration du projet (sortie de rendu dans `_site`).
- `.github/workflows/publish.yml` — rendu Quarto puis publication automatique sur la branche `gh-pages`.

## Comment ça marche

À chaque `push` sur `main`, GitHub Actions installe Quarto, **rend** la présentation dans `_site`
(`quarto render`) puis **déploie** ce dossier sur la branche **`gh-pages`** (l'action crée la branche
au premier passage). Comme le code n'est pas exécuté, **aucun R ni Python n'est nécessaire** : le rendu
est quasi instantané, rien à réinstaller.

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

- **Navigation** : flèches `←` `→` (ou `Espace`). `F` plein écran, `B`/`C` tableau (chalkboard), `Échap` vue d'ensemble.
- **Slides scrollables** : si une slide déborde, elle défile.
- **Bloc A** : l'énoncé est posé avant le graphique ; le boxplot est statique, à lire sur l'axe.
- **Bloc C** : onglets **R / Python** (le candidat choisit sa voie) ; le code est en lecture seule, son explication *est* la réponse.
- Gardez votre grille de correction à côté.

## Rendu en local (optionnel)

Nécessite seulement [Quarto](https://quarto.org) (ni R ni Python) :

```bash
quarto preview index.qmd   # aperçu live
quarto render index.qmd    # rendu unique
```
