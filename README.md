# Banking Risk & Financial Insights Analysis

## 📌 Project Overview
This project is a comprehensive **Banking Risk Analytics** solution designed to help financial institutions understand customer behavior and minimize lending risks. By analyzing customer profiles, financial holdings, and risk scores, I developed an end-to-end pipeline: from data extraction via SQL to exploratory analysis in Python, and finally, a 3-page interactive **Power BI Dashboard**.

The primary goal is to empower the bank to make data-driven decisions: approving loans for stable applicants and flagging high-risk profiles.

## 🛠️ Tech Stack
* **Database:** MySQL Workbench (Data Storage & Extraction)
* **Language:** Python (Pandas, SQLAlchemy, Matplotlib, Seaborn)
* **Visualization:** Power BI (Interactive Dashboarding)
* **Environment:** Jupyter Notebook / VS Code (using `.env` for secure DB connection)

---

## 🚀 Workflow & Technical Implementation

### 1. Data Extraction (SQL & Python)
Data is managed in a MySQL database. I used `SQLAlchemy` to securely pull the data into a Python environment, ensuring sensitive credentials were kept safe using environment variables.

```python
engine = create_engine(f"mysql+pymysql://{os.getenv('DB_USER')}:{os.getenv('DB_PASSWORD')}"
    f"@{os.getenv('DB_HOST')}:{os.getenv('DB_PORT')}/"
    f"{os.getenv('DB_NAME')}")

df = pd.read_sql('SELECT * FROM banking_analysis.customers', con=engine)
```

## 📊 2. Exploratory Data Analysis (EDA)

### 🔹 Feature Engineering
Estimated Income was categorized into **five income bands** using `pd.cut` to better segment customer financial behavior:

- Very Low  
- Low  
- Medium  
- High  
- Very High  

This allows more meaningful analysis of how financial products are distributed across income levels.

### 🔹 Univariate & Bivariate Analysis
The following customer dimensions were analyzed:

- Nationality  
- Loyalty Classification  
- Gender  
- Occupation  

These were compared against:

- Loan balances  
- Credit card balances  
- Savings  
- Checking accounts  

This revealed how different demographic groups interact with banking products.

### 🔹 Correlation Analysis
A **Seaborn Heatmap** was used to study relationships between:

- **Debt products:** Loans, Credit Cards  
- **Liquidity products:** Savings, Checking  

This helped identify how risk exposure clusters across customers.

---

## 📈 3. Power BI Dashboard Logic

Three dashboards were designed to provide a **360° view of bank health**.

---

### 🔴 A. Loan Analysis — *The Risk View*

Focused on **credit exposure and concentration risk**.

**Key Visuals:**

- **Loans by Occupation & Nationality**  
  Identifies whether the bank is overexposed to a single industry or region.

- **Income Band Distribution (Pie Chart)**  
  Shows how loan volumes are spread across income groups, revealing lending quality.

---

### 🔵 B. Deposit Analysis — *The Liquidity View*

Focused on **funding stability and cost of capital**.

**Key Visuals:**

- **Checking vs Savings vs Foreign Currency Accounts**  
  Determines the bank’s **cost of funds** and liquidity mix.

- **Deposits by Nationality & Branch ID**  
  Identifies which customer segments provide the most stable funding.

---

### 🟢 C. Summary Dashboard — *The Strategic View*

This dashboard shows the **overall health of the bank** using four core KPIs.

| Metric | Value | Interpretation |
|------|------|----------------|
| **Loan to Deposit Ratio** | **116.40%** | The bank lends more than it holds in deposits — an aggressive growth strategy |
| **Net Interest Margin (NIM)** | **7.55%** | Strong profitability after paying interest on deposits |
| **Risk vs Return (Scatter)** | — | Higher-risk loans generate higher margins |
| **Loan Growth Trend** | — | Rapid expansion observed around 2020 |

---

## 🔍 Key Insights & Observations

### 1️⃣ Asset Clustering  
Customers holding **business loans** are also far more likely to have **high credit card balances**, indicating **cross-product borrowing** behavior.

### 2️⃣ Stability Indicators  
High **total bank deposits** strongly correlate with **high savings balances**, representing the **lowest-risk customer segment**.

### 3️⃣ Income Paradox  
Estimated income shows only a **weak relationship** with credit card usage — meaning **spending is driven more by lifestyle and loyalty** than salary alone.

### 4️⃣ Risk Pricing  
Despite a high **Loan-to-Deposit Ratio (116.40%)**, the bank maintains a strong **Net Interest Margin (7.55%)**, indicating it is **correctly pricing risk**.

---


## 📁 Project Structure

├── data/ # Raw Banking.csv data
├── notebook/ # Jupyter Notebook for EDA & processing
├── SQL/ # schema.sql and query.sql
├── PowerBI/ # .pbix file and dashboard screenshots
├── .env.example # Template for DB credentials
└── README.md # Project documentation


---

## ⚙️ Setup & Installation

### 🗄️ Database
Run `schema.sql` in **MySQL Workbench** to create the database:

```sql
banking_analysis
```

## 🔐 Environment Setup

Create a `.env` file in the root directory and add the following:

```env
DB_USER=your_username  
DB_PASSWORD=your_password  
DB_HOST=localhost  
DB_NAME=banking_analysis  
```

## 🐍 Python Dependencies

Install all required Python libraries:

```bash
pip install pandas sqlalchemy pymysql seaborn matplotlib
```

## 📊 Power BI

Open the `.pbix` file in **Power BI Desktop** to interact with the dashboards:

- **Loan Risk View**  
- **Deposit (Liquidity) View**  
- **Strategic Summary Dashboard**

These dashboards allow you to analyze:

- Credit exposure  
- Deposit stability  
- Risk vs return  
- Profitability and growth  

---

## 🚀 Outcome

This project delivers a **bank-grade financial intelligence platform** that enables decision-makers to:

- Monitor liquidity  
- Control credit risk  
- Measure profitability  
- Detect customer concentration  
- Support data-driven lending strategy  

It reflects how modern financial institutions manage large-scale balance sheets using analytics.
