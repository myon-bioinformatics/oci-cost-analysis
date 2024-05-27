# Oracle Cloud Infrastructure Cost Analysis

## Overview

This script processes "cost data" from Oracle Cloud Infrastructure (OCI).

The data is sourced from OCI's Cost Management, specifically from the "Cost Analysis" -> "Cost Details" section. 

## Steps

1. **Download Data**:
   - Log in to Oracle Cloud Infrastructure.
   - Navigate to Cost Management -> Cost Analysis -> Cost Details.
   - Click on "Download table as CSV" to obtain the cost data.

2. **Data Processing**:
   - The downloaded CSV data is processed to extract relevant columns: Date (UTC), Block Storage, Compute, Database, Load Balancer, MySQL, Object Storage, Telemetry, Virtual Cloud Network, and Total (all in USD).
   - If the amounts in JPY are converted to USD using an exchange rate (example: 1 USD = 150 JPY).

3. **Script Execution**:
   - The script iterates over the processed data and prints each date along with the total cost in USD.
   - The output format is: `Date (UTC): <date>, Total (USD): <total>`.

## Example

```python
# Define a function to print Date (UTC) and Total (USD) for each row
def print_date_total_oci(dataframe):
    for index, row in dataframe.iterrows():
        print(f"Date (UTC): {row['Date (UTC)']}, Total (USD): {row['Total (USD)']}")

# Call the function to print Date (UTC) and Total (USD) for each row
print_date_total_oci(corrected_df_usd)
```

## Output
```mathmatica
Date (UTC): May 16 2024, Total (USD): 1.3608014053333333
Date (UTC): May 17 2024, Total (USD): 1.699895054
Date (UTC): May 18 2024, Total (USD): 1.699895054
Date (UTC): May 19 2024, Total (USD): 1.699895054
Date (UTC): May 20 2024, Total (USD): 0.20968403153333334
Date (UTC): May 21 2024, Total (USD): 0.060215053760000005
Date (UTC): May 22 2024, Total (USD): 0.060215053760000005
Date (UTC): May 23 2024, Total (USD): 0.055197126613333335
Date (UTC): May 24 2024, Total (USD): 6.785582786666667
```
