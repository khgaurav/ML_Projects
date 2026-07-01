# Data Dictionary — clean_online_retail.csv

| Column | Description |
|---|---|
| invoice_no | Invoice number for the transaction. Cancelled invoices were removed from the completed-sales dataset. |
| stock_code | Product stock code. Non-product stock codes such as POST, DOT, M, BANK CHARGES, and AMAZONFEE were removed. |
| description | Cleaned product description. Blank or missing descriptions were removed. |
| quantity | Number of units sold. Only positive quantities are kept. |
| invoice_date | Transaction date and time. Parsed as a datetime for time-based analysis. |
| unit_price | Price per unit in British pounds. Only positive prices are kept. |
| customer_id | Customer identifier. Missing customer IDs are marked as Unknown. |
| country | Customer country. Selected labels were standardized, such as EIRE to Ireland and RSA to South Africa. |
| revenue | Line revenue calculated as quantity × unit_price. |
| region | Region assigned using the country-to-region lookup table. |