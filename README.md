## FinCred: Line of Credit(LOC) Auto-Approval Application

📌 Project Overview<br>
The FinCred project is a tool that helps banks automatically decide if someone should get a line of credit, how much they can borrow, and at what interest rate. It uses machine learning to make these decisions faster and more accurately.

This project is for banks and financial institutions to speed up their credit approval process. Instead of manually reviewing every application, the system scores it in real time.

For people working in banks, it saves time, reduces paperwork, and lowers human error. For customers, it means faster approvals, more fair decisions, and a smoother experience when applying for credit.

---

## ⚙️ Technologies Used

| Component             | Technology                                |
|-----------------------|--------------------------------------------|
| Backend Framework     | Flask (Python)                             |
| Machine Learning      | Random Forest, XGBoost                     |
| Data Processing       | Pandas, NumPy                              |
| Data Validation       | Custom Python logic                        |
| Model Evaluation      | Scikit-learn                               |
| API Development       | Flask REST API with async support          |
| Data Simulation       | Synthetic data generation (Python)         |
| Authentication        | Token-based authentication (Flask)         |

---

## 🏦 Who Is It For?

- **Banks and financial institutions**: To automate and speed up credit approval.
- **Loan officers**: To reduce manual reviews and improve consistency.
- **Customers**: To receive faster, fairer, and more transparent LOC decisions.

---

## 🌟 Key Features
Instant LOC eligibility assessment.

Synthetic data generation for model training (5,000 rows).

Credit score calculation based on FICO-like model.

Real-time approval status, limit, and interest rate predictions.

---

## 🔄 Project Workflow

1. **Data Source**: The project started with real data point examples from Canadian banks.
2. **Data Gap**: After searching for relevant public datasets, no complete datasets were found.
3. **Synthetic Data Generation**: To ensure the model has realistic and diverse input, high-quality synthetic applicant data was generated—covering credit scores, income, utilization rates, and more.
4. **Model Training & Testing**: Machine learning models were trained using this data to predict:
   - Credit score validation
   - Approval decision
   - Loan amount limit
   - Interest rate
5. **API Development**: A Flask API was built to serve real-time predictions with authentication.
6. **Scoring Logic**: Business logic (like DTI, utilization, caps) was baked into the decision system to mimic real bank evaluation flows.

---
## 🧮 Example Calculation

**Input:**
- Income: $80,000  
- Debt: $2,100 (rent) + estimated $300 (based on credit utilization)  
- Expenses: $2,000 (excluded from DTI)  
- Credit Score: 700  
- Credit Limit: $25,000  
- Utilization: 40%  
- Open Accounts: 3  
- History: "On-time"  
- Requested Loan: $15,000  

**Calculation:**
- Estimated Debt: `25,000 * 0.4 * 0.03 = $300`
- Total Debt: `2,100 + 300 = $2,400`
- DTI (Debt-to-Income Ratio):  
  `(2,400 + 15,000 * 0.03) / (80,000 / 12)`  
  `= (2,400 + 450) / 6,666.67 ≈ 42.75%`
- Approval Logic:  
  - Base limit: $40,000  
  - DTI > 40% → reduced to $20,000  
  - Cap at request amount $15,000 → final approved = $15,000  
  - Rate: 6.75% + 1% (due to high DTI) → **7.75%**

**Output:**
> ✅ Approved for **$15,000** at **7.75%** interest (DTI slightly high but acceptable)
