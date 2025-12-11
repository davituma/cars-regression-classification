# 🚗 Projeto de Modelagem Estatística: Precificação de Veículos

> **Autores:** Davi Tuma & Elias Bariani
> **Disciplina:** Modelagem Estatística | **Instituição:** CESUPA
> **Professor:** Pedro Girotto

Este repositório contém o projeto prático do 2º Bimestre, focado na aplicação de técnicas estatísticas e de Machine Learning para análise de dados do mercado automotivo.

## 🎯 Objetivos do Projeto

O projeto visa resolver dois problemas de negócio utilizando o dataset *Car Details v3*:

1.  **Regressão (Precificação):** Prever o preço de venda (`selling_price`) de carros usados com base em características técnicas (motor, ano, quilometragem), comparando abordagens lineares e não-lineares.
2.  **Classificação (Segmentação):** Identificar se um veículo possui transmissão **Automática** ou **Manual**, priorizando o equilíbrio entre precisão e recuperação (*F1-Score*) para evitar falsos positivos.

## 📂 Dados e Licença

* **Fonte dos Dados:** [Vehicle Dataset - Kaggle](https://www.kaggle.com/nehalbirla/vehicle-dataset-from-cardekho)
* **Licença:** Open Database License (ODbL)

## 🛠️ Tecnologias Utilizadas

O projeto foi desenvolvido em **Python 3.10+** utilizando as seguintes bibliotecas:
* **Pandas & Numpy:** Manipulação e limpeza de dados.
* **Seaborn & Matplotlib:** Visualização de dados (EDA).
* **Statsmodels:** Regressão Linear Múltipla (OLS) e diagnóstico estatístico.
* **Scikit-Learn:** Random Forest, Regressão Polinomial e Métricas de Avaliação.
* **PyCaret:** AutoML, otimização de hiperparâmetros (Tuning) e comparação de modelos.

## 📊 Metodologia

O fluxo de trabalho seguiu as seguintes etapas:

1.  **Coleta e Limpeza (EDA):**
    * Tratamento de strings nas colunas `engine`, `max_power` e `mileage`.
    * Aplicação de Log-Transformation no alvo (`selling_price`) para normalizar a distribuição.
    * Testes de Hipótese (Teste T) e visualização gráfica.
2.  **Modelagem de Regressão (Progressiva):**
    * **Linear Simples:** Baseline com apenas 1 variável.
    * **Polinomial (Grau 2):** Captura de curvas de valorização em carros potentes.
    * **Múltipla (OLS):** Modelo completo com análise de significância ($P > |t|$).
3.  **Classificação e Otimização:**
    * Comparação inicial focada em *Recall* (Regressão Logística).
    * **Pivô de Estratégia:** Alteração da métrica alvo para **F1-Score** via PyCaret para reduzir alarmes falsos.
    * Seleção final do **Random Forest Classifier** com balanceamento de classes.

## 🚀 Resultados Alcançados

A evolução das métricas demonstrou que modelos baseados em árvore (Tree-Based) superaram significativamente os modelos lineares neste dataset:

| Tarefa | Modelo | Métrica Principal | Resultado | Observação |
| :--- | :--- | :--- | :--- | :--- |
| **Regressão** | Polinomial (Apenas Potência) | $R^2$ | 0.55 | Capturou a curvatura, mas insuficiente. |
| **Regressão** | Linear Múltipla (OLS) | $R^2$ | 0.87 | Bom ajuste, mas sensível a outliers. |
| **Regressão** | **PyCaret (Extra Trees)** | **$R^2$** | **0.96** | **Melhor performance (Erro médio ~16%).** |
| **Classificação** | Regressão Logística (Inicial) | Precisão | 0.47 | Muitos falsos positivos (ruído alto). |
| **Classificação** | **Random Forest (Final)** | **Precisão** | **0.85** | **Alta confiabilidade com Acurácia de ~95%.** |

> **Conclusão:** O modelo final de regressão explica **96%** da variação de preços. Na classificação, a mudança para o Random Forest eliminou drasticamente os erros de "alarme falso" (redução de 280 para 30 erros), entregando um modelo seguro para produção.

## 📂 Estrutura do Repositório

```bash
├── Car details v3.csv          # Dataset utilizado (Kaggle)
├── projeto_carros.ipynb        # Notebook com EDA, Regressões e PyCaret
├── requirements.txt            # Dependências do projeto
└── README.md                   # Documentação