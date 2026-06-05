# 🥪 Previsor de Preço de Lanches

🇺🇸 [English version](README.md)

### *Um modelo de Regressão Linear para prever o preço de lanches com base no tipo e no comprimento (cm).*

![Python](https://img.shields.io/badge/Python-3.11-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Regressão%20Linear-green)
![Streamlit](https://img.shields.io/badge/Streamlit-App-red)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange)

---

## 💡 Visão Geral do Projeto

Este projeto foi desenvolvido para explorar como **Machine Learning**, especificamente **Regressão Linear**, pode ser utilizado para prever o preço de lanches com base no **tipo de lanche** e no **comprimento (cm)**.

A ideia surgiu a partir de uma curiosidade simples:

> *“E se eu quisesse um lanche de 20 cm ou 40 cm? Quanto ele custaria?”* 🤔

Muitas redes de fast-food, como o **Subway**, trabalham com tamanhos fixos (**15 cm** e **30 cm**) e, em muitos casos, os preços seguem uma lógica proporcional.

Pensando nisso, o projeto busca resolver esse problema criando um modelo capaz de estimar o preço de **qualquer tamanho de lanche**, mesmo quando os dados disponíveis possuem apenas tamanhos fixos.

O projeto combina:

* 🐍 **Python**
* 🧠 **Machine Learning (Regressão Linear)**
* ⚙️ **Engenharia de Features**
* 🌐 **Interface interativa com Streamlit**
* 📊 **Manipulação e análise de dados**

---

## ✨ Funcionalidades

✅ Previsão de preços utilizando **Regressão Linear**

✅ Suporte para diferentes categorias de lanches

✅ Previsão em tempo real através de uma **interface interativa**

✅ Engenharia de atributos usando **termos de interação**

✅ Validação matemática da proporcionalidade dos preços

✅ Testes automáticos de consistência das previsões

---

## ⚙️ Tecnologias Utilizadas

* 🐍 **Python 3.11+**
* 📦 **Pandas** — manipulação e pré-processamento dos dados
* 🧠 **Scikit-Learn** — treinamento do modelo de regressão linear
* 🌐 **Streamlit** — construção da interface web interativa
* ⚙️ **Poetry** — gerenciamento de dependências e ambiente virtual
* 📈 **NumPy** — cálculos e validações numéricas

---

## 💻 Como Executar o Projeto

### 1️⃣ Clonar o repositório

```bash
git clone https://github.com/marinakallybo/Python-Sandwich-Predictor.git
cd Python-Sandwich-Predictor
```

### 2️⃣ Instalar o Poetry (caso ainda não tenha)

```bash
pip install poetry
```

### 3️⃣ Instalar as dependências

```bash
poetry install
```

### 4️⃣ Executar a aplicação

```bash
poetry run streamlit run app.py
```

Após isso, o Streamlit abrirá automaticamente no navegador. 🎉

---

## 📁 Estrutura do Projeto

```txt
Python-Sandwich-Predictor/
│── app.py                # Aplicação principal em Streamlit
│── lanches.csv           # Base de dados (lanches + preços)
│── README.md             # Documentação do projeto
│── pyproject.toml        # Configuração do Poetry
│── poetry.lock           # Controle das dependências
│── .gitignore            # Arquivos ignorados pelo Git
```

---

## 🍞 Conjunto de Dados

O arquivo `lanches.csv` foi criado com base nos preços de lanches inspirados no **Subway**.

Foram selecionadas as seguintes categorias:

* Frango
* Frango Teriyaki
* Carne Seca com Cream Cheese
* Vegetariano
* Steak Churrasco

Cada lanche possui:

* **Comprimento (15 cm e 30 cm)**
* **Preço proporcional**

A base de dados utiliza **One-Hot Encoding**, onde cada categoria de lanche é representada por colunas binárias (`0` ou `1`), permitindo que o modelo interprete corretamente variáveis categóricas.

Exemplo:

| Frango | Frango Teriyaki | Carne Seca | Vegetariano | Steak Churrasco | Comprimento | Preço |
| ------ | --------------- | ---------- | ----------- | --------------- | ----------- | ----- |
| 1      | 0               | 0          | 0           | 0               | 15          | 18.30 |
| 1      | 0               | 0          | 0           | 0               | 30          | 36.60 |
| 0      | 1               | 0          | 0           | 0               | 15          | 25.20 |
| 0      | 1               | 0          | 0           | 0               | 30          | 44.10 |

---

## 🧠 Como o Modelo Funciona

O projeto utiliza **Regressão Linear Múltipla** com **features de interação** para preservar a proporcionalidade dos preços.

Em vez de utilizar apenas o tipo do lanche e o comprimento separadamente, o modelo cria termos de interação como:

```python
frango_comp = Frango * Comprimento
```

Isso permite que o algoritmo aprenda **como cada centímetro de cada categoria de lanche influencia no preço final**.

O modelo é treinado com:

```python
LinearRegression(fit_intercept=False)
```

Desativar o intercepto garante que:

> **Um lanche de 0 cm tenha preço igual a 0.**

Isso preserva a proporcionalidade matemática perfeita nas previsões.

---

## 🧪 Testes de Proporcionalidade

A aplicação inclui testes para verificar se os preços previstos permanecem matematicamente consistentes com os dados de treino.

Exemplo:

| Sabor  | Comprimento (cm) | Preço Real | Preço Previsto | Diferença | Status |
| ------ | ---------------- | ---------- | -------------- | --------- | ------ |
| Frango | 15               | 18.30      | 18.30          | 0.00      | ✅      |
| Frango | 30               | 36.60      | 36.60          | 0.00      | ✅      |

O modelo utiliza:

```python
np.isclose(error, 0, atol=1e-2)
```

para validar se os erros são praticamente nulos.

---

## 💻 Interface Interativa

A aplicação desenvolvida com **Streamlit** permite que o usuário:

✅ Escolha o tipo de lanche

✅ Informe um comprimento personalizado (**20 cm, 40 cm, etc.**)

✅ Visualize instantaneamente o preço previsto

---

## 👩‍💻 Autora

**Marina Kally**
🔗 [LinkedIn](https://www.linkedin.com/in/marina-kally-695535252)





