# 📊 HR Analytics Dashboard | Tableau · Python

An end-to-end HR analytics dashboard that simulates a real-world workforce reporting solution. Built using **Tableau** for visualization and **Python (Faker)** for synthetic dataset generation — covering everything from hiring trends and demographic breakdowns to salary analysis and performance correlations.

---

## 🎯 Project Objective

The goal of this project was to replicate a real-world HR analytics workflow — starting from stakeholder requirement gathering, through data modelling, all the way to delivering an interactive Tableau dashboard that HR managers can actually use to make decisions.

---

## 📌 Dashboard Overview

The dashboard is split into two main views:

### 1. Summary View
A high-level snapshot broken into three sections:

**Overview**
- Total Hired, Active, and Terminated employee counts (BANs)
- Hiring and termination trends over time (Line Chart)
- Employee breakdown by Department and Job Title (Bar Charts)
- HQ vs. Branch comparison — New York as HQ (Map Visualization)
- Employee distribution by City and State (Enhanced Map)

**Demographics**
- Gender ratio across the company (Pie Chart)
- Age group and education level distribution (Bar Charts)
- Age vs. Education level correlation (Heatmap)
- Education vs. Performance rating correlation (Heatmap)

**Income Analysis**
- Salary comparison by education level and gender (Barbell Chart)
- Age vs. Salary correlation across departments (Scatter Plot)

### 2. Employee Records View
A filterable, drill-down table with full employee details — personal info, job data, salary, and performance — allowing customised exploration at the individual level.

---

## 🗂️ Dataset

The dataset was synthetically generated using the **Python Faker library**, simulating realistic HR records with the following key fields:

| Field | Description |
|---|---|
| Employee ID | Unique identifier |
| Name | Randomly generated |
| Gender | 46% Female / 54% Male |
| State & City | Predefined location list |
| Hire Date | 2015–2024 distribution |
| Department & Job Title | Probability-weighted assignment |
| Education Level | Mapped to job title |
| Performance Rating | Probability-weighted |
| Overtime | 30% probability |
| Salary | Range based on dept & title |
| Termination Date | 11.2% of employees, min 6-month gap from hire |

---

## 🧮 Key Calculated Fields (Tableau)

```tableau
// Total Hired
COUNT([Employee ID])

// Total Terminated
COUNT(IF NOT ISNULL([Termination Date]) THEN [Employee ID] END)

// Total Active
COUNT(IF ISNULL([Termination Date]) THEN [Employee ID] END)

// HQ vs Branch
CASE [State]
    WHEN 'New York' THEN 'HQ'
    ELSE 'Branch'
END

// Age
DATEDIFF('year', [Birth Date], TODAY())

// Age Group
IF [Age] < 25 THEN '<25'
ELSEIF [Age] >= 25 AND [Age] < 35 THEN '25-34'
ELSEIF [Age] >= 35 AND [Age] < 45 THEN '35-44'
ELSEIF [Age] >= 45 AND [Age] < 55 THEN '45-54'
ELSEIF [Age] >= 55 THEN '55+'
END
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Tableau | Dashboard design & visualization |
| Python (Faker) | Synthetic dataset generation |
| Excel / CSV | Data staging |

---

## 📁 Repository Structure

```
hr-analytics-dashboard/
│
├── data/
│   └── hr_dataset.csv          # Generated dataset
│
├── scripts/
│   └── generate_data.py        # Python Faker data generation script
│
├── dashboard/
│   └── HR_Dashboard.twbx       # Packaged Tableau workbook
│
├── screenshots/
│   ├── hr_summary.png          # Summary view screenshot
│   └── hr_detail.png           # Employee records view screenshot
│
└── README.md
```

---

## 🚀 How to Run

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/hr-analytics-dashboard.git
```

2. **Generate the dataset** (optional — pre-generated CSV included)
```bash
pip install faker pandas
python scripts/generate_data.py
```

3. **Open the Tableau workbook**
   - Open `dashboard/HR_Dashboard.twbx` in Tableau Desktop or Tableau Public
   - The dataset is embedded — no additional connection needed

---

## 📷 Screenshots

### Summary View
<img width="1009" height="578" alt="image" src="https://github.com/user-attachments/assets/b304c304-8151-4108-a79d-3b169f21b3c1" />


### Employee Records View
<img width="1000" height="570" alt="image" src="https://github.com/user-attachments/assets/dae24534-cc2f-478a-b0dc-ed47e9549d4a" />


---

## 🔗 Live Dashboard

👉 [View on Tableau Public](#) ← *(replace with your link)*

---

## 👤 Author

**Vignesh Derangula**
[LinkedIn](#) · [GitHub](#) · vigneshderangula@gmail.com
