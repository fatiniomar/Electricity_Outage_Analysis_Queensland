# Electricity_Outage_Analysis_Queensland
# Electricity Network Outage Analysis in Queensland: Patterns and Influencing Factors


## 1. Introduction

This project details an in-depth analysis of historical electricity network outage data from the Australian Energy Market Operator (AEMO) in Queensland. The primary goal is to identify underlying patterns and influencing factors contributing to outage characteristics, with a particular focus on understanding and mitigating **long-duration outages**. Utilizing data mining techniques, this analysis aims to provide actionable insights for network operators to enhance grid reliability and operational efficiency.

## 2. Problem Statement

Prolonged electricity outages pose significant challenges to grid reliability, customer satisfaction, and operational efficiency within complex electricity networks. While general outage trends are monitored, there remains a need to identify the intricate combinations of network characteristics, operational conditions, and external factors that frequently lead to these extended outage events.

## 3. Project Objective

The explicit objective of this study is: "To identify significant associations and patterns between network equipment characteristics, operational conditions (such as equipment age and seasonal factors), and the occurrence of long-duration electricity outages in Queensland, as revealed through the application of Association Rule Mining (FP-Growth)."

## 4. Methodology

The analysis follows a robust data science pipeline:
1.  **Data Collection:** Gathering raw outage and network equipment data from AEMO's public repository.
2.  **Preprocessing & Feature Engineering:** Extensive data cleaning, type conversion, filtering, and creation of new features (e.g., outage duration categories: Short, Medium, Long; equipment age bins; seasonal indicators). This stage also involved careful handling of complex data merging scenarios (e.g., managing `substationID - equipmentID` combinations) to ensure data integrity.
3.  **Data Exploration (EDA):** Initial visual and statistical analysis to understand data distributions and inform feature engineering decisions.
4.  **Association Rule Mining (ARM):** Applying the **FP-Growth algorithm** to uncover hidden "if-then" patterns. FP-Growth was chosen for its **efficiency and scalability** in handling large, dense datasets typical of power system operations, overcoming computational limitations of traditional ARM algorithms like Apriori.
5.  **Results & Insights:** Interpretation of discovered rules (assessed by Support, Confidence, and Lift) to derive actionable intelligence.

## 5. Key Findings (Summary)

The analysis yielded compelling insights into the drivers of long-duration outages:

* **Outage Duration:** Outages were categorized into 'Short' ($\le$ 179 min), 'Medium' (179-661 min), and 'Long' ($>$ 661 min).
* **Equipment Type:** While 'LINE' and 'CB' equipment contribute most to overall outages, 'ISOL' equipment disproportionately leads to Long outages (65.2% of its outages).
* **Equipment Age:** Equipment in **21-25 year and 36-40 year age bins** showed a significantly higher proportion of **Long outages (approx. 40%)** compared to other age groups (approx. 20%), indicating critical wear-out phases.
* **Seasonality:** While overall outage counts varied by season, 'Summer' exhibited a notably lower proportion of **Long outages (approx. 20%)** compared to other seasons (approx. 30%).
* **Association Rules:** `REASON_HV equipt commissioning` was identified as a consistently strong antecedent for Long outages, with top rules achieving **Confidence values up to ~63% and Lift values exceeding 2.5**. This highlights specific scenarios (e.g., `{'REASON_HV equipt commissioning', 'ISSECONDARY_0.0', 'EQUIPMENT_AGE_BIN_6-10', 'EQUIPMENTTYPE_CB'}` $\rightarrow$ `Long Outage`) that are 2.5 times more likely to result in a long outage than by chance.

## 7. Reproducibility

This project's analysis is fully reproducible. The code is written in Python and executed within Jupyter Notebooks.

### Prerequisites

Ensure you have Python 3.8+ installed.

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/fatiniomar/Electricity_Outage_Analysis_Queensland.git]
    cd Electricity_Outage_Analysis_Queensland
    ```

2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

### How to Run

1.  **Place data:** You will need to obtain the relevant historical outage and equipment data from AEMO's NEMWEB portal https://nemweb.com.au/Data_Archive/Wholesale_Electricity/MMSDM/2025/MMSDM_2025_01/MMSDM_Historical_Data_SQLLoader/DATA/.
*(Note: Due to data size and AEMO's distribution policies, raw data is not included in this repository.)*
3.  **Start Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```
4.  **Navigate and Run:** Open the notebook and execute each cell sequentially.

## 8. Contact

For any questions or further discussions regarding this project, please feel free to reach out:
* n11691611@qut.edu.au

