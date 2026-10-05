# ⚽ Football Match Predictor

Prédiction de l'issue d'un match de football entre deux équipes nationales, avec deux approches comparées dans un même notebook :

1. **Un modèle de Markov caché (HMM)** basé sur l'enchaînement des résultats passés de chaque équipe
2. **Des modèles de machine learning** basés sur le classement FIFA

L'exemple traité est **Maroc (domicile) vs Écosse (extérieur)**.

## 🗂️ Contenu du dépôt

```
football-match-predictor/
├── footballpredictor.ipynb   # notebook complet (données, HMM, machine learning)
├── README.md
└── .gitignore
```

## 📊 Données

Les fichiers CSV ne sont pas inclus dans le dépôt. À télécharger puis à placer en local (adapter les chemins dans le notebook) :

| Fichier | Utilisation |
|---|---|
| `results.csv` | Résultats de matchs internationaux depuis 1872 (filtrés depuis 2000) : approche HMM |
| `international_matches.csv` | Matchs internationaux avec le classement FIFA des deux équipes : approche ML |
| `fifa_ranking-2023-07-20.csv` | Classement FIFA au 20/07/2023 : prédiction du match |

## 🧠 Approche 1 : modèle de Markov caché

- **États** : `W` (victoire), `L` (défaite), `T` (nul)
- **Observation** : `H` (domicile) ou `A` (extérieur)
- Calcul pour chaque équipe des probabilités initiales, de la matrice de transition (résultat → résultat suivant) et de la matrice d'observation (résultat → domicile/extérieur)
- Prédiction avec `hmmlearn` (`CategoricalHMM`), puis combinaison des deux équipes :

| Issue | Probabilité |
|---|---|
| Victoire du Maroc | **0.56** |
| Victoire de l'Écosse | 0.24 |
| Match nul | 0.20 |

## 🤖 Approche 2 : machine learning

**Variables** : `average_rank`, `rank_difference`, `point_difference`, `is_stake` (match officiel ou amical), `is_worldcup`.
**Cible** : `is_won` (victoire de l'équipe à domicile ; le nul est compté comme non-victoire).
**Séparation** : 80 % entraînement / 20 % test.

| Modèle | Accuracy |
|---|---|
| **Régression logistique** | **68.38 %** |
| Naive Bayes | 68.36 % |
| SVM | 68.17 % |
| Random Forest | 63.70 % |
| KNN | 62.88 % |
| Arbre de décision | 59.10 % |

La régression logistique est retenue. Avec une marge de 0.05 autour de 50 %, elle donne pour Maroc vs Écosse une probabilité de victoire du Maroc de **0.53**, soit un **match nul** (le Maroc est 14e, l'Écosse 30e au classement du 20/07/2023).

## 🚀 Installation et utilisation

```bash
git clone https://github.com/Maryame-Abouiba/football-match-predictor.git
cd football-match-predictor
pip install numpy pandas scikit-learn hmmlearn jupyter
jupyter notebook footballpredictor.ipynb
```

Pour prédire un autre match, changez les noms des équipes (`'Morocco'`, `'Scotland'`) dans le notebook.

## 🛠️ Technologies

Python · Pandas · NumPy · scikit-learn · hmmlearn · Jupyter Notebook

## ⚠️ Limites

- L'approche HMM ne tient compte que de la séquence de résultats et du lieu, pas de la force de l'adversaire.
- L'approche ML ne distingue pas le nul de la défaite et se limite à quelques variables issues du classement FIFA.
- Le football est très aléatoire : les sorties sont des probabilités, pas des certitudes.

## 🔮 Pistes d'amélioration

- Prédire les trois classes (victoire / nul / défaite) plutôt qu'un résultat binaire
- Ajouter la forme récente, le type de compétition et le terrain neutre
- Combiner les meilleurs modèles (ensemble) et valider avec un découpage chronologique
- Construire une interface (Streamlit) pour choisir deux équipes

## 👤 Auteure

**Maryame Abouiba** — [GitHub](https://github.com/Maryame-Abouiba)

## 👤 Auteure

**Maryame Abouiba** — [GitHub](https://github.com/Maryame-Abouiba)
