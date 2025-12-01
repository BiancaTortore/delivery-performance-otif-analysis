# Delivery Performance & OTIF Analysis

This project analyzes delivery performance using a simulated logistics dataset to evaluate key Supply Chain KPIs such as Lead Time, Delay Rate, and OTIF (On Time In Full).  
The goal is to demonstrate practical analytical skills relevant to Logistics Analyst, Supply Chain Analyst, and Operations Analyst positions.

---

## Table of Contents
1. Project Overview  
2. Dataset  
3. KPIs  
4. Visualizations  
5. Insights & Conclusions  
6. How to Reproduce  
7. Next Steps  
8. Repository Structure  

---

## 1. Project Overview
The dataset simulates last-mile delivery operations involving multiple carriers and warehouses.  
The objective is to measure operational efficiency, identify bottlenecks, and propose actions that improve overall service levels.

Analysis was conducted in Google Sheets using calculated fields and pivot tables.

---

## 2. Dataset
The dataset includes:

- order_id  
- customer_city  
- warehouse  
- carrier  
- order_date  
- ship_date  
- delivery_date  
- units  
- status  
- lead_time (calculated)  
- delay_flag (calculated)  
- otif_flag (calculated)  
- lead_time_bucket (classified into 0–2, 3–4, 5+ days)

Source: `/data/deliveries_dataset.xlsx`

---

## 3. KPIs

### Lead Time  
Days between shipment and delivery:
```lead_time = delivery_date – ship_date```

### Delay Flag  
A delivery is delayed when lead_time > 3 days.

Values:  
- on_time  
- delayed  

### OTIF (On Time In Full)  
A delivery meets OTIF when:
- status = 1  
- lead_time ≤ 3  

Formula:
```otif_flag = "OTIF" if (status = 1 AND lead_time ≤ 3)```
```else "NO_OTIF"```

### Lead Time Buckets  
Used for distribution analysis:
- 0–2 days  
- 3–4 days  
- 5+ days  

---

## 4. Visualizations

### OTIF Performance (Total)
![OTIF Total](delivery-performance-otif-analysis/analysis
/Screenshot_OTIF_by_carrier.png)

### OTIF by Carrier
![OTIF by Carrier](delivery-performance-otif-analysis/analysis/Screenshot_OTIF_by_carrier)

### Average Lead Time
![Average Lead Time](delivery-performance-otif-analysis/analysis/Screenshot_average_lead_time)

### Lead Time Distribution
![Lead Time Distribution](delivery-performance-otif-analysis/analysis/Screenshot_lead_time_distribution)

### Lead Time by Warehouse
![Lead Time by Warehouse](delivery-performance-otif-analysis/analysis/Screenshot_leadtime_by_warehouse)

### On-time Rate
![On-time Rate](delivery-performance-otif-analysis/analysis/Screenshot_on_time_rate)

---

## 5. Insights & Conclusions

### Carrier Performance
- DHL: 30% OTIF, 7.5% NO_OTIF  
- GLS: 22.5% OTIF, 10% NO_OTIF  
- Hermes: 2.5% OTIF, 27.5% NO_OTIF  

Interpretation:  
DHL is clearly the most reliable carrier.  
GLS shows acceptable performance with room for improvement.  
Hermes underperforms significantly and drives a large share of delays.

### Warehouse Performance
Average lead time:  
- WH2: 3.54 days  
- WH1: 3.79 days  
- WH3: 4.31 days  

WH2 is the most efficient warehouse.  
WH3 demonstrates clear operational inefficiencies and contributes heavily to delays.

### OTIF Performance
- OTIF Rate: 55.01%  
- NO_OTIF: 44.99%

A 55% OTIF rate is below typical logistics standards and indicates broad inefficiencies across carriers and warehouses.

### Delay Rate & Root Causes
- On-time: 55%  
- Delayed: 45%  

Lead time buckets:  
- 0–2 days: 40%  
- 3–4 days: 20%  
- 5+ days: 40%

The 5+ days bucket is the main cause of low OTIF.  
Most delays originate from WH3 and Hermes.

### Summary  
The WH3 + Hermes combination represents the main operational bottleneck and should be addressed first.

### Recommended Actions
- Reduce dependence on Hermes  
- Improve operational processes at WH3  
- Shift part of WH3’s volume to WH2  
- Renegotiate SLAs with underperforming carriers  
- Assign urgent shipments to high-performing routes (e.g., DHL + WH2)

---

## 6. How to Reproduce
1. Download `deliveries_dataset.xlsx` from `/data`.  
2. Upload it to Google Sheets.  
3. Create pivot tables for:
   - OTIF distribution  
   - OTIF by carrier  
   - Average lead time  
   - Lead time buckets  
   - Lead time by warehouse  
   - Delay distribution  
4. Validate formulas:
   - lead_time  
   - delay_flag  
   - otif_flag  
   - lead_time_bucket  
5. Export screenshots into `/analysis`.

---

## 7. Next Steps
- Build a Power BI dashboard  
- Add cost-of-delay metrics  
- Expand dataset with SKU, region, distance  
- Apply regression analysis to predict delays  

---

## 8. Repository Structure
```
delivery-performance-otif-analysis/
│
├── data/
│   └── deliveries_dataset.xlsx
│
├── analysis/
│   ├── Screenshot_OTIF_total
│   ├── Screenshot_OTIF_by_carrier
│   ├── Screenshot_average_lead_time
│   ├── Screenshot_lead_time_distribution
│   ├── Screenshot_leadtime_by_warehouse
│   └── Screenshot_on_time_rate
│
└── README.md
```
