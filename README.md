# README

Ce projet illustre la construction, la diagonalisation et l'analyse
d'une matrice dynamique représentant un système linéaire de molécules
couplées.
## 0. Partie mathématique ( fichier PDF) 
Q1-2
## 1. Dépendances

Assurez‑vous d'installer les librairies suivantes avant d'exécuter le
script :


 install numpy matplotlib scipy


Le script utilise :

-   **numpy** : manipulation de tableaux, algèbre linéaire\
-   **matplotlib** : visualisation des spectres et modes propres\
-   **scipy.sparse** et **scipy.sparse.linalg** : version creuse de la
    matrice et diagonalisation efficace\
-   **time** : mesure du temps de calcul

## 2. Description du code

### a) Construction de la matrice dynamique

La fonction `construire_matrice(NbMol, epsCouple, normaliser)` crée une
matrice dynamique de dimension `2*NbMol` représentant un système
diatomique.\
Elle calcule ensuite les valeurs et vecteurs propres via `eigh`.

### b) Diagonalisation complète

`diagonalisation_complete` retourne les fréquences adimensionnées `ω/Ω0`
issues de la racine carrée des valeurs propres.

### c) Visualisations demandées

Le script génère plusieurs graphiques correspondant aux questions d'un
exercice : - spectre pour `N=10`, `k'=0` - étude du temps de calcul en
fonction de `N` - spectre pour `N=200` et différents couplages -
visualisation des premiers modes propres - modes optiques de haute
fréquence - séparation des branches acoustiques et optiques

### d) Version sparse

La fonction `matrice_sparse` génère une matrice creuse SciPy et calcule
les premières valeurs propres par `eigsh`, permettant d'accélérer le
traitement pour de très grandes tailles.

## 3. Exécution

Lancez simplement le script :

``` bash
python votre_script.py
```

Les figures apparaîtront automatiquement.

## 4. Notes

-   Le code utilise systématiquement l'importation de toutes les
    librairies au début du fichier conformément aux bonnes pratiques.
-   Pour les très grandes matrices, privilégiez l'approche **sparse**.
