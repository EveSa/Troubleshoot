---
layout: post
---
# Ajouter des sous section à la bibliographie

1. Ajouter des tags par dossier dans Zotero
2. Exporter la bibliographie avec les tags en format `.bib`
3. Ajouter les différentes parties de la bibliographie dans le document $\LaTeX$

```latex
\printbibliography[heading=bibintoc, keyword={Général},title={Bibliographie}]
```

# Changer la taille des marges

```latex
\usepackage[margin=2.5cm]{geometry}
```

De base, les marges sont à 2in dans les articles