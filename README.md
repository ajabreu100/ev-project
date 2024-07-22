# Washington DOL Electric Vehicle Registration Analysis

### Project Overview
---

This data analysis project aimed to identify the Washington State County with the highest count of electric vehicle registrations. After cleaning the data provided by the Washington Department of Licensing, running SQL queries, and creating visualizations, I have gained a deeper understanding of the EV registration activity in Washington state. 

![Dashboard 1](https://github.com/user-attachments/assets/9eec26f6-281b-4545-844a-9cacc90a1b60)


### Data Sources

EV Data: The primary dataset used for the analysis is the "Cleaned Data" file, which represents the refined dataset. The "Raw data" link provides access to the untouched imported dataset.

### Tools

- Excel - Data Cleaning ([Cleaned Data](cleaned_ev_data.csv), [Raw data](https://catalog.data.gov/dataset/electric-vehicle-population-data/resource/fa51be35-691f-45d2-9f3e-535877965e69))

- SQLite Studio - Data Analysis

- Tableau - Creating Visualizations


### Data Cleaning/ Preparation

In the data cleaning process phase, I performed tasks such as:
1. Loading CSV file into Excel, along with an initial inspection
2. Filling any missing values that may not have been entered
3. Examining data for any duplicate values
4. Transforming all text casing to proper cased
5. Trimming unnecessary data or spaces
6. Formating column titles

### Exploratory Data Analysis

##### Main Question
- Which County in Washington State has the highest number of electric vehicle (EV) registrations?
##### Bonus Questions
- Which electric vehicles have the longest driving range?

- Which other states are recognized by the Washington Department of Licensing?

### Data Analysis

```sql
--Viewing first 10 rows for import confirmation
SELECT * 
FROM ev_data
LIMIT 10;
--How many vehicles from each state are registered through Washington DOL
SELECT state, COUNT(*) AS number_registered
FROM ev_data
GROUP BY 1
ORDER BY 2 DESC;
--Top 5 EV vehicle models that perform with the most mileage
SELECT make, model, electric_range
FROM ev_data
GROUP BY 2
ORDER BY 3 DESC
LIMIT 5;
--What was the most common zip code 
SELECT postal_code, COUNT(*) AS occurrences
FROM ev_data
GROUP BY 1
ORDER BY 2 DESC
LIMIT 10;
--What was the most common county
SELECT county, COUNT(*) AS occurrences
FROM ev_data
GROUP BY 1
ORDER BY 2 DESC
LIMIT 10;
```

### Results

My findings are summarized as follows:

1. According to the Washington Department of Licensing, King County had the highest number of electric vehicle registrations in the state.
2. In terms of performance range, the top-performing electric vehicles are the Chevy Bolt, Hyundai Kona, and Tesla Model S.
3. California, Virginia, and Maryland are other states with high electric vehicle registration numbers under the Washington Department of Licensing.

### Recommendations

Based on the results formulated from the analysis:

The counties of King, Snohomish, and Pierce have the highest likelihood of electric vehicle-related engagement. Focusing on these areas will increase the likelihood of engagement for EV-focused endeavors, as EVs are significantly more prevalent in these regions.

### Limitations

Unfortunately, a few rows contain missing values that couldn't be included in certain calculations. Although the number of NULL values was small, it still had minimal effects on our overall findings. 

### References

My raw data source: [Click here](https://catalog.data.gov/dataset/electric-vehicle-population-data/resource/fa51be35-691f-45d2-9f3e-535877965e69)

