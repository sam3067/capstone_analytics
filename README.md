# capstone_analytics
Dynamic Pricing for Urban Parking Lots
Summer Analytics 2025 – Capstone Project
Overview:

This project implements a dynamic pricing system for 14 urban parking lots based on real-time data.
Three models were developed to simulate pricing behavior across time using only Python, Pandas, Numpy,
and Bokeh. Final outputs are visualized to show how each pricing strategy responds to varying demand.

Models Implemented:

1. Model 1: Baseline Linear Pricing
   - Price increases linearly with occupancy rate.

2. Model 2: Demand-Based Pricing
   - Considers occupancy, queue length, traffic, special day indicator, and vehicle type.

3. Model 3: Competitive Pricing
   - Incorporates competitor pricing using location proximity (within 1 km).
   - Suggests price reduction or hike based on surrounding lot prices.

Technologies Used:

- Python
- Pandas, NumPy
- Bokeh (for plotting)
- (Simulated streaming using Python loops instead of Pathway due to OS restrictions)

Instructions to Run:

1. Open `cap.ipynb` in Jupyter.
2. Run all cells in order.
3. Plot results will appear at the end for selected parking lots.
4. Dataset file `dataset.csv` should be in the same folder.

5. Models Description:



Model 1 – Linear Pricing:

Formula: Price = Base + α × (Occupancy / Capacity)
- Starts with a base price of $10.
- Price increases smoothly with occupancy.

Model 2 – Demand-Based Pricing:

Demand Function:
D = α * (Occupancy / Capacity) + β * QueueLength - γ * Traffic + δ * IsSpecialDay + ε * VehicleWeight

Price = BasePrice × (1 + λ × NormalizedDemand)

Feature Weights:
- α = 1.0 (occupancy rate)
- β = 0.5 (queue length)
- γ = 0.7 (traffic level)
- δ = 1.0 (special day)
- ε = 0.3 (vehicle type)

Normalization is applied to keep demand in [0, 1].
Final prices are clipped between $5 and $20.

Model 3 – Competitive Pricing:

- Checks for nearby parking lots (within 1 km).
- If current lot is full and others are cheaper → reduce price.
- If others are more expensive → increase price.
- Uses haversine distance calculation.

Real-Time Simulation:

Due to system limitations (Windows + Python 3.12), Pathway could not be used.
Instead, real-time behavior was simulated by processing records in time order.

Visualizations:

- Bokeh line plots compare Model 1, Model 2, and Model 3 pricing over time.
- Each plot shows how pricing changes with live data.

Assumptions:

- Traffic level mapped as: low=1, medium=2, high=3.
- Vehicle type mapped as: car=1.0, bike=0.5, truck=1.5.
- Pricing bounds: $5 (min) and $20 (max).
- Nearby lots defined as within 1 km.

