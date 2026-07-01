# Cleaning Decisions Log

- Kept the raw dataframe unchanged and created separate working and cleaned dataframes.
- Loaded the raw CSV using ISO-8859-1 encoding because the file is not UTF-8.
- Standardized `EIRE` to `Ireland`.
- Standardized `RSA` to `South Africa`.
- Converted `Unspecified` country values to missing values.
- Removed invoices starting with `C` from the completed-sales dataset because they represent cancellations.
- Removed rows where `quantity <= 0` because they do not represent completed sales.
- Removed rows where `unit_price <= 0` because zero or negative prices are not valid completed-sale prices.
- Removed non-product stock codes: `POST`, `DOT`, `M`, `BANK CHARGES`, and `AMAZONFEE`.
- Removed missing or blank product descriptions because product-level analysis requires usable product names.
- Filled missing `customer_id` values as `Unknown` to preserve valid sales rows.
- Excluded `Unknown` customers from customer-level analysis when needed.
- Removed exact duplicate rows using `drop_duplicates()`.
- Added `revenue` as `quantity × unit_price`.
- Merged country-region lookup data into the cleaned dataset for regional market analysis.