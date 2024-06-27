# Mass Shootings Analysis
Project on Mass Shootings

By Ken Ogihara

## Introduction
There has been over 400 mass shootings in the last 50 years that resulted in over 2000 deaths in the United States. On average, the number of mass shootings per year is 8 for the last 50 years. This dataset is taken from Kaggle and contains information on mass shootings in the United States of America. My main research question I will be answering is, "What characteristics should the U.S government look into when predicting the next mass shooting? The following columns are useful in our analysis:

### Columns and Descriptions

| Column                 | Description                                                |
|------------------------|------------------------------------------------------------|
| `S#`                   | Serial number of the incident.                             |
| `Title`                | Title of the incident.                                     |
| `Location`             | Location where the incident occurred.                      |
| `Date`                 | Date of the incident.                                      |
| `Incident Area`        | The specific area where the incident took place.           |
| `Open/Close Location`  | Indicates whether the incident happened inside an enclosed or open space. |
| `Target`               | The possible target audience or company.                   |
| `Cause`                | The cause of the incident (e.g., Terrorism, Hate Crime, Fun, etc.). |
| `Summary`              | A brief summary of the incident.                           |
| `Fatalities`           | Number of fatalities in the incident.                      |
| `Injured`              | Number of people injured in the incident.                  |
| `Total victims`        | Total number of victims (fatalities + injured).            |
| `Policeman Killed`     | Number of on-duty officers killed.                         |
| `Age`                  | Age of the shooter.                                        |
| `Mental Health Issues` | Whether the shooter had known mental health issues.        |
| `Race`                 | Race of the shooter.                                       |
| `Gender`               | Gender of the shooter.                                     |
| `Latitude`             | Latitude of the incident location.                         |
| `Longitude`            | Longitude of the incident location.                        |


Here's the first five rows with a few columns of the uncleaned dataset I worked with:

```py
print(shootings.head()[["Title", "Age", "Location", "Incident Area", "Latitude", "Fatalities"]].to_markdown(index = False))
```


| Title                               | Age | Location               | Incident Area                               | Latitude | Fatalities |
|:------------------------------------|----:|:-----------------------|:--------------------------------------------|---------:|-----------:|
| Texas church mass shooting          |  26 | Sutherland Springs, TX | Church                                      | nan      |         26 |
| Walmart shooting in suburban Denver |  47 | Thornton, CO           | Wal-Mart                                    | nan      |          3 |
| Edgewood business park shooting     |  37 | Edgewood, MD           | Remodeling Store                            | nan      |          3 |
| Las Vegas Strip mass shooting       |  64 | Las Vegas, NV          | Las Vegas Strip Concert outside Mandalay Bay |  36.1813 |         59 |
| San Francisco UPS shooting          |  38 | San Francisco, CA      | UPS facility                                | nan      |          3 |



## Data Cleaning and Exploratory Data Analysis

### Data Import and Cleaning

1. **Importing a New Dataset**
   - I loaded an additional dataset containing more mass shooting incidents.
   - File Path: `/Users/kenogihara/Desktop/ALL_PROJECTS/mass_shooting_project/US Mass Shootings May 24 2022.csv`

2. **Cleaning Columns of the New Dataset**
   - I standardized all column names in the new dataset.
   - I removed any unnecessary columns not present in the existing dataset.

3. **Concatenating Datasets**
   - I combined the cleaned new dataset with the existing dataset.

### Data Transformation

4. **Date Conversion**
   - I converted string dates to timestamp format for easier manipulation and analysis.

5. **Mental Health Issues Column**
   - I standardized the values in the `Mental Health Issues` column to ensure consistency.

6. **Gender Column**
   - I cleaned and standardized gender entries for consistency.

7. **Race Column**
   - I mapped various race descriptions to standard categories for consistency.

8. **Creating New Columns**
   - I extracted the year, month, and state in which a mass shooting occurred from `Date` and `Location` and created the following columns: `Year`, `Month`, and `State`.

9. **State Column Cleaning**
   - I converted state abbreviations to full state names for clarity.

### Handling Missing Data

10. **Geolocation Coordinates**
    - I manually provided coordinates for specific locations with missing values due to the lack of a valid API key.

### Integrating Presidential Data

11. **Cleaning Presidential Data**
    - I loaded and cleaned a dataset containing information about US presidents.
    - I adjusted the range of years for each president's term.

12. **Merging Datasets**
    - I merged the mass shootings dataset with the presidential data to analyze incidents in relation to the sitting president.

### Final Adjustments

13. **Dropping Unnecessary Columns**
    - I removed columns that were not useful for the analysis.

