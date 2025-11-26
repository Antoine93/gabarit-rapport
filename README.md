# Gabarits de Rapport LaTeX

Collection de templates LaTeX pour la rédaction de rapports académiques et professionnels.

## Gabarits Disponibles

### `generique/` - Template Générique
Template anonymisé et réutilisable pour tout type de rapport.

**Caractéristiques:**
- Style professionnel anonyme (sans logo ni information institutionnelle)
- Palette de couleurs neutre
- Variables minimales à configurer
- [Documentation complète](generique/README.md)

**Variables à modifier:**
```latex
\reportTitle{...}
\reportSubtitle{...}
\reportCategory{...}
\reportDate{...}
```

### `uqac/` - Template UQAC
Template pour les rapports académiques à l'Université du Québec à Chicoutimi.

**Caractéristiques:**
- Logo et couleurs UQAC
- Structure académique complète
- Champs pour cours, professeur, code permanent
- [Documentation complète](uqac/README.md)

**Variables à modifier:**
```latex
\courseName{...}
\courseCode{...}
\assignmentName{...}
\authorName{...}
\studentID{...}
\professorName{...}
```

## Structure Commune

Les deux gabarits partagent la même structure:

```
gabarit/
├── rapport.tex                 # Fichier principal
├── variables.tex               # Métadonnées à personnaliser
├── *.sty                       # Fichier de style
├── sections/
│   ├── 1-page_titre/          # Page de titre
│   ├── 2-introduction/        # Introduction
│   ├── 3-developpement/       # Développement
│   ├── 4-resultats/           # Résultats
│   ├── 5-conclusion/          # Conclusion
│   └── examples/              # Guide LaTeX (formules, tableaux, figures, code)
├── images/                    # Dossier pour les images
├── references/
│   └── references.bib         # Bibliographie
└── build/                     # Fichiers de compilation (auto-généré)
```

## Démarrage Rapide

1. **Choisir un gabarit** (`generique/` ou `uqac/`)
2. **Copier le dossier** vers votre projet
3. **Modifier `variables.tex`** avec vos informations
4. **Remplir les sections** dans `sections/`
5. **Compiler** avec VS Code (Ctrl+Alt+B) ou en ligne de commande

### Compilation

```bash
# Avec pdflatex (3 passes requises)
pdflatex -output-directory=build rapport.tex
biber build/rapport
pdflatex -output-directory=build rapport.tex
pdflatex -output-directory=build rapport.tex

# Avec latexmk (recommandé)
latexmk -pdf rapport.tex
```

## Fonctionnalités

- Configuration centralisée des métadonnées (`variables.tex`)
- Sections pré-structurées avec commentaires `% TODO:`
- Guide d'exemples LaTeX complet (`sections/examples/`)
- Support MATLAB avec coloration syntaxique
- Bibliographie avec Biber
- Configuration VS Code incluse
- Compilation dans `build/` (garde la racine propre)

## Documentation

Chaque gabarit possède sa propre documentation détaillée:
- [Documentation du gabarit générique](generique/README.md)
- [Documentation du gabarit UQAC](uqac/README.md)

## Ressources

- [Documentation LaTeX (français)](https://www.latex-project.org/help/documentation/)
- [LaTeX Wikibook](https://en.wikibooks.org/wiki/LaTeX)
- [Detexify - Recherche de symboles LaTeX](https://detexify.kirelabs.org/)

## Licence

Templates libres d'utilisation.
