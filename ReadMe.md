# My First project as a Data Engineer
## ETL Pipeline
### Python


import pandas as pd
from sqlalchemy import create_engine

def run_etl():
    # 1. EXTRACT: Read raw data from a source file
    raw_df = pd.read_csv("raw_sales.csv")
    
    # 2. TRANSFORM: Clean missing values and apply business logic
    # Fill empty revenue fields with zero and filter for major sales
    raw_df["revenue"] = raw_df["revenue"].fillna(0)
    transformed_df = raw_df[raw_df["revenue"] > 100]
    
    # 3. LOAD: Save data to a destination database
    db_engine = create_engine("sqlite:///sales_warehouse.db")
    transformed_df.to_sql("cleaned_sales", db_engine, if_exists="append", index=False)
    print("ETL Job completed successfully.")

if __name__ == "__main__":
    run_etl()
    
