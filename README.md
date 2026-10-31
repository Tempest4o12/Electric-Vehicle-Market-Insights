# Electric Vehicle Market Performance & Insights

A student data-analytics project combining **Flask**, **pandas**, **Plotly**, and a **Tableau Desktop/Public dashboard and story workflow**.

## Features
- Interactive web dashboard with manufacturer, region, category, and model-year filters.
- KPI cards for distinct vehicle records, annual sales units, average range, average listed price, average customer rating, and average battery capacity.
- Charts for model-year sales trend, category performance, top manufacturers, market regions, battery/range distribution, and price versus rating.
- Tableau implementation guide based on the Skill Wallet video transcripts.
- Kaggle data collection script and basic automated tests.
- Bundled 500-row sample dataset so the application can run immediately.

## Important data note
The repository contains a **500-row sample**, not the complete dataset. The full dataset is excluded from Git because it is large. For final analysis, use the provided ZIP's `ev_market_train.csv` or download the source dataset. The test file is not merged into the training data.

## Quick start

### 1. Create a virtual environment
Windows PowerShell:
```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

macOS/Linux:
```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

### 2. Run with the bundled sample
```bash
python app.py
```
Open http://127.0.0.1:5000

### 3. Use the full training dataset
Extract `ev_market_train.csv` from the supplied `archive.zip` and copy it into `data/ev_market_train.csv`. The app automatically prefers that file over the sample.

Alternatively, set a path explicitly:
Windows PowerShell:
```powershell
$env:EV_DATA_PATH="C:\path\to\ev_market_train.csv"
python app.py
```
macOS/Linux:
```bash
export EV_DATA_PATH="/path/to/ev_market_train.csv"
python app.py
```

### 4. Download from Kaggle (optional)
```bash
python scripts/download_data.py
```
The script uses KaggleHub and may require internet access and Kaggle authentication. It downloads available CSV files into `data/`. Review filenames and schema before using them.

## Tableau workflow
Follow [`docs/tableau_guide.md`](docs/tableau_guide.md) to connect the CSV, prepare fields, create KPI worksheets and charts, assemble the dashboard, build a multi-point Story, publish both to Tableau Public, and publish the Story and update the iframe `src` in the Tableau section of `templates/index.html` if the public view URL changes.

**Publishing limitation:** This repository does not include a pre-published Tableau Public workbook because publishing requires your Tableau account and the workbook created in Tableau Desktop/Public. The Flask page now embeds the published Tableau Public Story in the Tableau section. The Story remains hosted by Tableau Public, so an internet connection is required to view it.

## Tests
```bash
pytest -q
```

## Repository layout
```text
app.py
src/
  data_loader.py
  analytics.py
scripts/
  download_data.py
data/
  ev_market_sample.csv
templates/
  index.html
static/css/styles.css
tests/test_analytics.py
docs/
  project_report.md
  tableau_guide.md
requirements.txt
```

## Data source
Kaggle dataset identifier supplied in the project starter code:
`tharishreddy22/electric-vehicle-market-classification-dataset`

The provided local ZIP contains `ev_market_train.csv` and `ev_market_test.csv`. Verify the source dataset's license and exact schema before redistributing full data.

## License
The code is provided for educational use. Dataset licensing remains subject to the dataset publisher's terms.
