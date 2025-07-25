🏥 Healthcare Appointment No-Show Prediction 

📌 Objective

- Predict if a patient will *not show up* to their appointment.
- Identify key factors influencing no-shows (e.g., SMS reminders, age, gender, etc.).
- Visualize actionable insights using *Power BI*.
- Recommend improvements to reduce no-show rates.

 🧰 Tools & Technologies

- Python: Data cleaning, preprocessing, model training
- Scikit-learn: Decision tree model
- Pandas & Matplotlib: Data manipulation and visualization
- Power BI: Dashboards and insights
- Google Colab: Development environment

 📁 Dataset

Source: [Kaggle – Medical Appointment No Shows](https://www.kaggle.com/datasets/joniarroba/noshowappointments)

- Records: 110,000+
- Features:
  - PatientID, AppointmentID, Gender, Age
  - Scheduled Day, Appointment Day
  - SMS_received, Scholarship, Alcoholism, Hypertension
  - No-show (target variable)

 🧼 Data Cleaning Steps

1. Removed irrelevant columns: `PatientId`, `AppointmentID`
2. Converted date columns (`ScheduledDay`, `AppointmentDay`) to datetime
3. Created `WaitingDays` = AppointmentDay - ScheduledDay
4. Converted `No-show` to binary (0 = Showed, 1 = No-show)
5. Created dummy variables (e.g., `Gender_F`)
6. Handled invalid ages (removed `Age < 0`)
7. Final dataset saved as `appointments_final.csv`



 🤖Machine Learning Model

 🔍 Model Used:
- DecisionTreeClassifier (Scikit-learn)

 🧪 Steps:
1. Split data into training and test sets
2. Trained model on features (excluding datetime fields)
3. Evaluated using accuracy and classification report
4. Extracted feature importances


 📊 Power BI Dashboard

Key visuals included:
- Total No-Shows (KPI Card)
- No-Shows by Age Group (Bar chart)
- SMS vs No-Show Analysis (Stacked column)
- Gender-wise No-Show Pie Chart
- No-Show by Neighbourhood (Bar/Map)
- Filter Panel: Gender, Scholarship, Hypertension, Waiting Days

 🔍 Custom Measures (DAX):
```dax
Total No-Shows = CALCULATE(COUNTROWS(appointments_final), appointments_final[No_show] = 1)

No-Show % = DIVIDE([Total No-Shows], COUNTROWS(appointments_final), 0)

Male No-Shows = CALCULATE(COUNTROWS(appointments_final), appointments_final[Gender_F] = 0, appointments_final[No_show] = 1)

Female No-Shows = CALCULATE(COUNTROWS(appointments_final), appointments_final[Gender_F] = 1, appointments_final[No_show] = 1)
