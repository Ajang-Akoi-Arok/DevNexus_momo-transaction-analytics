# DevNexus_momo-transaction-analytics

**Team:** DevNexus

**Members:**
- Ajang Biar
- Chidiebele Anigbogu
- Sochukwuma Chukwu

## Project Description

This project processes MoMo (Mobile Money) SMS data provided in XML format. The data is cleaned, categorized, and stored in a relational database, then presented through a frontend dashboard for analysis and visualization. The project demonstrates backend data processing, database management, and frontend development as part of an enterprise-level fullstack application.

## System Architecture

_Link to architecture diagram: _

## Scrum Board

_Link to Scrum board: _

## Project Structure

```
DevNexus_momo-transaction-analytics/
├── README.md                  # Setup, run, overview, team info
├── requirements.txt           # xml parsing, dateutil, etc

├── web/                        # Frontend dashboard
│   ├── index.html
│   ├── styles.css
│   └── chart_handler.js        # Fetch + render charts/tables

├── data/
│   ├── raw/
│   │   └── momo.xml            # Provided XML input (git-ignored)
│   ├── processed/
│   │   └── dashboard.json      # Cleaned data for the frontend
│   └── db.sqlite3              # SQLite database file

├── etl/
│   ├── parse_xml.py            # Read and parse the XML
│   ├── clean_normalize.py      # Fix amounts, dates, phone numbers
│   ├── categorize.py           # Tag transaction types
│   ├── load_db.py              # Save to SQLite
│   └── run.py                  # Runs the whole pipeline in order

└── scripts/
    └── run_etl.sh               # One command to run everything
```

## Setup & Run

1. Clone the repository:
   ```
   git clone https://github.com/Ajang-Akoi-Arok/DevNexus_momo-transaction-analytics.git
   cd DevNexus_momo-transaction-analytics
   ```

2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Place the provided `momo.xml` file in `data/raw/`.

4. Run the ETL pipeline:
   ```
   bash scripts/run_etl.sh
   ```
   This parses, cleans, categorizes, and loads the data into `data/db.sqlite3`, and produces `data/processed/dashboard.json`.

5. Serve the frontend dashboard:
   ```
   python -m http.server 8000 --directory web
   ```
   Then open `http://localhost:8000` in your browser.

## Tech Stack

- **Backend / ETL:** Python (ElementTree/lxml for XML parsing, dateutil for date handling)
- **Database:** SQLite
- **Frontend:** HTML, CSS, JavaScript (chart rendering)