### Summary
This step involved extensive data cleaning and preparation to ensure the datasets are consistent, comprehensive, and ready for further analysis. Key tasks included standardizing column names and values, handling missing data, extracting useful features, and merging relevant datasets. The updated dataset contains 451 rows and 25 columns as opposed to our first uncleaned data that contained 323 rows and 19 columns. 

Here's the first 5 rows of the updated dataset:

| Title                               | Cause   | Fatalities | Latitude | Longitude | Race  | President Name |
|:------------------------------------|:--------|-----------:|---------:|----------:|:------|:---------------|
| Texas church mass shooting          | unknown |         26 |   29.2737 |  -98.0553 | White | Donald Trump   |
| Walmart shooting in suburban Denver | unknown |          3 |   39.8680 | -104.9720 | White | Donald Trump   |
| Edgewood business park shooting     | unknown |          3 |   39.4182 |  -76.2941 | Black | Donald Trump   |
| Las Vegas Strip mass shooting       | unknown |         59 |   36.1813 | -115.1340 | White | Donald Trump   |
| San Francisco UPS shooting          | revenge |          3 |   37.7749 | -122.4190 | Asian | Donald Trump   |


### EDA

Here is a map of all documented mass shootings that occurred in the United States from 1966-2022:

<iframe
  src="assets/mass_shootings_map.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>


Univariate plot that shows the top 10 states with the most mass shootings:

<iframe
  src="assets/plot1.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>


Univariate plot that shows the number of mass shootings over time:

<iframe
  src="assets/plot2.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>


Univariate plot that shows the number of fatalities per year:

<iframe
  src="assets/plot3.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

Univariate plot that shows the severity of mass shootings according to race:

<iframe
  src="assets/plot4.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

Univariate plot that shows the number of mass shootings according to race:

<iframe
  src="assets/plot5.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

Univariate plot that shows the distribution of average fatalities per party:

<iframe
  src="assets/plot6.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

## Assessment of Missingness

I noticed there were many missing values in the Employeed, Incident Area, and Cause column. I performed a hypothesis test to see if the misingness in the Cause column is dependent on the Mental Health Issues column.

Here are the steps I took to guide you through my analysis:

**1. Compute the Test Statistic:** I created an appropriate test statistic derived from the sample that quantifies the strength of association between the `Mental Health Issues` column and `Cause` column by calculating the distribution of `Mental Health Issues` when `Cause` is missing and when it is not missing. I used total variation distance as my test statistic since I am computing a difference in distributions for categorical variables.

**2. Create Shuffled Data:** I shuffled `Mental Health Issues` randomly and recomputed the test statistic for each shuffled dataset 1000x.

**3. Compute the p-value:** This determined the probability of observing a test statistic as extreme as the one computed from the actual data, assuming the null hypothesis is true.

```py
print(f"p_value : {p_value}")
```

p_value: 0.012

<iframe
  src="assets/plot7.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

I rejected the null hypothesis at the 5% level but failed to reject at the 1% level. For the sake of this project, I chose a significance level of 0.05. Therefore, I concluded that the differences are not due to random chance and that the `Cause` column is indeed **dependent** on the `Mental Health Issues` column.

Knowing this, I performed probabilistic imputation by sampling from the present values of `Cause` column separately
for each category in `Mental Health Issues` column.

### Probabilistic Imputation Code


```py
def prob_impute(series):
    series = series.copy()

    # Step 1: Find the number of missing values for that specific category
    num_null = series.isna().sum()
    
    # Step 2: Sample num_null observed values for that category
    fill_values = np.random.choice(series.dropna(), num_null)
    
    # Step 3: Fill in missing values and return series
    series[series.isna()] = fill_values
    return series

# Apply the probabilistic imputation
shootings["Cause"] = (
    shootings
    .groupby("Mental Health Issues")["Cause"]
    .transform(prob_impute)
)
```

## Hypothesis Testing

Let's recall the main research question:

**What characteristics should the U.S government look into when predicting the next mass shooting?**

Previously, we saw that mass shootings caused by Asian perpetrators result in the highest average fatalities. 
We will test if this is true with permutation testing.

**Null hypothesis:** Mass shootings caused by Asian perpetrators do not result in higher fatalites on average than 
shootings caused by any other ethnicity. The differences are simply due to random chance.

**Alternative hypothesis:** The differences are not due to random chance, and the distributions come from different
data generating processes.

The steps I took for this hypothesis test is the same as the steps I took for my assessment of missingness, with the exception of the test statistic being the difference in the proportion of fatalities between shootings caused by Asian perpetrators and other races. 


<iframe
  src="assets/Asian_Whiteplot.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

<iframe
  src="assets/Asian_Blackplot.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

