# ⚽ Football Match Predictor

Projet de machine learning qui prédit l'issue d'un match de football (victoire domicile / nul / victoire extérieur) à partir de statistiques historiques.

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)

## 📌 Aperçu

L'objectif est de construire un modèle capable d'estimer le résultat d'un match à partir de données comme la forme récente des équipes, les confrontations directes, les buts marqués/encaissés et l'avantage du terrain.

- **Entrée** : deux équipes, une date, un championnat
- **Sortie** : probabilités de victoire / nul / défaite
- **Modèles testés** : `[Régression logistique, Random Forest, XGBoost, ...]`

## 🗂️ Structure du projet

```
football-match-predictor/
├── data/            # jeux de données bruts et nettoyés
├── notebooks/       # exploration et expérimentations
├── src/             # code source (préparation, features, entraînement)
├── models/          # modèles entraînés sauvegardés
├── requirements.txt
└── README.md
```

> Adaptez cette arborescence à celle du dépôt réel.

## 🚀 Installation

```bash
git clone https://github.com/Maryame-Abouiba/football-match-predictor.git
cd football-match-predictor

python -m venv venv
source venv/bin/activate        # Windows : venv\Scripts\activate

pip install -r requirements.txt
```

## ▶️ Utilisation

```bash
# Entraîner le modèle
python src/train.py

# Prédire un match
python src/predict.py --home "Équipe A" --away "Équipe B"
```

## 📊 Données

- **Source** : `[Kaggle / football-data.co.uk / API-Football ...]`
- **Période** : `[ex. saisons 2015–2024]`
- **Variables principales** : forme récente, buts marqués/encaissés, historique des confrontations, domicile/extérieur

## 🧠 Méthodologie

1. Nettoyage et préparation des données
2. Création de features (moyennes glissantes, différence de forme, etc.)
3. Séparation train/test chronologique (pour éviter la fuite de données)
4. Entraînement et comparaison des modèles
5. Évaluation et sélection du meilleur modèle

## 📈 Résultats

| Modèle | Accuracy | F1-score |
|--------|----------|----------|
| Régression logistique | `XX %` | `XX` |
| Random Forest | `XX %` | `XX` |
| XGBoost | `XX %` | `XX` |

> Le football reste un sport très aléatoire : les prédictions sont des probabilités, pas des certitudes.

## 🛠️ Technologies

- Python, Pandas, NumPy
- Scikit-learn, XGBoost
- Matplotlib / Seaborn
- Jupyter Notebook

## 🔮 Améliorations possibles

- Intégrer les cotes des bookmakers et les statistiques xG
- Prendre en compte les blessures et les compositions
- Déployer une interface web (Streamlit / Flask)

## 🤝 Contribution

Les contributions sont les bienvenues : ouvrez une issue ou proposez une pull request.

## 📄 Licence

Distribué sous licence MIT. Voir le fichier `LICENSE`.

## 👤 Auteure

**Maryame Abouiba** — [GitHub](https://github.com/Maryame-Abouiba)
