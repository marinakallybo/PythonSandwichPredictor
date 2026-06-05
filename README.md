# 🥪 Sandwich Price Predictor

🇧🇷 [Versão em Português](README.pt-br.md)

### *A Linear Regression model for predicting sandwich prices based on sandwich type and length (cm).*

![Python](https://img.shields.io/badge/Python-3.11-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Linear%20Regression-green)
![Streamlit](https://img.shields.io/badge/Streamlit-App-red)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange)

---

## 💡 Project Overview

This project was developed to explore how **Machine Learning**, specifically **Linear Regression**, can be used to predict sandwich prices based on **sandwich type** and **length (cm)**.

The idea came from a simple curiosity:

> *“What if I wanted a 20 cm or 40 cm sandwich? How much would it cost?”* 🤔

Many sandwich chains, such as **Subway**, sell products in fixed sizes (typically **15 cm** and **30 cm**), where pricing often follows a proportional pattern.

This project attempts to solve that problem by building a predictive model capable of estimating the price of **any sandwich size**, even when the dataset only contains fixed lengths.

The project combines:

* 🐍 **Python**
* 🧠 **Machine Learning (Linear Regression)**
* ⚙️ **Feature Engineering**
* 🌐 **Interactive Web Interface with Streamlit**
* 📊 **Data Processing and Analysis**

---

## ✨ Features

✅ Predict sandwich prices using **Linear Regression**

✅ Support for different sandwich categories

✅ Real-time prediction through an **interactive Streamlit interface**

✅ Feature engineering using **interaction terms**

✅ Mathematical proportionality validation

✅ Automated prediction testing

---

## ⚙️ Technologies Used

* 🐍 **Python 3.11+**
* 📦 **Pandas** — data manipulation and preprocessing
* 🧠 **Scikit-Learn** — Linear Regression model training
* 🌐 **Streamlit** — interactive web interface
* ⚙️ **Poetry** — dependency and virtual environment management
* 📈 **NumPy** — numerical validation and calculations

---

## 💻 How to Run the Project

### 1️⃣ Clone the repository

```bash
git clone https://github.com/marinakallybo/Python-Sandwich-Predictor.git
cd Python-Sandwich-Predictor
```

### 2️⃣ Install Poetry (if not installed)

```bash
pip install poetry
```

### 3️⃣ Install dependencies

```bash
poetry install
```

### 4️⃣ Run the application

```bash
poetry run streamlit run app.py
```

After that, Streamlit will automatically open in your browser. 🎉

---

## 📁 Project Structure

```txt
Python-Sandwich-Predictor/
│── app.py                # Main Streamlit application
│── lanches.csv           # Dataset (sandwiches + prices)
│── README.md             # Project documentation
│── pyproject.toml        # Poetry configuration
│── poetry.lock           # Dependency versions
│── .gitignore            # Ignored files
```

---

## 🍞 Dataset

The dataset (`lanches.csv`) was created based on sandwich pricing inspired by **Subway** products.

The following sandwich categories were included:

* Chicken
* Chicken Teriyaki
* Shredded Beef with Cream Cheese
* Vegetarian
* Steak Barbecue

Each sandwich contains:

* **Length (15 cm and 30 cm)**
* **Proportional pricing**

The dataset uses **One-Hot Encoding**, where each sandwich category is represented by binary columns (`0` or `1`) so the model can properly understand categorical variables.

Example:

| Chicken | Chicken Teriyaki | Shredded Beef | Vegetarian | Steak BBQ | Length | Price |
| ------- | ---------------- | ------------- | ---------- | --------- | ------ | ----- |
| 1       | 0                | 0             | 0          | 0         | 15     | 18.30 |
| 1       | 0                | 0             | 0          | 0         | 30     | 36.60 |
| 0       | 1                | 0             | 0          | 0         | 15     | 25.20 |
| 0       | 1                | 0             | 0          | 0         | 30     | 44.10 |

---

## 🧠 How the Model Works

The project uses **Multiple Linear Regression** with **interaction features** to preserve pricing proportionality.

Instead of training only with sandwich type and length independently, the model creates interaction terms such as:

```python
chicken_comp = Chicken * Length
```

This allows the model to learn **how each centimeter of each sandwich category influences the final price**.

The model is trained using:

```python
LinearRegression(fit_intercept=False)
```

Disabling the intercept guarantees that:

> **A sandwich with 0 cm has a price of 0.**

This preserves perfect mathematical proportionality in predictions.

---

## 🧪 Proportionality Tests

The application includes validation tests to ensure that predicted prices remain mathematically consistent with training data.

Example:

| Flavor  | Length (cm) | Real Price | Predicted Price | Difference | Status |
| ------- | ----------- | ---------- | --------------- | ---------- | ------ |
| Chicken | 15          | 18.30      | 18.30           | 0.00       | ✅      |
| Chicken | 30          | 36.60      | 36.60           | 0.00       | ✅      |

The model checks whether prediction errors are extremely close to zero using:

```python
np.isclose(error, 0, atol=1e-2)
```

---

## 💻 Interactive Interface

The **Streamlit application** allows users to:

✅ Select the sandwich type

✅ Enter a custom sandwich length (20 cm, 40 cm, etc.)

✅ Instantly view the predicted price in real time

---

## 👩‍💻 Author

**Marina Kally**
🔗 LinkedIn: https://www.linkedin.com/in/marina-kally-695535252
