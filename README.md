# Instacart Order Dispatch & Delivery Routing Optimization

### Overview  
Optimized Instacart’s order dispatch and delivery routing in Montréal by formulating an Open Vehicle Routing Problem (OVRP) and solving it with Gurobi. By simulating realistic urban traffic and batching orders, we reduced average delivery times by 20%, increased shopper efficiency, and delivered targeted, data-driven recommendations for peak-hour operations.

### Directory layout  
```bash
.
├── README.md
├── .gitignore
├── data
│   ├── supply&demand_simulation.xlsx    # Simulated demand points & store locations
│   └── result.csv                # Optimized route outputs & timings
├── notebooks
│   └── Instacart_code.ipynb      # Jupyter Notebook with full optimization pipeline
└── reports
    ├── Instacart_report.pdf      # Comprehensive methodology & results
    └── Instachart_Final_presentation.pdf     # Final slide deck summarizing insights
```

---

### Problem Statement

Instacart’s Montréal operations face complex dispatch and routing challenges during peak hours (10 AM–3 PM). Shoppers must be assigned to orders and routed through a city of one‐way streets, construction zones, and variable traffic conditions. Our goal was to minimize per‐order delivery time while maintaining high on‐time performance and balancing operational constraints.

---

### Data Sources

* **Simulated Demand & Store Locations:**
  `supply&demand_simulation.xlsx` is generated with assumptions and Azure Bing Maps API to capture real traffic patterns, construction delays, and one‐way street restrictions.
* **Optimization Results:**
  `result.csv` summarizing batch timestamps, pickup and delivery durations, and shortest‐path sequences.

---

### Methodology

1. **Data Simulation**

   * Used Azure Bing Maps API to generate travel‐time matrices among 26 Dollarama branches and 100 demand points across four land‐use zones (residential, commercial, mixed‐use, suburban).
2. **Problem Formulation**

   * Defined an OVRP with binary variables for shopper–order assignments and routing arcs, including penalties for wait‐time thresholds (>10 min) and urban‐friction factors.
3. **Optimization Modeling**

   * Split into pickup‐stage and delivery‐stage submodels in Python, batching proximate orders and enforcing a two-order limit per trip.
4. **Solver Execution**

   * Tuned Gurobi’s MIPGap and time limits to solve peak-period routing instances, balancing optimality and runtime.
5. **Result Analysis**

   * Evaluated travel‐time savings, on-time delivery rates, and area-specific performance differences.
6. **Business Insight Translation**

   * Distilled technical outputs into four key insights—strategic batching, traffic‐aware penalties, time‐sensitive prioritization, and urban-zoning strategies—and drafted actionable recommendations.
     
---

### Results

* **–20% Average Delivery Time**: Strategic batching cut per-delivery travel by 20%.
* **+15% Shopper Efficiency**: Proximity-based assignments increased orders per route by 15%.
* **+12% On-Time Rate**: Traffic-aware routing improved on-time performance during peak hours.
* **Dynamic Zoning Insights**: Identified high-density urban vs. sparse suburban demand patterns for resource reallocation.

---

### Key Learnings & Challenges

* **Model Fidelity vs. Runtime**: Calibrated Gurobi’s MIPGap and time limits to handle large instances within operational deadlines.
* **Penalty Calibration**: Tuned construction and one-way street penalties to reflect real-world delays without over-restricting routes.
* **API Integration**: Managed Azure Bing Maps rate limits and data consistency to ensure reliable travel‐time estimates.

---

### Future Enhancements

1. **Real-Time Re-Optimization**: Incorporate live traffic and order feeds for dynamic route updates.
2. **Time-Window Constraints**: Add customer‐specified delivery intervals to balance efficiency and satisfaction.
3. **Multi-Supplier Routing**: Extend the model to batch orders across multiple retailers in a single trip.

