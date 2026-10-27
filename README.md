# Electric Vehicle Market Performance & Insights

An interactive electric-vehicle (EV) market analytics project built with **Python, Flask, pandas, Plotly, and Tableau Public**. The project combines a local web dashboard with a published Tableau Story to explore vehicle categories, manufacturers, sales, ratings, geography, and battery performance.

## Live Tableau Story

**Explore the published Tableau Story:** [Electric Vehicle Market Performance & Insights](https://public.tableau.com/views/ElectricVehicleMarketPerformanceInsights_17930441877120/EVMarketStory?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link)

The Flask website embeds this Story in its Tableau section. An internet connection is required to view the embedded Tableau content.

## Features

- Flask web application with interactive Plotly visualizations.
- Dashboard filters for manufacturer, market region, vehicle category, and model year.
- KPI summaries and charts for vehicle records, sales, range, price, ratings, and battery characteristics, depending on the columns available in the selected data.
- Tableau Story covering EV categories, manufacturers, annual sales, customer ratings, geography, battery performance, and key insights.
- Included 500-row sample CSV so the app can run without downloading the full dataset.
- Script to download the source dataset from Kaggle, plus basic automated tests.

## Data source and download

The full dataset is **not stored in this GitHub repository** because the CSV files are large. The repository includes a small sample for a quick start; use the full dataset to reproduce the analysis on the complete training data.

- **Source:** [Electric Vehicle Market Classification Dataset on Kaggle](https://www.kaggle.com/datasets/tharishreddy22/electric-vehicle-market-classification-dataset)
- **Kaggle dataset ID:** `tharishreddy22/electric-vehicle-market-classification-dataset`
- **Expected training file:** `ev_market_train.csv`
- **Optional test file:** `ev_market_test.csv`

### Option A — Download through Kaggle in your browser

1. Open the Kaggle dataset page linked above and sign in to Kaggle if prompted.
2. Download the dataset archive.
3. Extract the archive on your computer.
4. Copy `ev_market_train.csv` into this project's `data/` folder, so the path is `data/ev_market_train.csv`.
5. Optionally copy `ev_market_test.csv` into `data/` if you need it for your own analysis. The Flask app uses the training CSV; it does not merge the test file into the training data.

### Option B — Download using the included script

After installing the project requirements, run:

```bash
python scripts/download_data.py
```

The script uses KaggleHub to retrieve the dataset and copy CSV files into `data/`. Access requirements may vary by Kaggle account and environment. If the script fails, use Option A above and manually place `ev_market_train.csv` in `data/`.

**Data and licensing note:** The dataset is hosted by its original publisher on Kaggle. Review the dataset page, license, and any applicable terms before redistributing the source CSV or using it outside this educational project. This repository links to the source rather than republishing the full data.

## Run locally

### 1. Clone the repository

```bash
git clone https://github.com/Tempest4o12/Electric-Vehicle-Market-Insights.git
cd Electric-Vehicle-Market-Insights
```

Or download the repository ZIP from GitHub and extract it.

### 2. Create and activate a virtual environment

**Windows PowerShell:**

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```

**macOS/Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Start the application

```bash
python app.py
```

Open [http://127.0.0.1:5000](http://127.0.0.1:5000) in your browser.

By default, the app uses `data/ev_market_train.csv` if it exists; otherwise, it falls back to the bundled sample `data/ev_market_sample.csv`. The app displays which dataset it loaded.

### Use a CSV stored somewhere else (optional)

You can set the `EV_DATA_PATH` environment variable to the full path of a CSV file.

**Windows PowerShell:**

```powershell
$env:EV_DATA_PATH="C:\path\to\ev_market_train.csv"
python app.py
```

**macOS/Linux:**

```bash
export EV_DATA_PATH="/path/to/ev_market_train.csv"
python app.py
```

## Run tests

```bash
pytest -q
```

## Tableau workflow

The Tableau worksheets, dashboard, and Story were created in Tableau Public Desktop and published separately to Tableau Public. See [`docs/tableau_guide.md`](docs/tableau_guide.md) for the workflow. The Flask page embeds the published Story; if its Tableau URL changes, update the embed URL in `templates/index.html`.

## Project structure

```text
Electric-Vehicle-Market-Insights/
├── app.py
├── src/
│   ├── data_loader.py
│   └── analytics.py
├── scripts/
│   └── download_data.py
├── data/
│   ├── ev_market_sample.csv
│   └── README.md
├── templates/
│   └── index.html
├── static/css/styles.css
├── docs/
│   ├── project_report.md
│   └── tableau_guide.md
├── tests/
│   └── test_analytics.py
├── requirements.txt
├── .gitignore
└── README.md
```

## Limitations and interpretation

- The bundled sample is for demonstration and is not a substitute for the full dataset.
- Results depend on the selected dataset and its coverage. Counts of records alone do not prove actual market share.
- Some battery fields may contain missing values; interpret charts with those gaps in mind.
- Tableau visualizations are hosted by Tableau Public and require internet access.

## License

The application code is intended for educational use as described in the repository's `LICENSE` file. The dataset remains subject to the terms stated by its original publisher on Kaggle.
