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
| `reeleicao_prefeitos.ipynb` | Notebook único e autocontido (código + relatório técnico). **Parte A:** constrói a base a partir de fontes públicas. **Parte B:** análise exploratória, modelos, comparação entre blocos de variáveis, análise de erros, robustez e conclusões. |

**Abrir no Google Colab:** [reeleicao_prefeitos.ipynb](https://colab.research.google.com/github/enricotx/reeleicao-prefeitos/blob/main/reeleicao_prefeitos.ipynb)

### Fontes de dados

Todos os dados são dados abertos do governo, acessados pela [Base dos Dados](https://basedosdados.org):

- **Tribunal Superior Eleitoral (TSE):** candidatos, resultados, coligações e despesas de campanha — <https://dadosabertos.tse.jus.br>
- **Secretaria do Tesouro Nacional (FINBRA/SICONFI):** contas anuais dos municípios — <https://siconfi.tesouro.gov.br>
- **IBGE:** PIB dos municípios e estimativas de população — <https://www.ibge.gov.br>
- **INEP:** IDEB (Índice de Desenvolvimento da Educação Básica) — <https://www.gov.br/inep>

Nome, CPF e título de eleitor são usados apenas dentro da Parte A do notebook, para ligar a mesma pessoa entre duas eleições, e são descartados antes de a base ser salva. A sigla do partido não é usada como variável.

### Como reproduzir

1. Abra o notebook no Colab e execute todas as células (*Ambiente de execução → Executar tudo*). Com `CONSTRUIR_BASE = False` (padrão), a Parte A é pulada e a Parte B lê o `base_final.csv` direto deste repositório; não precisa de conta no Google Cloud.
2. Para reconstruir a base do zero, troque para `CONSTRUIR_BASE = True` (seção 0) e informe o ID do seu próprio projeto no Google Cloud na seção A.1 (modo *sandbox* gratuito do BigQuery).

Semente aleatória: 42. Principais bibliotecas: pandas, NumPy, scikit-learn e matplotlib (as versões são impressas na seção 0 do notebook).

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
| `reeleicao_prefeitos.ipynb` | Single self-contained notebook (code + technical report). **Part A:** builds the dataset from public sources. **Part B:** exploratory analysis, models, feature-block comparison, error analysis, robustness and conclusions. |

The notebook is written in Portuguese. **Open in Google Colab:** [reeleicao_prefeitos.ipynb](https://colab.research.google.com/github/enricotx/reeleicao-prefeitos/blob/main/reeleicao_prefeitos.ipynb)

### Data sources

All data are open government data accessed through [Base dos Dados](https://basedosdados.org): the Superior Electoral Court (TSE), the National Treasury (FINBRA/SICONFI), IBGE (municipal GDP and population) and INEP (IDEB). Names, CPF and voter ID numbers are used only inside Part A of the notebook to link the same person across two elections, and are dropped before the dataset is saved. Party labels are not used as features.

### Reproducing

1. Open the notebook in Colab and run all cells. With `CONSTRUIR_BASE = False` (default), Part A is skipped and Part B reads `base_final.csv` directly from this repository; no Google Cloud account is needed.
2. To rebuild the dataset from scratch, set `CONSTRUIR_BASE = True` (section 0) and enter your own Google Cloud project ID in section A.1 (free BigQuery sandbox).

Random seed: 42. Main libraries: pandas, NumPy, scikit-learn, matplotlib.

### Acknowledgements

The party succession table and the rule of identifying candidates by voter ID were adapted from a previous group project in which the author took part: [analiseCandidatos](https://github.com/SoaresDavidson/analiseCandidatos).
