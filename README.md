# Washington DOL EV (Electric Vehicle) Registration Analysis

### Project Overview
---

This data analysis project aimed to identify the Washington State County with the highest EV vehicle registration count. By cleaning the data provided by the Washington Department of Licensing, generating SQL queries, and constructing visuals, we have a deeper understanding of Washington state EV registration activity. 

![Dashboard 1](https://github.com/user-attachments/assets/9eec26f6-281b-4545-844a-9cacc90a1b60)


### Data Sources

EV Data: The primary dataset utilized for the analysis is the file "EV_washington_DOL_data." The file contains two sheets: one sheet titled "work_vehicle_data," which represents the cleaned and refined dataset, and one sheet titled "Original_vehicle_data," which represents the raw untouched imported dataset.

### Tools

-Excel - Data Cleaning ([Cleaned Data](cleaned_ev_data.csv), [Raw data](https://catalog.data.gov/dataset/electric-vehicle-population-data/resource/fa51be35-691f-45d2-9f3e-535877965e69))

-SQLite Studio - Data Analysis

-Tableau - Creating Visualizations


### Data Cleaning/ Preparation

In the data cleaning process phase, we performed tasks such as:
1. Loading CSV file into Excel, along with an initial inspection
2. Filling any missing values that may not have been completed
3. Examining data for any duplicate values
4. Transforming all text casing to proper case
5. Trimming unnecessary data or spaces
6. Formating column titles

### Exploratory Data Analysis

##### Main Question
-Which county of Washington state contains the most EV vehicle registrations
##### Bonus Questions
-Which EV vehicles contain the highest driving range

-What other states are registered in the Washington DOL

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
1. King County had the highest registration count under the Washington DOL.
2. The vehicles in the top-performing EV range include the Chevy Bolt, Hyundai Kona, and Tesla Model S.
3. The top states other registered under the Washington DOL include California, Virginia, and Maryland.

### Recommendations

Based on the results formulated from the analysis:

The counties of King, Snohomish, and Pierce have the highest chance of electric vehicle-related engagement.
Focusing on those areas will increase the likelihood of engagement, as EVs are exponentially more prevalent in these regions.

### Limitations
Unfortunately, some rows have missing values that could not be accounted for in certain calculations. Though the number of NULL values wasn't large, there is still data missing from our overall findings. 

### References

My raw data source: [Click here](https://catalog.data.gov/dataset/electric-vehicle-population-data/resource/fa51be35-691f-45d2-9f3e-535877965e69)

