# online-retail-cleaning

This repository documents the data preprocessing steps applied to an online retail transaction dataset.

### Dataset

The dataset contains transactional information from an online retailer, including attributes like `StockCode`, `Description`, `Quantity`, `UnitPrice`, `CustomerID`, `InvoiceDate`, and `Country`. Initial exploration revealed challenges such as missing values (especially `CustomerID` and `Description`), outliers (including negative `Quantity` values representing cancellations/returns), and categorical features needing transformation.

### Preprocessing Steps Summary

The following key preprocessing steps were performed using primarily Pandas (potentially supplemented by analysis in Excel):

1.  **Descriptive Statistics:** Initial analysis performed using Pandas (`.info()`, `.describe()`) and Excel to understand data distribution and identify potential issues.
2.  **Missing Value Handling:**
    * Mapped missing `Country` values using known `CustomerID`-Country relationships.
    * Imputed missing `UnitPrice` values using the average price for the corresponding `StockCode`.
    * Dropped rows with missing `CustomerID`, `InvoiceDate`, or `Quantity` as these were deemed essential for meaningful analysis or modeling.
3.  **Outlier Removal & Standardization:**
    * Filtered out non-product transactions based on specific `StockCode` values (e.g., 'POSTAGE', 'BANK CHARGES', 'M') and suspect `Description` entries (e.g., starting with '?').
    * Removed rows with negative `Quantity` values, as these typically represent returns or cancellations.
    * Standardized `Country` names (e.g., 'EIRE' to 'Ireland', 'RSA' to 'South Africa') and removed entries like 'Unspecified'.
4.  **Feature Scaling:**
    * Applied Standardization (Z-score normalization) to the `Quantity` and `UnitPrice` columns to address their large ranges and differing units, making them more suitable for distance-based or gradient-based ML algorithms.

The resulting processed dataset is intended to be cleaner, more consistent, and better structured for further exploratory data analysis or building predictive models.
