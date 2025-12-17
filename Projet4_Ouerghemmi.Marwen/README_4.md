



1\. OBJECTIF 



Ce programme simule l’évolution temporelle de la température

dans une pièce bidimensionnelle à l’aide de l’équation de la

diffusion thermique (équation de la chaleur).



La pièce contient :

\- une fenêtre maintenue à température extérieure constante

\- un radiateur maintenu à température élevée constante



Le programme calcule :

\- la distribution de température dans la pièce

\- le flux thermique échangé par la fenêtre et par le radiateur

\- l’évolution temporelle de ces flux sous forme de relaxation

&nbsp; exponentielle vers un régime stationnaire





2\. MODÈLE PHYSIQUE



L’équation résolue est l’équation de la chaleur 2D :



&nbsp;   ∂T/∂t = κ ( ∂²T/∂x² + ∂²T/∂y² )



où :

\- T est la température (°C)

\- κ est la diffusivité thermique de l’air



Hypothèses :

\- milieu homogène

\- diffusion pure (pas de convection)

\- régime transitoire puis stationnaire

\- radiateur et fenêtre imposent des températures constantes





3\. DISCRÉTISATION NUMÉRIQUE



\- Discrétisation spatiale : différences finies centrées

\- Discrétisation temporelle : schéma explicite

\- Condition de stabilité respectée via le facteur F = 0.1



La grille numérique est étendue par des cellules fantômes

pour imposer correctement les conditions aux limites.





4\. CONDITIONS AUX LIMITES



\- Conditions de Neumann (flux nul) sur les murs

\- Condition de Dirichlet sur la fenêtre : T = T\_ext

\- Condition de Dirichlet sur le radiateur : T = T\_heat



La fonction apply\_neumann\_bc applique ces conditions

à chaque pas de temps.





**5. STRUCTURE DU CODE**

5.1 Paramètres physiques et numériques

\- Taille de la grille

\- Diffusivité thermique

\- Pas de temps et pas d’espace

\- Températures imposées

\- Durée totale de la simulation (20 jours)



5.2 Initialisation

\- Température initiale uniforme

\- Placement géométrique de la fenêtre et du radiateur

\- Masques booléens pour identifier ces zones



5.3 Boucle temporelle principale

\- Mise à jour explicite de la température

\- Application des conditions aux limites

\- Enregistrement de snapshots à des temps choisis

\- Calcul du flux thermique à chaque snapshot



5.4 Calcul du flux thermique

Le flux est calculé à partir du gradient de température

au voisinage des frontières (fenêtre / radiateur) selon

la loi de Fourier :



&nbsp;   Φ = -λ ∇T



où λ est la conductivité thermique de l’air.



5.5 Visualisation

\- Cartes de température à différents instants

\- Courbes d’évolution des flux thermiques





6\. RELAXATION EXPONENTIELLE DES FLUX



Les flux calculés sont utilisés pour construire une évolution

idéalisée sous forme de relaxation exponentielle :



&nbsp;   Φ(t) = Φ∞ + (Φ₀ - Φ∞) exp(-t / τ)



où :

\- Φ₀ est le flux initial

\- Φ∞ est le flux stationnaire

\- τ est le temps caractéristique du système



Cette modélisation permet :

\- une lecture claire du régime transitoire

\- une interprétation physique simple

\- une présentation plus propre pour un rapport ou un oral





7\. SORTIES DU PROGRAMME



Le programme génère :

\- une carte de température initiale

\- des cartes de température à 0.1 jour, 1 jour et 20 jours

\- des cartes intermédiaires optionnelles

\- un graphe de l’évolution temporelle des flux :

&nbsp;    flux radiateur

&nbsp;    flux fenêtre







Bibliothèques  :

\- numpy

\- matplotlib





9\. REMARQUES



\- Le pas de temps respecte la stabilité du schéma explicite

\- Les paramètres τ et Δ peuvent être ajustés pour modifier

&nbsp; l’allure de la relaxation exponentielle

\- Le code est entièrement vectorisé pour de bonnes performances









