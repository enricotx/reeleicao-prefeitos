# Previsão de reeleição de prefeitos brasileiros: trabalho, máquina pública ou dinheiro de campanha?

[Português](#português) · [English](#english)

## Português

Projeto final da disciplina de **Inteligência Artificial** do curso de Ciência da Computação da Universidade Federal do Piauí (UFPI).

**Pergunta de pesquisa.** Qual grupo de indicadores (desempenho da gestão, máquina pública, dinheiro de campanha ou contexto político) carrega mais informação para prever se um prefeito de primeiro mandato será reeleito, e esse padrão muda conforme o porte e a dependência fiscal do município?

**Tarefa.** Classificação binária supervisionada (`reeleito` = 1/0). O objetivo é **preditivo, não causal**.

### Conteúdo

| Arquivo | Descrição |
|---|---|
| `base_final.csv` | Base consolidada: 5.622 prefeitos de primeiro mandato que disputaram a reeleição em 2020 (2.998) e 2024 (2.624). Sem nome, CPF, título de eleitor ou sigla de partido. |
| `01_construcao_dataset.ipynb` | Constrói a base a partir de fontes públicas (exige um projeto gratuito no Google Cloud para consultar a Base dos Dados no BigQuery). |
| `02_modelagem_reeleicao.ipynb` | Análise exploratória, modelos, comparação entre blocos de variáveis, análise de erros e robustez. Roda do início ao fim a partir do `base_final.csv`. |

**Abrir no Google Colab:**
[01 — construção da base](https://colab.research.google.com/github/enricotx/reeleicao-prefeitos/blob/main/01_construcao_dataset.ipynb) ·
[02 — modelagem](https://colab.research.google.com/github/enricotx/reeleicao-prefeitos/blob/main/02_modelagem_reeleicao.ipynb)

### Fontes de dados

Todos os dados são dados abertos do governo, acessados pela [Base dos Dados](https://basedosdados.org):

- **Tribunal Superior Eleitoral (TSE):** candidatos, resultados, coligações e despesas de campanha — <https://dadosabertos.tse.jus.br>
- **Secretaria do Tesouro Nacional (FINBRA/SICONFI):** contas anuais dos municípios — <https://siconfi.tesouro.gov.br>
- **IBGE:** PIB dos municípios e estimativas de população — <https://www.ibge.gov.br>
- **INEP:** IDEB (Índice de Desenvolvimento da Educação Básica) — <https://www.gov.br/inep>

Nome, CPF e título de eleitor são usados apenas dentro do notebook 01, para ligar a mesma pessoa entre duas eleições, e são descartados antes de a base ser salva. A sigla do partido não é usada como variável.

### Como reproduzir

1. Abra o notebook 02 no Colab e execute todas as células (*Ambiente de execução → Executar tudo*). Ele lê o `base_final.csv` direto deste repositório.
2. Para reconstruir a base do zero, execute o notebook 01 com o ID do seu próprio projeto no Google Cloud (modo *sandbox* gratuito do BigQuery).

Semente aleatória: 42. Principais bibliotecas: pandas, NumPy, scikit-learn e matplotlib (as versões são impressas no notebook 02).

### Agradecimentos

A tabela de sucessão de partidos (renomeações e fusões) e a regra de identificar candidatos pelo título de eleitor foram adaptadas de um trabalho anterior em grupo do qual o autor participou: [analiseCandidatos](https://github.com/SoaresDavidson/analiseCandidatos).

---

## English

Final project for the **Artificial Intelligence** course, Computer Science, Universidade Federal do Piauí (UFPI).

**Research question.** Which group of indicators (management performance, public machine, campaign money, or political context) carries the most information to predict whether a first-term mayor is re-elected, and does this pattern change with the size and fiscal dependence of the municipality?

**Task.** Supervised binary classification (`reeleito` = 1/0). The goal is **predictive, not causal**.

### Contents

| File | Description |
|---|---|
| `base_final.csv` | Consolidated dataset: 5,622 first-term mayors who ran for re-election in 2020 (2,998) and 2024 (2,624). No names, CPF, voter ID or party labels. |
| `01_construcao_dataset.ipynb` | Builds the dataset from public sources (requires a free Google Cloud project to query Base dos Dados on BigQuery). |
| `02_modelagem_reeleicao.ipynb` | Exploratory analysis, models, feature-block comparison, error analysis and robustness. Runs end-to-end from `base_final.csv`. |

The notebooks are written in Portuguese. Links to open them in Google Colab are in the Portuguese section above.

### Data sources

All data are open government data accessed through [Base dos Dados](https://basedosdados.org): the Superior Electoral Court (TSE), the National Treasury (FINBRA/SICONFI), IBGE (municipal GDP and population) and INEP (IDEB). Names, CPF and voter ID numbers are used only inside notebook 01 to link the same person across two elections, and are dropped before the dataset is saved. Party labels are not used as features.

### Reproducing

1. Open notebook 02 in Colab and run all cells. It reads `base_final.csv` directly from this repository.
2. To rebuild the dataset from scratch, run notebook 01 with your own Google Cloud project ID (free BigQuery sandbox).

Random seed: 42. Main libraries: pandas, NumPy, scikit-learn, matplotlib.

### Acknowledgements

The party succession table and the rule of identifying candidates by voter ID were adapted from a previous group project in which the author took part: [analiseCandidatos](https://github.com/SoaresDavidson/analiseCandidatos).
