# 🏦 Bank Interest Rates Web Scraping & Yield Analytics Pipeline

An end-to-end data pipeline built in Python to automatedly scrape, parse, normalize, and calculate quarterly compounded annualized yields for Fixed Deposit (FD) and savings interest rates across **50+ Indian commercial and Small Finance Banks (SFBs)**.

---

## 📌 Project Overview

Financial institutions continuously update their Fixed Deposit (FD) and savings interest rates across varying tenure buckets. Manually monitoring these portals is tedious and error-prone. 

This repository provides an automated data extraction and transformation engine that:
1. **Scrapes** raw interest rate tables from 50+ banking websites using `BeautifulSoup`, `Requests`, and `Selenium`.
2. **Normalizes** heterogeneous tenure text (e.g., *"1 yr to < 2 yrs"*, *"22 Months (Green Earth)"*, *"444 days"*) into standardized numeric day counts (`Duration (days)`).
3. **Computes Annualized Effective Yields** using quarterly compounding mathematical models for tenures $\ge 180$ days.
4. **Generates Analytical Datasets** (`Processed_Interest_Table.xlsx`) comparing nominal rates against true annualized yields for both **General** and **Senior Citizen** categories.

---

## ✨ Key Metrics & Technical Features

- **Extensive Coverage (50+ Banks)**: Scrapes rate matrices across Public Sector Banks, Private Banks, and Small Finance Banks for tenures ranging from 7 days to 10 years.
- **95% Process Automation**: Reduced multi-hour manual data collection (~8+ hours across 50 portals) down to an automated execution time of **under 10 minutes**.
- **Dynamic DOM Handling**: Uses `Selenium WebDriver` with `WebDriverWait` for JavaScript-rendered dynamic pages, and lightweight `Requests` + `BeautifulSoup` for static portals.
- **Data Normalization Engine**: Custom Regex parsing pipeline (`parse_duration`) that cleans irregular tenure descriptions and handles edge cases like special green FDs or conditional bounds (*"to less than"*).
- **Quarterly Compounding Math**: Automatically evaluates quarterly compounding to compute effective annualized yield ($Y$) from nominal rate ($r$) and duration ($T$ years):

$$\text{Effective Yield} = \left(1 + \frac{r}{4}\right)^{4 \cdot T} - 1$$

$$\text{Annualized Yield} = \left(1 + \text{Effective Yield}\right)^{\frac{1}{T}} - 1$$

---

## 📂 Repository Structure

```
Web_scraping/
├── Master_scrape_file_v1.ipynb                 # Master execution pipeline
├── Parsing and computing annualised yield.ipynb # Tenure parsing & compounding yield engine
│
├── Public Sector Banks/
│   ├── State_Bank_of_India_v2.ipynb
│   ├── Bank_of_Baroda_v2.ipynb
│   ├── Canara_Bank_v2.ipynb
│   ├── Punjab_National_Bank_v2.ipynb
│   ├── Union Bank of India.ipynb
│   └── ...
│
├── Private Sector Banks/
│   ├── HDFC_Bank_v2.ipynb
│   ├── ICICI_Bank_v2.ipynb
│   ├── Kotak_Mahindra_Bank_v2.ipynb
│   ├── Axis_Bank_v2.ipynb
│   ├── Yes_Bank_v2.ipynb
│   └── ...
│
├── Small Finance Banks (SFBs)/
│   ├── AU_SF_Bank_v2.ipynb
│   ├── Ujjivan_SF_Bank_v2.ipynb
│   ├── Equitas_SF_Bank_v2.ipynb
│   ├── Jana_SF_Bank_v2.ipynb
│   └── ...
│
├── .gitignore                                  # Git ignore configuration
└── README.md                                   # Project documentation
```

---

## 🏦 Covered Banks

| Bank Type | Institutions Covered |
| :--- | :--- |
| **Public Sector Banks** | State Bank of India (SBI), Bank of Baroda, Canara Bank, Punjab National Bank, Union Bank of India, UCO Bank, Central Bank of India, Indian Bank, Bank of India, Bank of Maharashtra, Punjab & Sind Bank, Indian Overseas Bank. |
| **Private Sector Banks** | HDFC Bank, ICICI Bank, Kotak Mahindra Bank, Axis Bank, Federal Bank, IndusInd Bank, Yes Bank, RBL Bank, IDFC First Bank, City Union Bank, DBS Bank, Deutsche Bank, Dhanlaxmi Bank, Jammu & Kashmir Bank, Karnataka Bank, Karur Vysya Bank, Nainital Bank, South Indian Bank, Standard Chartered Bank, Tamilnad Mercantile Bank. |
| **Small Finance Banks** | AU Small Finance Bank, Ujjivan SFB, Equitas SFB, Jana SFB, Capital SFB, ESAF SFB, Northeast SFB, Shivalik SFB, Suryoday SFB. |

---

## 🛠️ Setup & Installation

### 1. Prerequisites
Ensure Python 3.8+ is installed on your system.

### 2. Clone the Repository
```bash
git clone https://github.com/SanjanaThakran/Web_scraping.git
cd Web_scraping
```

### 3. Install Dependencies
```bash
pip install pandas openpyxl requests bs4 selenium notebook
```

*Note: For Selenium notebooks, ensure Chrome or ChromeDriver is installed.*

---

## 🚀 How to Run

1. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
2. Run individual bank scrapers (e.g., `State_Bank_of_India_v2.ipynb`) to extract raw rate tables.
3. Run `Parsing and computing annualised yield.ipynb` to clean tenure descriptions, calculate quarterly compounding, and export `Processed_Interest_Table.xlsx`.

---

## 👤 Author

**Sanjana Thakran**  
GitHub: [@SanjanaThakran](https://github.com/SanjanaThakran)
