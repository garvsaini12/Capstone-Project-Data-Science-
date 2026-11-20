# Capstone-Project-Data-Science-
# Patient Appointment No-Show Analysis

> A Data Science Capstone Project to analyse why patients miss medical appointments and predict no-shows using Machine Learning.

**Course:** AML002 - Introduction to Data Science  
**Programme:** B.Sc. (Hons.) Data Science, Semester - I  
**University:** K.R. Mangalam University, Gurugram  
**Author:** Garv Saini (2610840012)  
**Language:** Python

---

## 📋 Problem Statement

Hospitals lose valuable appointment capacity when patients fail to attend their scheduled medical appointments.

This project analyses a de-identified medical appointment dataset to:
1. Calculate the overall no-show rate
2. Identify patterns associated with patient non-attendance
3. Build models to predict missed appointments

**Findings are exploratory only.** This is not a clinical decision system.

---

## 📦 Dataset

**Source:** Kaggle - Medical Appointment No Shows (Joni Hoppen)  
**Link:** https://www.kaggle.com/datasets/joniarroba/noshowappointments

| Detail | Value |
| :--- | :--- |
| Total Records | 110,527 |
| Original Columns | 14 |
| Unit of Analysis | 1 Row = 1 Appointment |
| Target Column | `No-show` (Yes = Missed, No = Attended) |

### Columns Used

| Column | Meaning |
| :--- | :--- |
| `Gender` | Recorded gender category |
| `ScheduledDay` | Date/time when appointment was booked |
| `AppointmentDay` | Date of appointment |
| `Age` | Age of patient |
| `Neighbourhood` | Neighbourhood / location category |
| `Scholarship` | Bolsa Familia welfare programme indicator |
| `Hipertension` | Hypertension indicator (source spelling) |
| `Diabetes` | Diabetes indicator |
| `Alcoholism` | Alcoholism indicator |
| `Handcap` | Handicap / disability indicator (source spelling) |
| `SMS_received` | Whether SMS reminder was received |
| `No-show` | Outcome: Yes / No |

> `PatientId` and `AppointmentID` are **NOT** used as predictors. They are identifiers only.

---

## 🛠️ Tools & Libraries

- Python 3
- pandas, NumPy - Data loading, cleaning
- Matplotlib, Seaborn - Visualisation
- scikit-learn - Machine Learning
- Google Colab / Jupyter - Notebook Environment

---

## 🔄 Methodology - 5 Phases

### Phase 1: Problem Definition & Data Understanding
Confirm problem statement, download CSV, inspect shape, dtypes, `head()`, `info()`, `describe()`, missing values.

### Phase 2: Data Cleaning, Wrangling & EDA
- Remove duplicate rows
- Parse `ScheduledDay` and `AppointmentDay` as dates
- Standardise `No-show` labels to Yes / No
- Remove invalid dates, Age < 0
- Create `Waiting_Days = AppointmentDay - ScheduledDay`
- Create `Appointment_Weekday` and `Age_Group` (0-17, 18-30, 31-45, 46-60, Above 60)
- Remove `Waiting_Days < 0` rows and document exclusions

### Phase 3: Visualisation & Insights
1. Attendance Counts
2. No-Show Rate by Age Group
3. No-Show Rate by SMS Status
4. No-Show Rate by Weekday
5. Waiting Days vs No-Show (Boxplot)
6. No-Show Rate by Gender
7. Top 10 Neighbourhoods by No-Show Rate
8. Numeric Correlation Heatmap

### Phase 4: Machine Learning & Evaluation
- **Target:** `No_Show_Target` (No = 0, Yes = 1)
- **Split:** 80% Train, 20% Test, `stratify=y, random_state=42`
- **Preprocessing Pipeline:**
    - Categorical: Most Frequent Imputation + OneHotEncoder
    - Numeric: Median Imputation
- **Models Compared:**
    - Logistic Regression (`max_iter=1000, class_weight="balanced"`)
    - Decision Tree (`max_depth=8, class_weight="balanced"`)

- **Metrics:** Accuracy, Precision, Recall, F1-Score, ROC-AUC, Confusion Matrix

### Phase 5: Report, Conclusion & Demonstration
Final report with charts, actual numerical results, model comparison, limitations and conclusion.

---

## 🚀 How to Run

### Step 1: Download Dataset
Download `KaggleV2-May-2016.csv` from Kaggle link above.

### Step 2: Open Google Colab
Create a new notebook and paste the code from `Patient_Appointment_No_Show_Analysis.ipynb` or `Appendix A` of the report.

### Step 3: Upload CSV
When the upload window appears, select the downloaded CSV file.

### Step 4: Run All Cells
Run from top to bottom. Outputs will be saved in:
