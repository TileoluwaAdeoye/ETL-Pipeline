# My First project as a Data Engineer
## ETL Pipeline
### Python


University ETL Pipeline

A simple Python Extract-Transform-Load (ETL) pipeline that fetches university data from an API, filters for California universities, and stores the results in a SQLite database.

📋 Project Overview

This project demonstrates a basic ETL workflow:

Extract: Retrieves university data from the HipoLabs Universities API
Transform: Filters universities by location (California) and formats data
Load: Stores the processed data into a SQLite database
🎯 Features
Fetches real-time university data from a public API
Filters universities by state/region
Converts nested list data into comma-separated strings
Stores results in a portable SQLite database
Includes error handling and data validation
📦 Requirements
Python 3.7+
requests - for API calls
pandas - for data manipulation
sqlalchemy - for database operations
🚀 Installation
Clone the repository:
bash
git clone https://github.com/yourusername/university-etl-pipeline.git
cd university-etl-pipeline
Create a virtual environment (recommended):
bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
Install dependencies:
bash
pip install -r requirements.txt
💻 Usage

Run the ETL pipeline:

bash
python etl_project.py
Expected Output
Total Number of universities from API: 5722
Number of universities in California: 342

A SQLite database file my_lite_store.db will be created in the project directory with the filtered data.

📊 Data Structure

The output table cal_uni contains the following columns:

Column	Type	Description
name	string	University name
domains	string	Comma-separated domain names
country	string	Country (United States)
web_pages	string	Comma-separated web page URLs
🔍 How It Works
Extract
Calls the HipoLabs API endpoint: http://universities.hipolabs.com/search?country=United+States
Returns JSON data containing all US universities
Transform
Converts JSON data to a pandas DataFrame
Filters for universities with "California" in the name
Converts list columns (domains, web_pages) to comma-separated strings
Resets the DataFrame index for clean output
Load
Creates/connects to a SQLite database (my_lite_store.db)
Writes the transformed data to the cal_uni table
Uses if_exists='replace' to overwrite existing data on re-runs
📝 Example Query

To view the data after running the pipeline:

python
import pandas as pd
from sqlalchemy import create_engine

engine = create_engine('sqlite:///my_lite_store.db')
df = pd.read_sql('SELECT * FROM cal_uni', engine)
print(df)
🛠️ Troubleshooting

Issue: API connection error

Solution: Check your internet connection and verify the API URL is accessible

Issue: SQLite database locked

Solution: Close any other connections to the database and try again

Issue: ModuleNotFoundError

Solution: Ensure all dependencies are installed: pip install -r requirements.txt
📚 Learning Resources
Requests Documentation
Pandas Documentation
SQLAlchemy Documentation
HipoLabs Universities API
🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
    run_etl()
    
