# Customer Shopping Analysis

This repository explores customer shopping behaviors using the **Customer Shopping Dataset** from Kaggle. The project cleans raw transaction data, loads it into a relational database for downstream analytics, and summarizes insights such as category performance, demographic trends, and seasonal revenue patterns.

## Repository contents

- `customer_shopping_data.csv` — Source dataset (99,457 rows × 10 columns) with customer transactions collected across multiple shopping malls.
- `acquire_data.ipynb` — Notebook to download the dataset from Kaggle, perform basic cleaning, and load records into a MySQL database table.
- `data_analysis.xlsx` — Excel workbook with aggregated metrics and visualizations.
- `project_summary.docx` — Written summary of the analytical findings and recommendations.
- `Data Analysis Report.docx` — Supporting documentation for the analysis.

## Data dictionary

The CSV file includes the following columns:

| Column | Description |
| --- | --- |
| `invoice_no` | Transaction identifier. |
| `customer_id` | Unique customer identifier. |
| `gender` | Customer gender. |
| `age` | Customer age in years. |
| `category` | Purchased product category (e.g., Clothing, Shoes, Books). |
| `quantity` | Units purchased. |
| `price` | Unit price in local currency. |
| `payment_method` | Payment type (Cash, Debit Card, Credit Card). |
| `invoice_date` | Purchase date in `DD/MM/YYYY` format. |
| `shopping_mall` | Mall where the purchase occurred. |

## Key insights (from `project_summary.docx`)

- **Top categories:** Clothing and Shoes drive the highest revenue, especially in malls like Istinye Park and Forum Istanbul, while Books and Technology lag behind.【F:project_summary.docx†plaintext】  
- **Customer mix:** Revenue is nearly evenly split between male and female shoppers, supporting gender-neutral marketing strategies.【F:project_summary.docx†plaintext】  
- **Seasonality:** Revenue peaks in November–December and softens in July–August; revenue has grown steadily from 2022 to 2023.【F:project_summary.docx†plaintext】

## Running the notebook

1. Install dependencies (Python 3.10+ recommended):
   ```bash
   pip install kagglehub pandas mysql-connector-python
   ```
2. Open and run `acquire_data.ipynb` in Jupyter or VS Code.
3. Update the MySQL connection settings in the notebook before executing database cells. Avoid committing credentials back to the repository.
4. The notebook:
   - Downloads the Kaggle dataset via `kagglehub`.
   - Performs light cleaning (duplicate checks, null checks, date parsing, and sorting).
   - Creates a `Transactions` table and inserts all rows into MySQL for analysis.【F:acquire_data.ipynb†plaintext】

## Quick start: explore the dataset locally

```python
import pandas as pd
df = pd.read_csv("customer_shopping_data.csv")
df["invoice_date"] = pd.to_datetime(df["invoice_date"], format="%d/%m/%Y")
print(df.head())
```

## Source

Dataset: [Customer Shopping Dataset on Kaggle](https://www.kaggle.com/datasets/mehmettahiraslan/customer-shopping-dataset)
