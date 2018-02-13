# Template de These
Structure minimale pour rédiger un manuscrit de thèse de doctorat aux normes typographiques françaises.

## Structure du document
Le document comprend les parties suivantes :

* Table des matières
* Liste des figures
* Liste des tableaux

1. Chapitre 1
  * Citation de début de chapitre
  * Table des matières détaillée du chapitre
  * Corps du chapitre
  * Références biblio du chapitre
2. Chapitre 2
  * Idem
3. Etc.

* Annexes :
  * documents annexes
  * liste des acronymes
  * liste des symboles
  * glossaire

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
Une alternative à la la compilation manuelle (même automatisée avec un script bash), est d'utiliser latexmk qui va complémenter automariser *tout* le processus.

````
latexmk -pdf -pvc Main.tex
````
Les options servent respectivement à avoir un fichier pdf et afficher le document généré. Plus d'information sur latexmk sont disponiles [ici](https://man.cx/latexmk) et [là](http://mg.readthedocs.io/latexmk.html).

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
