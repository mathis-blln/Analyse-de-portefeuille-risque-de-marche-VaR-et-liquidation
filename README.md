# Analyse de portefeuille : risque de marché, VaR et liquidation

Ce projet Python regroupe quatre séances d’analyse autour du risque de marché et de la liquidation d’actifs. L’objectif est d’étudier les comportements de portefeuilles en environnement de marché réel ou simulé, à travers des mesures statistiques, des comparaisons benchmark, et des stratégies d’exécution.

---

## Organisation du projet

###  Séance 1 — Risque de marché : portefeuille CAC40 (indépendante)

#### Objectifs :
- Étudier la performance et la volatilité d’un portefeuille équipondéré constitué de 10 actions du CAC40
- Comparer ce portefeuille à l’indice de référence (le CAC 40)
- Calculer des indicateurs de risque (VaR historique et gaussienne, tracking error)

#### Méthodes :
- **Données récupérées** sur 2 ans via `yfinance`
- **Calculs effectués** :
  - `AUM(t)` (valeur quotidienne du portefeuille)
  - **Performance** \( perf(T_i) = AUM(T_i)/AUM(T_{i-1}) - 1 \)
  - **Volatilité annualisée** (écart-type * √252)
  - **Tracking Error** : écart-type des différences de performances entre portefeuille et indice
  - **VaR historique** à 1 jour et 20 jours (quantiles empiriques)
  - **VaR gaussienne** à 99% de confiance, basée sur une distribution normale
  - 
---

### Séance 2 : Risque de liquidité : profil d'écoulement avec et sans déformation, avec ou sans stress

#### Objectifs : 
- Comparer l'écoulement d'un portefeuille d'actions avec et sans déformation, et analyse des poids au fil des jours
- Analyser l'impact d'un stress sur les volumes que l'on peut écouler chaque jour

#### Méthode : 

Nous faisons l'hypothèse que chaque acteur ne peut dépasser 20% du Average Daily Volumes 3 mois. Cela reflète la profondeur de marché. 

- Pour le profil avec déformation, nous supposons que la quantité liquidable en 1 jour vaut ADV 3M * 20%
  Chaque jour, nous liquidons le minimum entre les quantités restantes et la quantité liquidable en 1 jour.

- Pour le profil sans déformation, nous adoptons la stratégie; afin de ne pas altérer la composition du portefeuille, nous devons liquider à la vitesse de l'actif le moins liquide du portefeuille.


### Séance 3&4 : Risque de marché : pricing de bonds (clean/dirty price), puis calculs de VaR

#### Objectifs : 
- pricing de bond (dirty/clean price)
- calcul de sensi taux et crédit 
- calcul de VaR avec approche par les sensi
- calcul de VaR avec approche par re-pricing
- calcul de la VaR Monte-Carlo
- 

