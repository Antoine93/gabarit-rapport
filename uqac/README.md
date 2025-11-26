# Template de Rapport LaTeX - UQAC

Template réutilisable pour la rédaction de rapports académiques à l'Université du Québec à Chicoutimi (UQAC).

## Structure du Projet

```
rapport/
├── rapport.tex                 # Fichier principal
├── variables.tex               # Métadonnées du document (à modifier pour chaque rapport)
├── uqac.sty                    # Style UQAC (générique, ne pas modifier)
├── .vscode/
│   └── settings.json          # Configuration VS Code (sortie build/)
├── sections/                  # TEMPLATES GÉNÉRIQUES
│   ├── 1-page_titre/
│   ├── 2-introduction/
│   ├── 3-developpement/
│   ├── 4-resultats/
│   ├── 5-conclusion/
│   └── examples/              # Guide de référence LaTeX
├── images/                    # Images et figures
├── references/
│   └── references.bib         # Bibliographie
└── build/                     # Fichiers intermédiaires (généré automatiquement)
```

## Démarrage Rapide

### Pour un Nouveau Rapport

1. **Copier le dossier `rapport/`** vers un nouveau projet
2. **Modifier `variables.tex`** avec vos informations :
   ```latex
   \newcommand{\courseName}{Nom du cours}
   \newcommand{\courseCode}{Sigle du cours}
   \newcommand{\assignmentName}{Nom du devoir}
   \newcommand{\authorName}{Nom, Prénom}
   \newcommand{\studentID}{Code permanent}
   \newcommand{\professorName}{Nom du/de la professeur(e)}
   \newcommand{\universityName}{Nom de l'université}
   \newcommand{\departmentName}{Département}
   \newcommand{\assignmentDate}{Jour Mois Année}
   ```
3. **Remplir les sections** dans `sections/` en remplaçant les `TODO`
4. **Compiler** avec VS Code ou la ligne de commande

### Compilation

#### Avec VS Code (recommandé)
1. Installer l'extension **LaTeX Workshop**
2. Ouvrir `rapport.tex`
3. Utiliser `Ctrl+Alt+B` pour compiler
4. Le PDF sera généré dans `build/rapport.pdf`

**Important :** Si votre workspace VS Code contient plusieurs dossiers (ex: `devoir2/rapport/`, `devoir2/code/`), déplacez `.vscode/settings.json` à la racine du workspace (`devoir2/.vscode/settings.json`) pour que la configuration s'applique correctement.

#### Ligne de commande
```bash
# Avec pdflatex
pdflatex -output-directory=build rapport.tex
biber build/rapport
pdflatex -output-directory=build rapport.tex
pdflatex -output-directory=build rapport.tex

# Avec latexmk (avantage: pas besoin de compiler plusieurs fois)
latexmk -pdf rapport.tex
```

## Utilisation

### 1. Variables Globales (`variables.tex`)

Toutes les métadonnées sont centralisées dans un seul fichier. Modifier ces valeurs met à jour automatiquement :
- La page de titre
- Les en-têtes et pieds de page
- Les métadonnées LaTeX

**Par défaut (template) :**
```latex
\newcommand{\courseName}{Nom du cours}
\newcommand{\courseCode}{Sigle du cours}
\newcommand{\assignmentName}{Nom du devoir}
\newcommand{\authorName}{Nom, Prénom}
\newcommand{\studentID}{Code permanent}
\newcommand{\professorName}{Nom du/de la professeur(e)}
\newcommand{\universityName}{Nom de l'université}
\newcommand{\departmentName}{Département}
\newcommand{\assignmentDate}{Jour Mois Année}
```

### 2. Structure des Sections

Chaque section template contient :
- Des commentaires `% TODO:` indiquant quoi écrire
- Des exemples commentés de code LaTeX
- Une structure de base à suivre

