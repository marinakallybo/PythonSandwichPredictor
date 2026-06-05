# 🥪 Sandwich Price Predictor

🇧🇷 [Versão em Português](README.pt-br.md)

### *A Linear Regression model to predict sandwich prices based on type and length (cm).*

---

## 💡 Main Idea

Everything started with a simple curiosity:

> “What if I wanted a 20cm or even a 40cm sandwich? How much would it cost?” 🤔

We know that **Subway** usually offers sandwiches in **15cm** and **30cm** sizes, and in some cases, the 30cm option costs **exactly twice** as much as the 15cm one.

That made me wonder:

> “Could I build a model capable of automatically calculating the proportional price of any sandwich size?”

That’s how the **Sandwich Price Predictor** was born — a project that combines **Python + Machine Learning (Linear Regression)** to predict the price of different sandwich types based on their length.

---

## ⚙️ Technologies Used

* 🐍 **Python 3.11+**
* 📦 **Pandas** — data manipulation and analysis
* 🧠 **Scikit-learn** — building and training the linear regression model
* 🌐 **Streamlit** — interactive web interface
* ⚙️ **Poetry** — dependency and virtual environment management

---

## 💻 Running the Project

### 🔹 1. Clone the repository

```bash
git clone https://github.com/marinakallybo/Previsor-Pre-os-Lanches.git
cd Previsor-Pre-os-Lanches
```

### 🔹 2. Install Poetry (if not installed)

```bash
pip install poetry
```

### 🔹 3. Install dependencies

```bash
poetry install
```

### 🔹 4. Activate the virtual environment

```bash
poetry shell
```

### 🔹 5. Run the app

```bash
streamlit run app.py
```

After that, Streamlit will automatically open in your browser. 🎉

---

## 🧩 Project Structure

```text
📂 PROJECT-ML/
├── 📁 .venv/               # Virtual environment (created automatically by Poetry)
├── 📁 src/                 # Helper modules (optional)
├── 📁 tests/               # Automated tests
│
├── 📄 app.py               # Main application (model + interface)
├── 📄 lanches.csv          # Dataset (sandwiches + prices)
├── 📄 pyproject.toml       # Poetry configuration and dependencies
├── 📄 poetry.lock          # Exact dependency versions
└── 📄 README.md            # Project documentation
```

---

## 🍞 Dataset

The `lanches.csv` dataset was created based on **Subway sandwiches**.

The project includes **5 sandwich types**:

* Chicken
* Chicken Teriyaki
* Shredded Beef with Cream Cheese
* Vegetarian
* Steak Barbecue

Each sandwich contains values for **length (15cm and 30cm)** and **proportional price**.

The dataset uses **One-Hot Encoding**, where each sandwich type is represented as a column containing `0` or `1`. This helps the model correctly understand categorical variables.

Example:

| Chicken | Chicken Teriyaki | Shredded Beef + Cream Cheese | Vegetarian | Steak Barbecue | Length | Price |
| :-----: | :--------------: | :--------------------------: | :--------: | :------------: | :----: | :---: |
|    1    |         0        |               0              |      0     |        0       |   15   | 18.30 |
|    1    |         0        |               0              |      0     |        0       |   30   | 36.60 |
|    0    |         1        |               0              |      0     |        0       |   15   | 25.20 |
|    0    |         1        |               0              |      0     |        0       |   30   | 44.10 |

---

## 🧠 Model Logic

The model uses **Multiple Linear Regression**, ensuring that the **price increases proportionally** to the sandwich length.

It creates interaction terms between sandwich type and length, such as:

```python
chicken_length = Chicken * Length
```

These interaction columns allow the model to learn how **each centimeter of each sandwich type** influences the final price.

The model is trained with:

```python
LinearRegression(fit_intercept=False)
```

This guarantees that the predicted price for a **0cm sandwich is $0**, preserving perfect proportionality.

---

## 🧪 Proportionality Tests

The project includes tests to verify that predicted prices are **identical** to training data prices, ensuring mathematical consistency.

Example:

| Flavor  | Length (cm) | Real Price | Predicted Price | Difference | Status |
| :------ | :---------: | :--------: | :-------------: | :--------: | :----: |
| Chicken |      15     |    18.30   |      18.30      |    0.00    |    ✅   |
| Chicken |      30     |    36.60   |      36.60      |    0.00    |    ✅   |

---

## 💻 Interactive Interface

The **Streamlit** app allows users to:

✅ Choose the sandwich type

✅ Enter any desired length (20cm, 40cm, etc.)

✅ Instantly see the predicted price in real time

---

## ✨ Author

**Marina Kally**
🔗 LinkedIn: https://www.linkedin.com/in/marina-kally-695535252
