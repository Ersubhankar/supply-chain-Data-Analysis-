A data processing, cleaning, exploratory data analysis (EDA), and machine learning/statistical modeling pipeline for analyzing supply chain metrics, production performance, defects, and logistics efficiency.

## 📋 Table of Contents
- [Project Overview](#-project-overview)
- [Key Features](#-key-features)
- [Dataset Overview](#-dataset-overview)
- [Project Architecture & Workflow](#-project-architecture--workflow)
- [Technologies & Libraries Used](#-technologies--libraries-used)
- [Installation & Setup](#-installation--setup)
- [Data Cleaning & Preprocessing Pipeline](#-data-cleaning--preprocessing-pipeline)
- [Exploratory Data Analysis (EDA) & Insights](#-exploratory-data-analysis-eda--insights)
- [Repository Structure](#-repository-structure)
- [Future Enhancements](#-future-enhancements)
- [License](#-license)

## 📌 Project Overview
Efficient supply chain management is crucial for minimizing operational overhead, ensuring quality assurance, optimizing inventory levels, and maximizing revenue. This project provides a step-by-step analytical framework to clean, inspect, analyze, and visualize supply chain performance across various dimensions including product categories, transportation routes, supplier lead times, defect rates, and generated revenue.

The core objective is to transform raw, noisy operational dataset into a clean, structured asset and extract actionable insights to streamline logistics and manufacturing processes.

## ✨ Key Features
* **Data Ingestion & Quality Audit**: Checks for missing values, structural anomalies, improper formatting, and invalid data inputs.
* **Automated Data Cleaning**:
  * Strips whitespace and standardizes text casing across categorical features.
  * Replaces dirty/missing flags (`N/A`, `NULL`, blank strings) with standardized `NaN`.
  * Filters out logically invalid data (e.g., negative/zero prices, stock levels, lead times, or costs).
  * Standardizes numeric fields to two decimal places for financial and metric consistency.
* **Exploratory Data Analysis (EDA)**:
  * Statistical profiling (`describe()`, correlation matrices, distribution summaries).
  * Category-level breakdown of revenue, production volume, and defect rates.
  * Correlation heatmap generation to identify key operational dependencies.

## 📊 Dataset Overview
The dataset contains **100 records and 24 features** capturing end-to-end supply chain operations across cosmetics, haircare, and skincare product lines.

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Product type` | `str` | Category of the product (haircare, skincare, cosmetics). |
| `SKU` | `str` | Stock Keeping Unit identifier. |
| `Price` | `float64` | Selling price per unit. |
| `Availability` | `int64` | Stock availability score/count. |
| `Number of products sold` | `float64` | Units sold per product. |
| `Revenue generated` | `float64` | Total revenue produced. |
| `Customer demographics` | `str` | Primary consumer demographic (Female, Male, Non-Binary, Unknown). |
| `Stock levels` | `int64` | Current quantity in warehouse inventory. |
| `Lead times` | `int64` | Supplier order processing time (days). |
| `Order quantities` | `int64` | Average or minimum order quantity per batch. |
| `Shipping times` | `int64` | Time required to ship products to destination. |
| `Shipping carriers` | `str` | Logistics provider handling the shipment. |
| `Shipping costs` | `float64` | Cost incurred per shipment. |
| `Supplier name` | `str` | Identifier/Name of the product supplier. |
| `Location` | `str` | Manufacturing/warehouse city (Mumbai, Delhi, Kolkata, Chennai, Bangalore). |
| `Lead time` | `float64` | Overall fulfillment lead time. |
| `Production volumes` | `float64` | Total units produced during manufacturing. |
| `Manufacturing lead time` | `float64` | Days required to manufacture a batch. |
| `Manufacturing costs` | `float64` | Direct cost of production per batch/unit. |
| `Inspection results` | `str` | Quality control result (`Pass`, `Fail`, `Pending`). |
| `Defect rates` | `float64` | Percentage/rate of defective items found. |
| `Transportation modes` | `str` | Mode of delivery (`Road`, `Air`, `Rail`, `Sea`). |
| `Routes` | `str` | Specific logistics route code (`Route A`, `Route B`, `Route C`). |
| `Costs` | `float64` | Total combined transportation and handling costs. |

## 🛠 Project Architecture & Workflow


Raw Supply Chain Data 

        │
        ▼
Data Quality Auditing --> Inspect Missing Values & Types

        │
        ▼

Cleaning & Preprocessing --> Case Uniformity, Filtering Non-Positive Values, Rounding

        │
        ▼

Statistical Analysis & EDA --> Metrics Summaries, Revenue Analysis

        │
        ▼

Visualizations & Insights --> Correlation Heatmap, Bar Plots, Export Metrics


## 💻 Technologies & Libraries Used
- **Python 3.x**
- **Pandas**: Data manipulation, filtering, and aggregation.
- **NumPy**: Numerical computations and conditional data handling.
- **Matplotlib**: Core plot generation and layout customization.
- **Seaborn**: High-level statistical data visualization.
- **OpenPyXL**: Reading and processing Excel (`.xlsx`) datasets.

## ⚙️ Installation & Setup

1. **Clone the Repository**
   ```bash
   git clone [https://github.com/your-username/supply-chain-analysis.git](https://github.com/your-username/supply-chain-analysis.git)
   cd supply-chain-analysis
Create a Virtual Environment (Optional but Recommended)Bashpython -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
Install DependenciesBashpip install pandas numpy matplotlib seaborn openpyxl
Run the Analysis Notebook / ScriptBashjupyter notebook supply_chain_analysis.ipynb

🧹 Data Cleaning & Preprocessing PipelineThe data cleaning pipeline executes the following steps sequentially to guarantee data integrity:Missing & Dirty Value Normalization:Replaces placeholder strings ('N/A', 'NULL', '', ' ') with np.nan.Text Normalization:Strips leading and trailing spaces from string entries and applies title casing to categories (e.g., converting 'FEMALE' / 'female' → 'Female').Invalid/Outlier Value Filtering:Removes records containing negative or zero values across key operational metrics (Price, Availability, Stock levels, Lead times, Manufacturing costs, Defect rates, Shipping costs, Costs).Precision Formatting:Rounds financial and metric columns (Price, Revenue generated, Shipping costs, Manufacturing costs, Defect rates, Costs) to two decimal places.📈 Exploratory Data Analysis (EDA) & InsightsKey Operational Metrics Summary (Post-Cleaning)Mean Selling Price: ~$49.97Mean Revenue Generated: ~$5,765.83 per product entryAverage Defect Rate: ~2.30%Average Manufacturing Cost: ~$46.26Revenue Breakdown by Product CategoryProduct TypeRevenue Generated ($)Skincare$187,672.40Haircare$161,327.45Cosmetics$154,003.91Skincare generates the highest overall revenue, making it the primary driver of top-line growth.Generated Visualizationscorrelation_matrix.png: Heatmap illustrating relationships between lead times, defect rates, shipping costs, and generated revenue.revenue_by_product_type.png: Bar plot showcasing revenue distribution across product lines.📁 Repository Structure├── data/
│   └── supply_chain_data.xlsx      # Primary input dataset
├── output/
│   ├── correlation_matrix.png       # Generated correlation plot
│   └── revenue_by_product_type.png # Revenue distribution chart
├── supply_chain_analysis.ipynb      # Main Jupyter notebook containing code & analysis
├── README.md                        # Project documentation
└── requirements.txt                 # Dependencies list

🔮 Future Enhancements
[ ] Build a predictive machine learning model to forecast product demand and stockouts.
[ ] Implement supplier scoring based on defect rates and lead time compliance.
[ ] Optimize logistics routing using linear programming to minimize total transportation cost (Costs + Shipping costs).
[ ] Develop an interactive Streamlit or Dash dashboard for real-time operational monitoring.

📜 LicenseThis project is licensed under the MIT License.
