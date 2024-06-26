# Mass Shootings Analysis
Project on Mass Shootings

By Ken Ogihara

## Introduction
There has been over 400 mass shootings in the last 50 years that resulted in over 2000 deaths in the United States. On average, the number of mass shootings per year is 8 for the last 50 years. This dataset is taken from Kaggle and contains information on mass shootings in the United States of America. My main research question I will be answering is, "What characteristics should the U.S government look into when predicting the next mass shooting? What laws should policymakers implement to prevent future mass shootings?The following columns will be useful in our analysis:

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


Here's the first five rows of the uncleaned data

```py
print(shootings.head()[["Title", "Age", "Location", "Incident Area", "Mental Health Issues", "Fatalities"]].to_markdown(index = False))
```


| Title                               | Age | Location               | Incident Area                               | Mental Health Issues | Fatalities |
|:------------------------------------|----:|:-----------------------|:--------------------------------------------|:---------------------|-----------:|
| Texas church mass shooting          |  26 | Sutherland Springs, TX | Church                                      | No                   |         26 |
| Walmart shooting in suburban Denver |  47 | Thornton, CO           | Wal-Mart                                    | No                   |          3 |
| Edgewood business park shooting     |  37 | Edgewood, MD           | Remodeling Store                            | No                   |          3 |
| Las Vegas Strip mass shooting       |  64 | Las Vegas, NV          | Las Vegas Strip Concert outside Mandalay Bay| Unclear              |         59 |
| San Francisco UPS shooting          |  38 | San Francisco, CA      | UPS facility                                | Yes                  |          3 |


## Data Cleaning and Exploratory Analysis

