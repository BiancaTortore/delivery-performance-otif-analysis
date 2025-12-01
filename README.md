# Delivery Performance & OTIF Analysis

This project analyzes delivery performance using a simulated logistics dataset.
The objective is to evaluate key Supply Chain KPIs such as Lead Time, Delay Rate, and OTIF (On Time In Full) using Google Sheets pivot tables.
The analysis aims to demonstrate core skills relevant to Logistics Analyst, Supply Chain Analyst, and Operations Analyst roles.

---

## 📁 Repository Structure
```
delivery-performance-otif-analysis/
│
├── data/
│   └── deliveries_dataset.xlsx
│
├── analysis/
│   └── Screenshot_OTIF_total
│   └── Screenshot_OTIF_by_carrier
│   └── Screenshot_average_lead_time
│   └── Screenshot_lead_time_distribution
│   └── Screenshot_leadtime_by_warehouse
│   └── Screenshot_on_time_rate
│
└── README.md
```

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
- **lead_time_bucket** (categorized)

The dataset simulates real delivery operations across multiple warehouses and carriers.

---
## 📈 KPI Definitions

### **Lead Time**
Number of days between shipment and delivery:
```lead_time = delivery_date – ship_date```
### **Delay Flag**
A delivery is considered **delayed** if:
```lead_time > 3 days```

Values:
- `on_time`
- `delayed`

### **OTIF (On Time In Full)**
A delivery is OTIF when:
- The order was delivered (`status = 1`)
- The delivery occurred within 3 days or less

```otif_flag = "OTIF" if (status = 1 AND lead_time ≤ 3)```
```else "NO_OTIF"```

### **Lead Time Buckets**
Custom buckets added for distribution analysis:
- **0–2 days**
- **3–4 days**
- **5+ days**

---

## 📸 Visualizations

### **1. OTIF Performance (Total)**
![OTIF Total](analysis/Screenshot_OTIF_total)

### **2. OTIF by Carrier**
![OTIF by Carrier](analysis/Screenshot_OTIF_by_carrier)

### **3. Average Lead Time**
![Average Lead Time](analysis/Screenshot_average_lead_time)

### **4. Lead Time Distribution**
![Lead Time Distribution](analysis/Screenshot_lead_time_distribution)

### **5. Lead Time by Warehouse**
![Lead Time by Warehouse](analysis/Screenshot_leadtime_by_warehouse)

### **6. On-time Rate**
![On-time Rate](analysis/Screenshot_on_time_rate)

---

## 📌 Insights & Conclusions

### **1. Carrier Performance (Reliability)**

The OTIF analysis reveals significant differences between carriers:

- **DHL:** 30% OTIF, 7.5% NO_OTIF  
- **GLS:** 22.5% OTIF, 10% NO_OTIF  
- **Hermes:** 2.5% OTIF, 27.5% NO_OTIF  

**Interpretation:**

- **DHL is the most reliable carrier** in the dataset.  
- **GLS shows moderate performance** with room for improvement.  
- **Hermes performs poorly**, responsible for most delays and almost no OTIF deliveries.  
- In a real operation, **Hermes would require urgent reevaluation or reduced assigned volume**.

---

### **2. Warehouse Performance (Lead Time Efficiency)**

Average lead time by warehouse:

- **WH2 → 3.54 days**  
- **WH1 → 3.79 days**  
- **WH3 → 4.31 days**

**Interpretation:**

- **WH2 is the most efficient warehouse**, with the shortest operational cycle.  
- **WH3 shows operational inefficiencies**, with significantly longer lead times.  
- Warehouse variability directly impacts the OTIF score.

---

### **3. OTIF Performance (Service Level)**

- **OTIF Rate:** 55.01%  
- **NO_OTIF:** 44.99%

**Interpretation:**  
A global OTIF of **55%** indicates the operation is not meeting typical logistics service-level standards.  
This is largely influenced by carrier and warehouse performance issues.

---

### **4. Delay Rate & Root Cause Analysis**

- **On-time deliveries:** 55%  
- **Delayed deliveries:** 45%

Lead time bucket distribution:

- **0–2 days:** 40%  
- **3–4 days:** 20%  
- **5+ days:** 40%

**Root cause:**

- The **5+ days bucket** is the main driver of low OTIF.  
- Delays are strongly linked to:
  - **Warehouse WH3**  
  - **Carrier Hermes**

**Conclusion:**  
The combination **WH3 + Hermes** represents the main operational bottleneck.

---

### **5. Recommended Actions (Operational Improvements)**

- **Reduce reliance on Hermes**, due to extremely low OTIF compliance.  
- **Review and optimize WH3 processes**, focusing on dispatch speed and workflow efficiency.  
- **Shift WH3’s workload to WH2**, the most efficient warehouse.  
- **Renegotiate SLAs** with underperforming carriers.  
- **Assign urgent shipments to high-performing combinations** such as DHL + WH2.

---

## 🛠️ How to Reproduce This Analysis

1. Download `deliveries_dataset.xlsx` from `/data`.  
2. Upload it to Google Sheets.  
3. Create pivot tables for:
   - OTIF distribution  
   - OTIF by carrier  
   - Average lead time  
   - Lead time buckets  
   - Lead time per warehouse  
   - Delay distribution  
4. Verify formulas for:
   - `lead_time`  
   - `delay_flag`  
   - `otif_flag`  
   - `lead_time_bucket`  
5. Export visualizations into `/analysis`.

---

## 🚀 Next Steps

- Build a Power BI dashboard with slicers and KPI cards.  
- Add cost-of-delay metrics for deeper operational insights.  
- Expand dataset with SKU, region, and delivery distance.  
- Perform regression analysis to predict delays.
