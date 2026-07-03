![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Lab | Simple Linear Regression

## Goal

Use scikit-learn to build a simple linear regression model end-to-end: create it, train it, test it, and evaluate it, using a real-world dataset.

## Dataset

`FuelConsumptionCo2.csv` contains fuel consumption ratings and estimated CO2 emissions for new light-duty vehicles sold in Canada (model year 2014, 1,067 records), including engine size, cylinders, fuel consumption (city/highway/combined) and CO2 emissions.

## What Was Done

1. **Explored the data** — loaded the CSV with pandas, summarized it with `.describe()`, and selected the relevant features (`ENGINESIZE`, `CYLINDERS`, `FUELCONSUMPTION_COMB`, `CO2EMISSIONS`).
2. **Visualized relationships** — plotted histograms of the selected features and scatter plots of each feature against `CO2EMISSIONS` to judge how linear each relationship looked.
3. **Split the data** — created an 80/20 train/test split using a random mask (`np.random.rand`), keeping the sets mutually exclusive for an honest out-of-sample evaluation.
4. **Trained a first model** — fit a `LinearRegression` model on `ENGINESIZE` vs. `CO2EMISSIONS`, plotted the resulting fit line over the training data, and inspected the coefficient and intercept.
5. **Evaluated the model** — used the test set to compute Mean Absolute Error (MAE), Mean Squared Error (MSE), and R² score.
6. **Exercise: repeated the process with a different feature** — retrained using `FUELCONSUMPTION_COMB` instead of `ENGINESIZE` and compared the resulting error metrics.

## Results

| Feature used         | MAE   | MSE    | R²   |
|-----------------------|-------|--------|------|
| `ENGINESIZE`           | 23.48 | 972.25 | 0.75 |
| `FUELCONSUMPTION_COMB` | 20.79 | 775.80 | —    |

## Key Learnings

- A simple linear regression model needs only two learned parameters (slope/coefficient and intercept), and scikit-learn estimates them directly from the full training set.
- Splitting data into train/test sets before fitting is essential: it lets you measure how well the model generalizes to data it has never seen, rather than just how well it memorized the training data.
- Not all features are equally good predictors: even though both `ENGINESIZE` and `FUELCONSUMPTION_COMB` correlate with `CO2EMISSIONS`, using `FUELCONSUMPTION_COMB` produced a lower MAE and MSE, meaning it is the stronger single predictor of emissions for this dataset.
- Visualizing a feature against the target before modeling is a useful sanity check to confirm the relationship looks roughly linear before committing to a linear model.
- Different metrics highlight different things: MAE gives an intuitive average error, MSE penalizes large errors more heavily, and R² summarizes how much of the variance in the target the model explains.

## Deliverables

- Completed `main.ipynb` notebook with all exercise cells filled in and executed.

## Submission

- Upon completion, add your deliverables to git.
- Then commit git and push your branch to the remote.
- Make a pull request and paste the PR link in the submission field in the Student Portal.

<br>

**Good luck!**