**Sections disponibles :**
- **1-page_titre/** : Page de titre automatique (utilise `variables.tex`)
- **2-introduction/** : Contexte, objectifs, organisation
- **3-developpement/** : Contenu principal avec exemples
- **4-resultats/** : Résultats expérimentaux et analyse
- **5-conclusion/** : Synthèse, accomplissements, perspectives
- **examples/** : Guide de référence permanent

### 3. Guide d'Exemples

Le dossier `sections/examples/` contient des exemples complets pour :

#### Formules Mathématiques (`formules.tex`)
```latex
% Formule inline
L'équation $E = mc^2$ est célèbre.

% Formule centrée
\begin{equation}
    \int_{a}^{b} f(x) \, dx = F(b) - F(a)
\end{equation}

% Système d'équations
\begin{align}
    x + y &= 5 \\
    2x - y &= 1
\end{align}
```

#### Tableaux (`tableaux.tex`)
```latex
\begin{table}[H]
    \centering
    \caption{Résultats expérimentaux}
    \label{tab:exemple}
    \begin{tabular}{|c|c|c|}
        \hline
        \textbf{Essai} & \textbf{Valeur} & \textbf{Unité} \\
        \hline
        1 & 10 & m \\
        2 & 20 & kg \\
        \hline
    \end{tabular}
\end{table}
```

#### Figures (`figures.tex`)
```latex
\begin{figure}[H]
    \centering
    \includegraphics[width=0.6\textwidth]{images/figure.png}
    \caption{Description de la figure}
    \label{fig:exemple}
\end{figure}
```

#### Code MATLAB (`code.tex`)
```latex
% Code simple
\begin{lstlisting}[caption={Exemple de code}, label={code:exemple}]
% Calcul de la moyenne
x = [1, 2, 3, 4, 5];
moyenne = mean(x);
disp(['Moyenne : ', num2str(moyenne)]);
\end{lstlisting}

% Code avec formules mathématiques
\begin{lstlisting}[caption={Code avec formules}, escapechar=|]
% Résout l'équation |$ax^2 + bx + c = 0$|
delta = b^2 - 4*a*c;
\end{lstlisting}
```

### 4. Références

#### Références croisées
```latex
% Définir un label
\section{Introduction}
\label{sec:intro}

% Référencer
Comme mentionné à la Section~\ref{sec:intro}...
Le Tableau~\ref{tab:exemple} montre...
La Figure~\ref{fig:exemple} illustre...
Le Code~\ref{code:exemple} présente...
```

#### Bibliographie
1. Ajouter les références dans `references/references.bib` :
```bibtex
@article{exemple2025,
    author = {Nom, Prénom},
    title = {Titre de l'article},
    journal = {Nom du journal},
    year = {2025}
}
```

2. Citer dans le texte :
```latex
Selon \cite{exemple2025}, les méthodes numériques...
```

## Style UQAC (`uqac.sty`)

Le fichier de style inclut automatiquement :

### Packages Chargés
- Encodage UTF-8 et français (babel)
- Math (amsmath, amssymb)
- Figures et tableaux (graphicx, float, caption)
- Code source (listings, xcolor)
- TikZ pour diagrammes
- Et plus...

### Configuration MATLAB
- Coloration syntaxique complète
- Support des accents français (é, è, ê, à, ç, etc.)
- Support des caractères spéciaux (°, ±, ², ³, etc.)
- Support des lettres grecques (α, β, γ, δ, π, etc.)

### Commandes Personnalisées

#### En-têtes et pieds de page
```latex
\uqacheaders{Titre Cours}{Code Cours}
```

#### Logo UQAC
```latex
\uqaclogo[0.2]  % 20% de la largeur
```

### Couleurs UQAC
- `uqacGreen` : RGB(107, 138, 21) - Vert UQAC
- `uqacGray` : RGB(128, 128, 128) - Gris

## Configuration VS Code

Le fichier `.vscode/settings.json` configure :
- Sortie dans `build/` (garde la racine propre)
- Séquence de compilation complète avec bibliographie (pdflatex → biber → pdflatex × 2)
- Utilisation automatique de `rapport.tex` comme fichier principal

```json
{
   "latex-workshop.latex.outDir": "%DIR%/build",
   "latex-workshop.latex.rootFile.doNotPrompt": true,
   "latex-workshop.latex.rootFile.useSubFile": false,
   "latex-workshop.latex.search.rootFiles.include": ["rapport.tex"],
   "latex-workshop.latex.recipes": [
      {
         "name": "pdflatex → biber → pdflatex × 2",
         "tools": ["pdflatex", "biber", "pdflatex", "pdflatex"]
      }
   ],
   "latex-workshop.latex.tools": [
      {
         "name": "pdflatex",
         "command": "pdflatex",
         "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-output-directory=build",
            "%DOC%"
         ]
      },
      {
         "name": "biber",
         "command": "biber",
         "args": [
            "--output-directory=build",
            "%DOCFILE%"
         ]
      }
   ]
}
```

**Avantages :**
- Vous pouvez compiler depuis n'importe quel fichier `.tex` (introduction, développement, etc.)
- La compilation utilisera toujours `rapport.tex` comme fichier principal
- Tous les fichiers intermédiaires vont dans `build/`
- La bibliographie est automatiquement traitée

## Workflow Recommandé

### Nouveau Devoir (Même Cours)
1. Copier le dossier `rapport/`
2. Modifier uniquement :
   - `variables.tex` (changer `assignmentName` et `assignmentDate`)
   - Contenu des sections
3. Compiler

### Nouveau Cours
1. Copier le dossier `rapport/`
2. Modifier `variables.tex` (toutes les variables)
3. Remplir les sections dans `sections/`
4. Compiler

### Ajout de Contenu
1. Consulter `sections/examples/` pour la syntaxe
2. Ajouter le contenu dans les sections appropriées
3. Placer les images dans `images/` (ou sous-dossier comme `images/logo/`)
4. Ajouter les références dans `references/references.bib`

## Dépannage

### Erreur "Cannot find reference"
**Cause :** Les labels référencés n'existent pas encore.
**Solution :** Compiler **deux fois** (LaTeX a besoin de deux passes).

### Caractères accentués mal affichés
**Cause :** Fichier non encodé en UTF-8.
**Solution :** Sauvegarder les fichiers `.tex` en UTF-8 dans VS Code.

### Images non trouvées
**Cause :** Chemin relatif incorrect.
**Solution :** Vérifier que les images sont dans `images/` et utiliser :
```latex
\includegraphics[width=0.5\textwidth]{images/nom_image.png}
```

### Bibliographie non affichée
**Cause :** Fichier `references.bib` vide ou Biber non exécuté.
**Solution :**
1. Vérifier que `references/references.bib` contient au moins une référence
2. Avec VS Code : La configuration exécute automatiquement Biber
3. Ligne de commande :
```bash
pdflatex rapport.tex
biber --output-directory=build rapport
pdflatex rapport.tex
pdflatex rapport.tex
```

### Fichiers intermédiaires dans la racine
**Causes possibles :**
1. Configuration VS Code non appliquée
2. Vous compilez un fichier inclus au lieu de `rapport.tex`

**Solution :**
1. Vérifier que `.vscode/settings.json` contient les paramètres `rootFile`
2. Avec la configuration actuelle, vous pouvez compiler depuis n'importe quel fichier `.tex`
3. Si le problème persiste, redémarrer VS Code

### Erreur "Cannot find 'build/rapport.bcf'"
**Cause :** Biber cherche les fichiers au mauvais endroit.
**Solution :** Vérifier que dans `.vscode/settings.json`, la configuration Biber utilise :
```json
"args": ["--output-directory=build", "%DOCFILE%"]
```

## Ressources

- [Documentation LaTeX (français)](https://www.latex-project.org/help/documentation/)
- [Documentation TikZ](https://tikz.dev/)
- [LaTeX Wikibook](https://en.wikibooks.org/wiki/LaTeX)
- [TeXdoc - Documentation en ligne](https://texdoc.org/)
- [Detexify - Recherche de symboles LaTeX](https://detexify.kirelabs.org/)
- [TeXample.net - Exemples TikZ](https://texample.net/)

## Contribution

Pour améliorer ce template :
1. Modifier les fichiers dans `sections/` pour les templates
2. Modifier `uqac.sty` pour le style
3. Mettre à jour ce README

## Licence

Template libre d'utilisation pour les étudiants de l'UQAC.

---

**Bon courage avec vos rapports !**
