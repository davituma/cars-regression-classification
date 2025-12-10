# 🚗 Projeto de Modelagem Estatística: Precificação de Veículos

> **Autores:** Davi Tuma & Elias Bariani
> **Disciplina:** Modelagem Estatística | **Instituição:** CESUPA
> **Professor:** Pedro Girotto

Este repositório contém o projeto prático do 2º Bimestre, focado na aplicação de técnicas estatísticas e de Machine Learning para análise de dados do mercado automotivo.

## 🎯 Objetivos do Projeto

O projeto visa resolver dois problemas de negócio utilizando o dataset *Car Details v3*:

1.  **Regressão (Precificação):** Prever o preço de venda (`selling_price`) de carros usados com base em características técnicas (motor, ano, quilometragem), comparando abordagens lineares e não-lineares.
2.  **Classificação (Segmentação):** Identificar se um veículo possui transmissão **Automática** ou **Manual**, focando na recuperação (Recall) da classe minoritária.

## 📂 Dados e Licença

* **Fonte dos Dados:** [Vehicle Dataset - Kaggle](https://www.kaggle.com/nehalbirla/vehicle-dataset-from-cardekho)
* **Licença:** Open Database License (ODbL)

## 🛠️ Tecnologias Utilizadas

O projeto foi desenvolvido em **Python 3.10+** utilizando as seguintes bibliotecas:
* **Pandas & Numpy:** Manipulação e limpeza de dados.
* **Seaborn & Matplotlib:** Visualização de dados (EDA).
* **Statsmodels:** Regressão Linear Múltipla (OLS) e diagnóstico estatístico.
* **Scikit-Learn:** Regressão Polinomial, Naive Bayes e Regressão Logística.
* **PyCaret:** AutoML, otimização de hiperparâmetros e validação cruzada.

## 📊 Metodologia

O fluxo de trabalho seguiu as seguintes etapas:

1.  **Coleta e Limpeza (EDA):**
    * Tratamento de strings nas colunas `engine`, `max_power` e `mileage`.
    * Aplicação de Log-Transformation no alvo (`selling_price`) para normalizar a distribuição.
    * Testes de Hipótese (Teste T) e visualização gráfica (Pairplots, Heatmaps).
2.  **Modelagem de Regressão (Progressiva):**
    * **Linear Simples:** Baseline com apenas 1 variável.
    * **Polinomial (Grau 2):** Captura de curvas de valorização em carros potentes.
    * **Múltipla (OLS):** Modelo completo com todas as variáveis e análise de significância ($P > |t|$).
3.  **Classificação e Otimização:**
    * Classificação via **Naive Bayes** e **Regressão Logística**.
    * Uso do **PyCaret** para comparar modelos, realizar *tuning* e balanceamento de classes.

## 🚀 Resultados Alcançados

A inclusão de modelos não-lineares e a otimização via PyCaret trouxeram ganhos expressivos:

| Tarefa | Modelo | Métrica Principal | Resultado | Observação |
| :--- | :--- | :--- | :--- | :--- |
| **Regressão** | Polinomial (Apenas Potência) | $R^2$ | 0.55 | Capturou a curvatura, mas faltam dados. |
| **Regressão** | **Linear Múltipla (OLS)** | **$R^2$** | **0.87** | **Excelente ajuste para um modelo linear.** |
| **Regressão** | PyCaret (Extra Trees/LightGBM) | $R^2$ | 0.96 | Melhor performance geral. |
| **Classificação** | Regressão Logística (Base) | Recall (Auto) | 0.52 | Errava metade dos automáticos. |
| **Classificação** | **Regressão Logística (Tunada)** | **Recall (Auto)** | **0.81** | **+55% de ganho na detecção.** |

> **Conclusão:** O modelo final de regressão consegue explicar **96%** da variação de preços do mercado. Na classificação, conseguimos mitigar o problema do desbalanceamento, elevando a detecção de automáticos para um nível operacionalmente seguro.

## 📂 Estrutura do Repositório

```bash
├── Car details v3.csv          # Dataset utilizado (Kaggle)
├── projeto_carros.ipynb        # Notebook com EDA, Regressões e PyCaret
├── requirements.txt            # Dependências do projeto
└── README.md                   # Documentação