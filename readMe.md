# 🚗 Projeto de Modelagem Estatística: Precificação de Veículos

> **Disciplina:** Modelagem Estatística | **Instituição:** CESUPA
> **Professor:** Pedro Girotto

Este repositório contém o projeto prático do 2º Bimestre, focado na aplicação de técnicas estatísticas e de Machine Learning para análise de dados do mercado automotivo.

## 🎯 Objetivos do Projeto

O projeto visa resolver dois problemas de negócio utilizando o dataset *Car Details v3*:

1.  **Regressão (Precificação):** Prever o preço de venda (`selling_price`) de carros usados com base em características técnicas (motor, ano, quilometragem), utilizando interpretação estatística de coeficientes.
2.  **Classificação (Segmentação):** Identificar se um veículo possui transmissão **Automática** ou **Manual**, focando na recuperação (Recall) da classe minoritária.

## 🛠️ Tecnologias Utilizadas

O projeto foi desenvolvido em **Python 3.10+** utilizando as seguintes bibliotecas obrigatórias:
* **Pandas & Numpy:** Manipulação e limpeza de dados.
* **Seaborn & Matplotlib:** Visualização de dados (EDA).
* **Statsmodels:** Regressão Linear Múltipla (OLS) e diagnóstico estatístico (P-valores).
* **Scikit-Learn:** Modelos de Machine Learning (Baseline).
* **PyCaret:** AutoML, otimização de hiperparâmetros e validação cruzada.

## 📊 Metodologia

O fluxo de trabalho seguiu as seguintes etapas:

1.  **Coleta e Limpeza (EDA):**
    * Tratamento de strings nas colunas `engine`, `max_power` e `mileage` (remoção de unidades "CC", "bhp", "kmpl").
    * Remoção de valores nulos e inconsistentes.
    * Análise de correlação e visualização gráfica (Boxplots, Scatterplots).
2.  **Modelagem Estatística (Baseline):**
    * Regressão via **Statsmodels (OLS)** para análise de significância das variáveis ($P > |t|$).
    * Classificação via **Naive Bayes** e **Regressão Logística**.
3.  **Otimização (AutoML):**
    * Uso do **PyCaret** para comparar modelos e realizar *tuning*.
    * Aplicação de balanceamento de classes (`fix_imbalance`) para corrigir o viés na detecção de carros automáticos.

## 🚀 Resultados Alcançados

A otimização trouxe ganhos expressivos em relação ao baseline inicial:

| Tarefa | Métrica | Modelo Inicial (Baseline) | Modelo Otimizado (PyCaret) | Ganho |
| :--- | :--- | :--- | :--- | :--- |
| **Regressão** | $R^2$ | 0.68 (Linear OLS) | **0.96 (LightGBM)** | +41% |
| **Classificação** | Recall (Automático) | 0.52 (Reg. Logística) | **0.81 (Reg. Logística Tunada)** | +55% |

> **Insight de Negócio:** O modelo final consegue explicar 96% da variação de preços do mercado e identificar corretamente 80% dos carros automáticos, superando as limitações dos modelos lineares simples.

## 📂 Estrutura do Repositório

```bash
├── Car details v3.csv          # Dataset utilizado (Kaggle)
├── projeto_veiculos.ipynb      # Notebook com EDA, Modelagem e Relatório
├── requirements.txt            # Dependências do projeto
└── README.md                   # DocumentaçãoS