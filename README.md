# E-commerce Marketing Analytics Toolkit

A comprehensive toolkit for analysing marketing performance and optimising budget allocation across channels. Built with Python, it helps marketers make data-driven decisions by analysing historical performance, measuring channel effectiveness, and providing budget optimisation recommendations.

The model optimises marketing spend to maximise GMV by training an XGBoost model to predict GMV based on marketing spends and external factors (e.g., holidays, sales events, pay days, rolling GMV/units).
Baseline GMV is estimated by setting marketing spends to zero. Saturation levels are calculated using ROI and modelled with the Hill function. Budget constraints (min/max spends per channel and total budget) are set, and Gurobi optimisation is applied to maximise GMV within these limits. The output includes the optimised budget allocation and expected GMV.

Limitations:
The baseline revenue estimation shows the sensitivity of data availability, as even small changes in data can lead to significant changes in revenue dynamics.

Results:
13.60% increase in total revenue and an 11.68% decrease in total investment.
