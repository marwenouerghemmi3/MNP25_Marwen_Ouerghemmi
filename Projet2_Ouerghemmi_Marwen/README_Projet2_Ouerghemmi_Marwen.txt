README — Projet2_Marwen.Ouerghemmi

1. Description générale : 

Ce projet simule le modèle d’Ising 1D (J = 1, sans champ externe) à l’aide de l’algorithme de Metropolis.
Le code calcule et analyse : énergie, magnétisation, histogrammes, capacité calorifique et dépendance en température.


Paramètres globaux :
- N = 1000 spins
- SAMPLE_STEPS = 10000
- États initiaux : aligned ou random
- Générateur : numpy.default_rng()

2. Fonctions principales (avec paramètres)

flip_random_spin(spin_array, generator=None)
Paramètres :
- spin_array : tableau des spins
- generator : RNG (optionnel)
Rôle :
Sélectionne un spin aléatoire, calcule la variation d’énergie
ΔE = -2 σ_k (σ_{k-1} + σ_{k+1})
et retourne le spin.

metropolis_step(spin_array, current_energy, current_magnet, temperature, generator=None)
Paramètres :
- spin_array, current_energy, current_magnet
- temperature
- generator
Rôle :
Propose un flip, calcule ΔE et ΔM, et décide de l’accepter selon ΔE < 0 ou r < exp(-ΔE/T).

compute_specific_heat(energy_samples, T)
Paramètres :
- energy_samples
- T
Rôle :
Calcule Cv = (⟨E²⟩ - ⟨E⟩²)/T².

ising_simulation(N, T, SAMPLE_STEPS, generator, init_type='aligned')
Paramètres :
- N, T, SAMPLE_STEPS, generator
- init_type : aligned ou random
Rôle :
Initialisation + évolution Metropolis + stockage énergie/magnétisation.

3. 

Question 3  Équilibration
Estimations (N = 1000) :
- T = 20 (random) : 1–10 sweeps → 1000–10 000 étapes
- T = 1 : 10–100 sweeps → 10 000–100 000 étapes
- T = 0.1 (aligned) : <1 sweep → 100–1000 étapes
- T = 0.1 (random) : très lent → 10³–10⁵ sweeps

Remarque :
10000 étapes suffisent pour T = 20 et T = 1, mais pas pour T = 0.1 en état aléatoire.

Conclusion :
Équilibre rapide à haute T, modéré à T ≈ 1, extrêmement lent à basse T si initialisation aléatoire.

Question 6  Histogrammes basse vs haute T
Haute température :
- énergie large
- magnétisation centrée en 0

Basse température :
- énergie étroite (minimum)
- magnétisation proche ±N (bimodale)

Conclusion :
Les histogrammes basse et haute température ne se ressemblent pas : désordre à haute T, ordre quasi parfait à basse T.
Explication physique : 

À haute température, l’agitation thermique domine : les spins se retournent librement, ce qui produit des histogrammes larges pour l’énergie et de magnétisation centrée sur 0.
À basse température, les interactions entre spins dominent : le système reste proche de son état fondamental, donnant des histogrammes très étroits en énergie et une magnétisation proche de ±N.
Les deux régimes sont donc physiquement opposés : désordre thermique contre ordre collectif.
