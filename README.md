# Logistics Supply Chain Optimization: Reducing Delays & Costs

### Project Overview
This project analyzes a logistics dataset containing shipment records to identify inefficiencies in the supply chain. The goal was to determine the root causes of shipping delays, optimize carrier selection based on Cost Per Mile (CPM), and improve overall customer satisfaction.

**Role:** Data Analyst  
**Tools:** Microsoft Excel (Power Pivot, DAX, Pivot Tables), Data Cleaning, Business Logic Validation.

---

### Key Business Problem
The logistics operations were facing unexplained delays and rising costs. The management needed a data-driven strategy to:
1. Identify which carriers are underperforming.
2. Locate specific "bottleneck" routes.
3. Determine if package weight affects delivery speed.

---

### Methodology & Data Cleaning
Before analysis, the raw dataset required extensive validation to ensure data integrity.

**1. Data Quality & Standardization:**
* **Text Normalization:** Standardized Carrier names (removed duplicates/typos) and verified consistent formatting.
* **Logic Validation:** Created complex nested `IF` flags to identify logical errors (e.g., *Shipment Date > Delivery Date* or *Status "Lost" with a Delivery Date*).
* **Imputation:** Calculated missing Cost values using a weighted average based on `Distance` and `Weight_Class`.

**2. Feature Engineering:**
* **Weight Segmentation:** Created a `Weight_Class` column (Small, Medium, Heavy) to analyze performance across different package types.
* **DAX Measures:** Developed a `Cost Per Mile (CPM)` measure using Power Pivot to accurately compare carrier pricing efficiency.

---

### Key Insights

**1. Efficiency vs. Reliability**
* **FedEx** is the most reliable carrier with a delay rate of only **8.14%**.
* **USPS** offers the best value, combining a fast 4-day average transit with the lowest CPM (**$0.146**).

**2. The "Heavy Package" Failure**
* **Root Cause Analysis** revealed that **LaserShip** has a critical failure rate with "Heavy" items (>30kg).
* **Data Point:** While they only had **1** delay for Small items, they had **11** delays for Heavy items (a 1000% increase in risk).

**3. Route Bottlenecks**
* Identified significant delays on the **Miami (MIA) to Boston (BOS)** route, averaging **6+ days** (2 days slower than the network average).
* The primary contributor to this delay was identified as DHL.

![Insert your Heatmap Screenshot Here]
*(Figure 1: Route Heatmap identifying the Miami-Boston bottleneck)*

---

### Recommendations
Based on the analysis, the following actions were recommended to stakeholders:

1.  **Carrier Re-allocation:** Shift all "Heavy" shipments away from LaserShip to FedEx to reduce damage and delays.
2.  **Route Optimization:** Investigate the DHL performance on the East Coast corridor (MIA-BOS) or switch volume to USPS for these specific lanes.
3.  **Cost Savings:** Utilize USPS for standard priority shipments to capitalize on the $0.146 CPM.

---

### File Structure
* `Logistics_Analysis.xlsx` - The raw data and analysis.
* `Executive_Report.pdf` - Summary of findings for management.
