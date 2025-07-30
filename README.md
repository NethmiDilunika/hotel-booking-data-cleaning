# 🏨 Hotel Booking Data Cleaning

This project focuses on cleaning and preparing the [Hotel Booking Demand Dataset](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand) for analysis. The dataset contains booking records from two types of hotels (resort and city) between July 2015 and August 2017. The goal is to identify and fix data quality issues such as missing values, duplicates, outliers, and inconsistencies, resulting in a robust, analysis-ready dataset.

---

## 📌 Objectives

- Handle missing values appropriately
- Remove duplicate and inconsistent records
- Detect and treat outliers in numerical columns
- Validate data integrity and fix logical errors
- Generate a clean, analysis-ready dataset
- Document the data cleaning process

---

## 📂 Folder Structure

```
hotel-booking-data-cleaning/
├── data/
│   ├── hotel_bookings.csv              # Raw dataset
│   └── hotel_bookings_cleaned.csv      # Final cleaned dataset
├── notebooks/
│   └── data_cleaning_process.ipynb     # Jupyter Notebook with all cleaning steps
├── reports/
│   └── data_cleaning_report.md         # Markdown report documenting the cleaning process
└── scripts/
    └── cleaning_functions.py           # Optional: Python functions for reusability
```

---

## 🧪 Cleaning Process Overview

| Step                   | Description                                                        |
|------------------------|--------------------------------------------------------------------|
| **Initial Inspection** | Reviewed data types, structure, and summary statistics             |
| **Missing Values**     | Filled `children`, `agent`, `company` with 0; `country` with mode  |
| **Duplicates**         | Removed ~30–50 exact duplicate rows                                |
| **Outliers**           | Used IQR method to remove outliers from `adr`, `lead_time`, etc.   |
| **Inconsistencies**    | Removed rows with zero total guests; fixed date formatting         |
| **Feature Engineering**| Added `arrival_date`, `total_guests`, `arrival_day_of_week`        |
| **Validation**         | Confirmed no missing or illogical values remained                  |

---

## ✨ Feature Engineering

- **total_guests**: Sum of adults, children, and babies
- **arrival_date**: Combined date from year, month, and day columns
- **arrival_day_of_week**: Weekday name for arrival
- **is_high_season**: Flag for July or August arrivals

---

## 🗃️ Dataset Source

- [Hotel Booking Demand Dataset (Kaggle)](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand)

---

## 💡 Recommendations

- Enforce validation rules during data collection (e.g., guest count > 0)
- Avoid missing or float-type categorical fields (e.g., agent/company IDs)
- Implement automated cleaning scripts for future datasets
- Flag extreme values (e.g., ADR > 1000) during entry

---

## ⚙️ Requirements

- Python 3.7+
- pandas, numpy, seaborn, matplotlib
- Jupyter Notebook or Google Colab

Install requirements using:

```bash
pip install pandas numpy matplotlib seaborn
```

---

## 🚀 Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/hotel-booking-data-cleaning.git
   cd hotel-booking-data-cleaning
   ```

2. **Download the dataset:**  
   Place `hotel_bookings.csv` in the `data/` directory.

3. **Run the cleaning notebook:**  
   Open `notebooks/data_cleaning_process.ipynb` in Jupyter or Colab and follow the steps.

---

## 📊 Outputs

- **Cleaned Dataset:** `data/hotel_bookings_cleaned.csv`
- **Cleaning Report:** `reports/data_cleaning_report.md`

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!  
Feel free to open an issue or submit a pull request.

---

## 📄 License

This project is licensed under the MIT License.
