# QA-PAYMENT-FUNNEL

## 📌 Descripción del Proyecto
This repository contains the documentation and QA test scripts for validating the payment flow system. The main objective is to ensure the end-to-end functionality of the payment process through regression and integration testing.

## 📂 Repository Contents
- `/docs`: Detailed documentation (test plan and reports).
- `/src/tests/Postman`: Postman collections and environments.


## ▶️ How to Run
1. **Clone the Repository**
```bash
git clone https://github.com/your-username/qa-pay-funnel.git
```
2. **Install Newman**
```bash
npm install -g newman newman-reporter-htmlextra
```
3. **Run the collection with an HTML report**
```bash
newman run src/tests/Postman/PayFunnel.postman_collection.json -e src/tests/Postman/staging.postman_environment.json \
-r cli,htmlextra --reporter-htmlextra-export newman-report.html
```

![Newman Tests](https://github.com/lonnynarvaezqa/qa-payment-funnel/actions/workflows/newman-tests.yml/badge.svg)

## 📑 Deliverables
- [Test Plan](./docs/TestPlan.md)
- [Test Execution Report](./docs/TestReport.md)

---
### 👤 Contact
[Lonny Narváez]
[https://www.linkedin.com/in/lonnynarvaez/]
```
