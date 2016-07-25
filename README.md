# Template de These
Structure minimale pour rédiger un manuscrit de thèse de doctorat aux normes typographiques françaises.

## Compilation
### (pdf)latex
Le fichier ``Main.tex`` est le fichier maitre, c'est donc lui qu'il faut compiler avec (pdf)latex. 

### bibtex
On a une bibliographie par chapitre, il faut donc compiler chaque chapitre séparément avec bibtex.

### makeglossaries
Pour utiliser le package ``glossaries``, il faut utiliser le compilateur éponyme. C'est le fichier maitre (``Main.tex``) qu'il faut compiler.

### Pour résumer
La compilation de tout le document ressemble à ça:
```bash
pdflatex Main
bibtex Chapitre1
bibtex Chapitre2
makeglossaries Main
pdflatex Main
pdflatex Main
````

## Rédaction chapitre par chapitre
Dans le fichier ``Main.tex``, il faut penser à modifier la ligne suivante pour définir la liste des chapitres à compiler :
````latex
\includeonly{Chapitre1,Chapitre2,Annexes}
````

## Glossaire
Les entrées des glossaires (définitions, acronymes et symboles) sont définies dans ``Glossaire.tex``. Pour accéder à une entrée du glossaire, il suffit d'utiliser la commande suivante :
````latex
\gls{<label>}
````
