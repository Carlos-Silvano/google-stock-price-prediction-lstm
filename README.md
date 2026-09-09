# 📈 Previsão de Preços de Ações da Google (GOOGL) com LSTM

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![Keras](https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=keras&logoColor=white)](https://keras.io/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![yfinance](https://img.shields.io/badge/yfinance-Yahoo%20Finance-00833E?style=for-the-badge)](https://pypi.org/project/yfinance/)

Este repositório contém uma implementação prática de **Deep Learning para Séries Temporais**, utilizando redes neurais recorrentes do tipo **LSTM (Long Short-Term Memory)** para prever os preços históricos de fechamento das ações da **Alphabet Inc. (GOOGL)**.

---

## 📌 Sobre o Projeto

A previsão de séries temporais financeiras é um desafio clássico devido à volatilidade e ruído inerentes ao mercado de ações. Redes **LSTM** são especialmente adequadas para essa tarefa por serem capazes de aprender dependências e padrões de longo prazo em sequências temporais.

neste projeto, utilizamos dados históricos do **Yahoo Finance** para treinar um modelo capaz de prever os preços de fechamento (*Close Price*) com base em uma janela histórica de **60 dias**.

---

## 🚀 Funcionalidades e Fluxo de Trabalho

1. **Download Automático dos Dados:**
   - Obtenção dos dados históricos diários de negociação do ativo `GOOGL` via biblioteca `yfinance`.
2. **Pré-processamento de Dados:**
   - Filtro pelo preço de fechamento (*Close*).
   - Normalização dos valores utilizando `MinMaxScaler(feature_range=(0, 1))`.
   - Divisão temporal em conjunto de **Treino (80%)** e **Teste (20%)**, respeitando a ordem cronológica dos dados.
   - Criação de estrutura de dados com janelas deslizantes (*lookback*) de 60 dias.
3. **Arquitetura da Rede Neural (LSTM):**
   - **Camada LSTM 1:** 50 unidades, `return_sequences=True`.
   - **Dropout 1:** Taxa de 20% para prevenção de *overfitting*.
   - **Camada LSTM 2:** 50 unidades, `return_sequences=False`.
   - **Dropout 2:** Taxa de 20%.
   - **Camadas Densas:** Camada intermediária e camada de saída para previsão contínua.
   - **Compilação:** Otimizador `Adam` e função de perda `Mean Squared Error (MSE)`.
4. **Avaliação e Visualização:**
   - Desnormalização dos dados previstos e reais usando `inverse_transform`.
   - Plotagem de gráficos comparativos detalhando o histórico real e as estimativas do modelo.

---

## 📂 Estrutura do Repositório

```text
├── data/                      # Diretório opcional para armazenar datasets locais
├── notebooks/
│   └── google_stock_lstm.ipynb # Jupyter Notebook com a implementação completa
├── src/                       # Código-fonte modularizado (opcional)
├── .gitignore                 # Arquivos ignorados pelo Git
├── README.md                  # Documentação do projeto
└── requirements.txt           # Dependências do projeto


🛠️ Tecnologias e Bibliotecas
Python 3.x

TensorFlow / Keras — Construção e treinamento da rede LSTM

yfinance — Coleta de dados financeiros em tempo real

Pandas & NumPy — Manipulação e estruturação dos dados

Matplotlib — Visualização e geração de gráficos

Scikit-learn — Normalização de dados com MinMaxScaler
