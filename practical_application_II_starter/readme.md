# Summary of findings

After analyzing the used vehicle dataset and testing several regression models, I found that the Random Forest Regressor provided the most accurate price predictions.
The most influential features for determining used car prices were the age of the car (car_age), the mileage (odometer), and whether the vehicle used diesel fuel.
These factors had the greatest impact on price, with newer, lower-mileage, and diesel vehicles generally commanding higher values. I have provided similar recommendation for the client below. 

**Best model:**  Random Forest Regressor outperformed other models, achieving the lowest MAE and MSE and the highest R² score, indicating strong predictive performance.

**Key metrics for Random Forest:**

- MAE: ~3364.64
- MSE: ~3.93
- R²: ~0.77

Please see the [jupyter notebook](practical_application_II_starter/prompt_II.ipynb) for key metrics for other models.

# Recommendations to the Client

1. **Focus on Diesel Vehicles:** Diesel cars tend to command higher prices. Consider highlighting diesel vehicles in your marketing and pricing strategies.
2. **Prioritize Newer Car Inventory:** Newer vehicles consistently achieve higher sale prices and tend to sell faster. Promoting newer models would help maximize revenue.
3. **Emphasize Low Mileage (Marketing):** Mileage is a critical factor in determining price. Promote vehicles with lower odometer readings, and consider offering incentives for trade-ins with low mileage.
4. **Data-Driven Pricing:** Use the predictive model to support pricing decisions, ensuring that age, mileage, and fuel type are appropriately factored into your pricing strategy for optimal competitiveness and profitability.
5. **Inventory Management**: Regularly review your inventory for older or high-mileage vehicles, and consider targeted promotions or pricing adjustments to move these vehicles more efficiently.
