# Predicting the re-election of Brazilian mayors: work, public machine, or campaign money?

Final project for the **Artificial Intelligence** course, Computer Science, Universidade Federal do Piauí (UFPI).

**Research question.** Which group of indicators (management performance, public machine, campaign money,
or political context) carries the most information to predict whether a first-term mayor is re-elected,
and does this pattern change with the size and fiscal dependence of the municipality?

**Task.** Supervised binary classification (`reeleito` = 1/0). The goal is **predictive, not causal**.

## Contents

| File | Description |
|---|---|
| `base_final.csv` | Consolidated dataset: 5,622 first-term mayors who ran for re-election in 2020 (2,998) and 2024 (2,624). No names, CPF, voter ID or party labels. |
| `01_construcao_dataset.ipynb` | Builds the dataset from public sources (requires a free Google Cloud project to query Base dos Dados on BigQuery). |
| `02_modelagem_reeleicao.ipynb` | Exploratory analysis, models, block comparison, error analysis and robustness. Runs end-to-end from `base_final.csv`. |

**Open in Google Colab:**
[01 — dataset](https://colab.research.google.com/github/enricotx/reeleicao-prefeitos/blob/main/01_construcao_dataset.ipynb) ·
[02 — modeling](https://colab.research.google.com/github/enricotx/reeleicao-prefeitos/blob/main/02_modelagem_reeleicao.ipynb)

## Data sources

All data are open government data, accessed through [Base dos Dados](https://basedosdados.org):

- **Tribunal Superior Eleitoral (TSE)**: candidates, results, party coalitions and campaign expenses — <https://dadosabertos.tse.jus.br>
- **Secretaria do Tesouro Nacional (FINBRA/SICONFI)**: annual municipal accounts — <https://siconfi.tesouro.gov.br>
- **IBGE**: municipal GDP and population estimates — <https://www.ibge.gov.br>
- **INEP**: IDEB (basic education quality index) — <https://www.gov.br/inep>

Names, CPF and voter ID numbers are used only inside notebook 01 to link the same person across two elections,
and are dropped before the dataset is saved. Party labels are not used as features.

## Reproducing

1. Open notebook 02 in Colab and run all cells (*Runtime → Run all*). It reads `base_final.csv` directly from this repository.
2. To rebuild the dataset from scratch, run notebook 01 with your own Google Cloud project ID (free BigQuery sandbox).

Random seed: 42. Main libraries: pandas, NumPy, scikit-learn, matplotlib (versions printed in notebook 02).

## Acknowledgements

The party succession table (renamings and mergers) and the rule of identifying candidates by voter ID were adapted
from a previous group project in which the author took part: [analiseCandidatos](https://github.com/SoaresDavidson/analiseCandidatos).
