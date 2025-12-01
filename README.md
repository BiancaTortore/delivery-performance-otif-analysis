# Delivery Performance & OTIF Analysis

This project analyzes delivery performance using real-world logistics KPIs such as Lead Time, Delay Rate, and OTIF (On Time In Full).  
It was built as part of a Supply Chain & Logistics Analytics portfolio to demonstrate skills in data cleaning, KPI calculation, and operational performance assessment.

---

## 📦 Dataset Overview

The dataset contains **40 delivery records** with the following fields:

- **order_id**
- **customer_city**
- **warehouse**
- **carrier** (DHL, Hermes, GLS)
- **order_date**
- **ship_date**
- **delivery_date**
- **units**
- **status** (delivered / delayed)
- **lead_time** (calculated)
- **delay_flag** (calculated)
- **otif_flag** (calculated)

The dataset simulates real delivery operations across multiple warehouses and carriers.

---

## 📊 KPIs Calculated

### **1. Lead Time**
Number of days between shipping and delivery.
**lead_time = delivery_date - ship_date**

### **2. Delay Flag**
Indicates whether a delivery is considered delayed.  
Industry rule: **lead_time > 3 days = delayed**

### **3. OTIF (On Time In Full)**
A delivery is considered OTIF when:

- The order was **delivered**, and  
- **Lead time ≤ 3 days**

This KPI is widely used in logistics to assess delivery performance and service quality.

---

## 🧮 Key Pivot Analyses

The following analyses were performed (using Google Sheets Pivot Tables):

### **1. OTIF % Total**
Shows the percentage of deliveries meeting OTIF standards.

### **2. OTIF by Carrier**
Compares performance across DHL, Hermes, and GLS.

### **3. Average Lead Time by Warehouse**
Identifies which warehouse operates more efficiently.

---

## 🔍 Insights (Examples)

These are examples of insights derived from the dataset:

- Carriers show significant differences in OTIF performance.
- Some warehouses have consistently higher lead times.
- Delays are often concentrated in specific carrier–warehouse combinations.
- OTIF % provides a clear measure of overall delivery service quality.

(Replace with your actual numbers after analyzing your pivot tables.)

---

## 🛠 Tools Used

- **Google Sheets** (pivot tables and KPI calculations)
- **Excel** (initial data manipulation)
- **CSV/XLSX dataset**
- *(Optional for later)* Power BI or Tableau for visualization

---

## 📁 Repository Structure
```
delivery-performance-otif-analysis/
│
├── data/
│   └── deliveries_dataset.xlsx
│
├── analysis/
│   └── Sreenshot_OTIF_total
│   └── Sreenshot_OTIF_by_carrier
│   └── Sreenshot_leadtime_by_warehouse
│
└── README.md
```

---

## 🎯 Objective

This project demonstrates the ability to:

- Clean and enrich operational datasets  
- Calculate core logistics KPIs  
- Analyze supply chain performance  
- Interpret OTIF metrics for decision-making  
- Build portfolio-ready analytics material  

It is designed to reflect typical responsibilities of a **Logistics Analyst / Supply Chain Analyst**.

---

## 📬 Contact

For collaboration or inquiries related to logistics analytics or data operations, feel free to connect via GitHub or LinkedIn.