<iframe
  src="assets/Asian_Unknownplot.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

<iframe
  src="assets/Asian_Otherplot.html"
  width="700"
  height="500"
  frameborder="0"
></iframe>

<iframe
  src="assets/Asian_Latinoplot.html"
  width="900"
  height="500"
  frameborder="0"
></iframe>

<iframe
  src="assets/Asian_Native Americanplot.html"
  width="900"
  height="500"
  frameborder="0"
></iframe>

<iframe
  src="assets/Asian_Multiracialplot.html"
  width="900"
  height="500"
  frameborder="0"
></iframe>


### Summary

I failed to reject the null hypothesis at a significance level of 0.05 in the following scenarios:

1. White people
2. Others
3. Native Americans
4. Multiracial

We rejected the null hypothesis for Black, Unknown, and Latinos. In other words, mass shootings caused by Asian
perpetrators indeed result in higher fatalities on average than shootings caused by Black, Unknown and Latinos;
however, there is enough evidence to suggest that mass shootings caused by Asian perpetrators do not result in
higher fatalities on average than shootings caused by White, Others, Native Americans, and multiracial people.

### Second Hypothesis Test:

In our sixth univariate plot, we saw that there were more
fatalities on average during Republican presidency than Democratic presidency. In my second hypothesis test, I will see if this is true.

**Null hypothesis:** There is no relationship between the two parties. The differences are simply due to random chance.

**Alternative hypothesis:** On average, there are more fatalities during Republican presidency than Democratic
presidencies. The differences are not due to random chance.

```py
print(f"p_value: {p_value}")
```

p_value: 0.00

<iframe
  src="assets/plot8.html"
  width="800"
  height="500"
  frameborder="0"
></iframe>

I rejected the null hypothesis at any significance level. This means that there is enough evidence 
to suggest that there are more fatalities on average during Republican presidency than Democratic presidency 
from 1966-2022.

## Final Model

In this section, I used KMeans clustering which is a form of unsupervised learning to group my data into specific categories. I chose this model because 
our dataset does not have an explicit set of labeled data that consists of input-output pairs. Our data consists of
unlabeled data of input features without any corresponding labels; therefore, my goal in this section was to
develop a model that creates clusters of data to find hidden patterns and structures.

### Checking for Missing Values
- I first identified columns that have no missing values
- I addressed a specific row (323) where `Total victims` and `Injured` had missing values, filling them with the number of fatalities

### Feature Selection
I selected the following features to be used in KMeans clustering:

1. `Cause`
2. `Fatalities`
3. `Injured`
4. `Total victims`
5. `Mental Health Issues`
6. `Gender`
7. `Year`
8. `President Name`
9. `Race`

### Preprocessing

I applied transformations to the selected features:
- `OneHotEncoder` for categorical features: `Cause`, `Mental Health Issues`, `Gender`, `President Name`, `Race`.

- `StandardScaler` for numerical features: `Fatalities`, `Injured`, `Total victims`.

### Silhouette Score
I evaluated the performance of K-means clustering for different numbers of clusters (ranging from 2 to 10) using the silhouette score. I determined that 6 clusters had the highest silhouette coefficient after 2. Hence, I created a pipeline integrating the preprocessing steps and the K-means model with 6 clusters.
I then fitted the model to the selected features and generated cluster labels. Finally, I joined the cluster labels to the original dataset for further analysis.


<iframe
  src="assets/ss.html"
  width="800"
  height="500"
  frameborder="0"
></iframe>

### Dimensionality Reduction

I used **TruncatedSVD** to reduce the dimensionality of the dataset to 2 components for visualization. TruncatedSVD was chosen over PCA because it handles sparse matrices (resulting from one-hot encoding) efficiently. Here are the results:


<iframe
  src="assets/clusters.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Final Analysis   

Univariate plot that shows the average number of fatalities per cluster:

<iframe
  src="assets/plot9.html"
  width="900"
  height="700"
  frameborder="0"
></iframe>

Univariate plot that shows the percentage of mass shootings that occurred during Republican presidencies per cluster:

<iframe
  src="assets/plot10.html"
  width="900"
  height="700"
  frameborder="0"
></iframe>

Univariate plot that shows the average year in which mass shootings occurred per cluster:

<iframe
  src="assets/plot11.html"
  width="900"
  height="700"
  frameborder="0"
></iframe>


## Conclusion

Cluster 4 has the highest average fatalities and injuries compared to its 
counterparts. There seems to be a slight correlation in the severity of mass shootings and poltical party.
Finally, there seems to be a slight correlation with the severity of a shooting and the
year in which it occurred. Recent years tend to have more severe shootings than past years with the exception of 
cluster 1.
