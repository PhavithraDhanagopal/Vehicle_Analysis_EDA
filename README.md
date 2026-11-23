# Vehicle Sales and Price Trend Analysis

A beginner-friendly Exploratory Data Analysis (EDA) project analyzing used vehicle sales, specifications, and price patterns.

---

## Project Objective

> "To explore vehicle prices, manufacturing years, mileage, fuel types, transmission, and other vehicle characteristics using Exploratory Data Analysis and identify patterns and trends in vehicle selling prices."

This project is tailored as an introductory college EDA assignment, focusing strictly on data inspection, descriptive statistics, cleaning, feature preparation, and visualization without machine learning or predictive modeling.

---

## Dataset Description & Source

- **Dataset Source:** Kaggle ([Vehicle Dataset from Cardekho - Car details v3](https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho))
- **File Location:** `data/Car details v3.csv`
- **Initial Shape:** 8,128 rows × 13 columns

### Main Columns Used

| Column | Data Type (Raw) | Description |
|---|---|---|
| `name` | Object (String) | Full car name (used to extract brand) |
| `year` | Integer | Manufacturing year (used to calculate vehicle age) |
| `selling_price` | Integer | Listing price in Indian Rupees (INR) |
| `km_driven` | Integer | Total distance travelled in kilometres |
| `fuel` | Object (String) | Fuel type: Diesel, Petrol, CNG, LPG |
| `seller_type` | Object (String) | Seller category: Individual, Dealer, Trustmark Dealer |
| `transmission` | Object (String) | Transmission type: Manual, Automatic |
| `owner` | Object (String) | Ownership history: First Owner, Second Owner, etc. |
| `mileage` | Object (String) | Fuel economy with units (`kmpl` or `km/kg`) |
| `engine` | Object (String) | Engine displacement with unit (`CC`) |
| `max_power` | Object (String) | Power output with unit (`bhp`) |
| `torque` | Object (String) | Engine torque (retained unchanged due to inconsistent units) |
| `seats` | Float | Seating capacity |

---

## EDA Steps Performed

1. **Dataset Overview & Structural Understanding:**
   - Checked dataset dimensions, column names, data types, and previewed records.
2. **Data Quality & Integrity Inspection:**
   - Identified missing values across columns (`mileage`, `engine`, `max_power`, `torque`, and `seats` each had ~221 missing entries).
   - Identified and removed 1,202 exact duplicate listings, leaving 6,926 unique records.
3. **Data Cleaning & Safe Extraction:**
   - Extracted numeric values from string columns: `mileage_num` (kmpl), `engine_num` (CC), and `max_power_num` (bhp).
   - Preserved `torque` without forced conversion due to inconsistent mixed units (Nm vs. kgm@rpm).
4. **Feature Preparation:**
   - Derived `vehicle_age` using the maximum dataset year (`2020 - year`) to avoid system clock dependency.
   - Extracted `brand` from the `name` column (e.g., Maruti, Hyundai, Honda).
5. **Descriptive Statistics:**
   - Calculated mean, median, standard deviation, quartiles, and frequency counts for categorical attributes.
6. **Univariate Analysis:**
   - Examined individual distributions of selling price, vehicle year, kilometres driven, top brands, fuel types, and transmission modes.
7. **Bivariate & Multivariable Analysis:**
   - Explored relationships between selling price and fuel type, transmission, manufacturing year, kilometres driven, and vehicle age.
   - Evaluated correlation matrix across all numeric features.
8. **Synthesis & Reporting:**
   - Summarized concrete, data-backed findings and actionable conclusions.

---

## Visualizations Created

