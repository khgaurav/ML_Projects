# Mini Project 1: Cobblestone Gifts Cleaning Project

GitHub repository: https://github.com/Luke-Sanders1/MiniProject1

## Authors

- Omar Gomaa
- Luke Sanders
- Gaurav K Harish

## Overview

This project cleans and analyzes the **Online Retail / E-Commerce Data** dataset, a real transaction dataset from a UK-based non-store online retailer. The company mainly sells unique all-occasion gifts, and many of its customers are wholesalers.

The goal of the project is to take a messy raw sales export and turn it into a clean, reliable completed-sales dataset. The cleaned dataset will then be used to answer business questions about seasonality, best-selling products, markets, customer concentration, order value, returns, cancellations, and overall data quality.

The notebook follows the required project phases from the assignment PDF and demonstrates the required pandas data-wrangling techniques using an object-oriented structure.

## Dataset

Dataset: **Online Retail / E-Commerce Data**

Source: The dataset is publicly available through Kaggle as `carrie1/ecommerce-data` and originally comes from the UCI Machine Learning Repository under the title **Online Retail**.

According to the dataset description, it contains actual transactions occurring between **01/12/2010 and 09/12/2011** for a UK-based and registered non-store online retail company. The company mainly sells unique all-occasion gifts, and many customers are wholesalers.

Acknowledgement: Per the UCI Machine Learning Repository, the data was made available by **Dr. Daqing Chen**, Director of the Public Analytics Group, School of Engineering, London South Bank University.

The raw file is named:

```text
data.csv
```

Important loading note: the file is not UTF-8 encoded. It should be loaded with:

```python
pd.read_csv("data.csv", encoding="ISO-8859-1")
```

The raw `data.csv` file is intentionally not committed to this repository. It should be downloaded separately from Kaggle or UCI, then placed in the project folder before running the notebook.

## Project Structure

The main notebook is:

```text
MiniProject1.ipynb
```

The repository also includes:

```text
README.md
requirements.txt
.gitignore
```

`requirements.txt` lists the Python libraries needed to run the notebook. `.gitignore` prevents raw data files, Python cache files, notebook checkpoints, local virtual environments, and editor files from being committed accidentally.

## Requirements

Install dependencies from `requirements.txt`:

```bash
pip install -r requirements.txt
```

Current `requirements.txt` contents:

```text
pandas
numpy
matplotlib
kagglehub
jupyter
notebook
```

These packages support dataframe processing, plotting, Kaggle dataset access, and running the Jupyter notebook.

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/Luke-Sanders1/MiniProject1.git
cd MiniProject1
```

2. Install the required libraries:

```bash
pip install -r requirements.txt
```

3. Download the dataset.

Option A: Download manually from Kaggle and place `data.csv` in the project folder.

Option B: Use the notebook's Kaggle/KaggleHub download code if Kaggle access is configured.

4. Run the notebook:

```bash
jupyter notebook MiniProject1.ipynb
```

Then run the cells from top to bottom.

## Project Phases

### Phase A — Load & Profile

This phase loads and profiles the raw dataset.

It includes:

- Loading `data.csv` with the correct encoding
- Displaying `head()`, `shape`, `info()`, and `describe()`
- Checking missing values
- Reviewing unique values and category counts
- Surfacing non-product stock codes
- Summarizing `Quantity` and `UnitPrice`
- Creating a country-to-region lookup dataframe

### Phase B — Select & Filter

This phase inspects and filters the raw data.

It includes:

- Slicing with `iloc`
- Creating a unique line-item index
- Retrieving rows with `loc`
- Isolating cancelled invoices
- Identifying non-positive quantities and prices
- Sorting by quantity and line revenue

### Phase C — Clean & Fix

This phase creates the cleaned completed-sales dataset.

It includes:

- Standardizing country labels such as `EIRE` to `Ireland` and `RSA` to `South Africa`
- Converting `Unspecified` country values to missing values
- Renaming columns to snake_case
- Handling missing descriptions and customer IDs
- Dropping unused helper columns
- Removing cancellations, non-product rows, invalid quantities, and invalid prices
- Detecting and removing duplicate rows

The cleaned completed-sales dataframe is stored as:

```python
clean_sales_df
```

### Phase D — Engineer & Summarize

This phase creates analysis-ready features and summaries.

It includes:

- Creating a `revenue` column
- Cleaning descriptions with `apply`
- Flagging cancelled invoices
- Demonstrating a loop/list comprehension over a column
- Grouping sales by country and customer
- Aggregating multiple statistics at once
- Applying custom group summaries
- Resampling revenue by time

### Phase E — Combine

This phase demonstrates combining and enriching data.

It includes:

- Splitting the cleaned data into two time periods
- Recombining the split datasets with `pd.concat()`
- Merging the country-to-region lookup table with the sales data
- Comparing inner joins and left joins
- Identifying countries without region matches

