# A/B Test Significance Toolkit

#### The project calculates the statistical significance of key funnel metrics for multiple A/B tests using a two-proportional z-test in a generalized manner (for any number of metrics and dimensions) and visualizes the results in Tableau.

---

## About the Project

Calculating significance using online calculators isn't always convenient, and it's also difficult to scale. That's why the project is based on my replacement of this method with a Python script that:
- calculates the significance for 4 funnel metrics (add_payment_info, add_shipping_info, begin_checkout, new_accounts - all relative to the session);
- it works with arrays and loops, without statically defining the number of metrics, so you can easily add other metrics if necessary;
- counts both the total for the test and the breakdowns (devices, continents, countries);
- outputs a ready-to-use CSV file for visualization.

#### Statistical significance without taking sample size into account can be misleading when certain segments show extreme percentage changes with a p-value < 0.05 but do not hold up to scrutiny based on the volume of data. Therefore, the result should always be considered in conjunction with the sample size.

---

##  Data

The data is retrieved from BigQuery using an SQL query and exported to CSV:
| Column | Description |
|---|---|
| `test`, `test_group` | A/B test number and group (1 = control, 2 = test) |
| `event_name`, `value` | event name and quantity |
| `date`, `country`, `device`, `continent`, `channel` | dimensions for cross-sections |

---

## Stack

| Step | Tools |
|---|---|
| Data Collection | BigQuery (SQL, multi-CTE + `UNION ALL`) |
| Calculation | Python - `pandas`, `numpy`, `statsmodels` (`proportions_ztest`) |
| Environment | Google Colab |
| Visualization | Tableau Public |

---

## Dashboard

#### The interactive Tableau dashboard displays four metrics, indicating which ones are significant and which are not (color-coded), with a filter by test number:
#### [Link to Dasboard](https://public.tableau.com/views/ABtestdashboard_17889006779050/ABtest?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

---

## Get in touch

Feel free to connect on [LinkedIn](https://www.linkedin.com/in/yuliia-mushynska-a31141346), or check out more dashboards on [Tableau Public](https://public.tableau.com/app/profile/yuliia.mushynska).