- **Selling Price Distribution:** Histogram and Boxplot highlighting right-skewness and outliers.
- **Manufacturing Year Distribution:** Bar chart showing vehicle counts across manufacturing years.
- **Kilometres Driven Distribution:** Dual histogram comparing the full range against the 95th percentile.
- **Top 15 Vehicle Brands:** Bar chart depicting market presence and listing frequencies.
- **Fuel Type Composition:** Bar chart and pie chart showing vehicle distribution across fuel types.
- **Transmission Mode Share:** Bar chart and pie chart illustrating Manual vs. Automatic proportion.
- **Average Price by Fuel Type:** Bar chart comparing average selling prices across Diesel, Petrol, CNG, and LPG.
- **Average Price by Transmission:** Bar chart highlighting the price premium for Automatic vehicles.
- **Price Trend by Year:** Trend plot showing how average selling price increases with newer models.
- **Selling Price vs. Kilometres Driven:** Scatter plot demonstrating depreciation trends.
- **Median Price by Vehicle Age:** Bar chart illustrating price drop over car lifespan.
- **Price Distribution by Fuel Type:** Boxplot with 95th percentile capping for clear quartile viewing.
- **Price Distribution by Transmission:** Boxplot contrasting Manual vs. Automatic spread.
- **Average Price by Seller Type:** Comparison across Individuals, Dealers, and Trustmark Dealers.
- **Average Price by Owner Category:** Breakdown across first, second, third, and fourth+ owners.
- **Correlation Heatmap:** Lower-triangle matrix showing correlation coefficients for all numerical variables.
- **Selling Price vs. Max Power:** Scatter plot demonstrating the strong positive relationship between engine output and price.
- **Top 10 Brands Average Price:** Comparative bar chart of average pricing among the 10 most common brands.

---

## Key Findings

1. **Price Skewness:**
   - The median selling price is ₹4,50,000, while the mean is ₹6,38,272 (in the raw dataset), indicating positive skewness caused by high-end luxury vehicles.
2. **Brand Popularity:**
   - Maruti is the dominant brand in the dataset (2,448 listings in raw data), followed by Hyundai.
3. **Transmission Price Premium:**
   - Automatic vehicles represent only ~12.9% of listings but command an average price of ~₹18.7 Lakhs, compared to ~₹4.55 Lakhs for Manual vehicles (~4× difference).
4. **Fuel Type Price Comparison:**
   - Diesel vehicles command the highest average selling price (~₹7.91 Lakhs), followed by Petrol (~₹4.62 Lakhs), CNG (~₹3.01 Lakhs), and LPG (~₹2.00 Lakhs).
5. **Vehicle Age & Mileage Impact:**
   - Vehicle age is negatively correlated with selling price (approx. −0.414).
   - Kilometres driven shows a moderate negative correlation with price (approx. −0.226).
6. **Engine Power Correlation:**
   - Maximum power (`max_power_num`) showed the strongest positive correlation with selling price (approx. +0.748).

---

## Tools & Libraries Used

- **Python 3**
- **Pandas** — Data manipulation and aggregation
- **NumPy** — Numerical operations and array manipulation
- **Matplotlib** — Core visualization and custom plotting
- **Seaborn** — Statistical graphics and aesthetic themes

---

## How to Run the Notebook

### 1. Running Locally (Jupyter Lab / VS Code / Jupyter Notebook)

1. Open your terminal in the project directory:
   ```bash
   cd D:\Veicle_Sales_eda
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Launch Jupyter:
   ```bash
   jupyter notebook vehicle_analysis.ipynb
   ```
4. Run all cells sequentially. The code automatically detects `data/Car details v3.csv`.

### 2. Running in Google Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Click **File** → **Upload notebook** and choose `vehicle_analysis.ipynb`.
3. In the left sidebar of Colab, click the **Files (folder icon)**.
4. Upload `Car details v3.csv` directly into `/content/`.
   - Alternatively, create a `data/` folder in Colab and upload the CSV inside it.
5. Click **Runtime** → **Run all**.
   - The dataset loader in Cell 5 checks both `data/Car details v3.csv` and `/content/Car details v3.csv` seamlessly.
