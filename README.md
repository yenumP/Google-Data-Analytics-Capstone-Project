# Cyclistic Bike Case Study

## Table of Contents

- [Project Overview](#project-overview)
- [About The Company](#about-the-company)
- [Stakeholders Objective](#stakeholders-objective)
- [Data Description](#data-description)
- [Data Preparation](#data-preparation)
- [Analysis](#analysis)
- [Results](#results)
- [Summary](#summary)
- [Recommendation](#recommendation)




### Project Overview
This capstone project serves as the completion of the Google Data Analytics Professional Certificate, utilizing publicly available data in accordance with the specified license agreement.


### About The Company
Cyclistic, a fictional bike-share company based in Chicago, Illinois, was established in 2016 and has expanded its fleet to 5,824 geotracked bicycles that can be docked at 692 Cyclistic stations throughout the city. Users have the convenience of picking up bikes from one station and returning them to any other dock within the Cyclistic network at their convenience.

In the past, Cyclistic's marketing approach focused on attracting a wide range of consumers through general awareness and flexible pricing plans. Presently, customers have the option to purchase single-ride passes, full-day passes, or annual memberships. For the purpose of this analysis, individuals who opt for single-ride or full-day passes will be categorized as casual riders, while those who choose annual memberships are considered Cyclistic members.


### Stakeholder's Objective
The marketing team at Cyclistic aims to increase the number of annual memberships by converting casual riders into annual members, as they have determined that annual members are more profitable. To achieve this goal, they seek to understand the current usage patterns of both customer types and have outlined the following questions to guide their future marketing strategies;

1.How do annual members and casual riders use Cyclistic bikes differently?
2. Why would casual riders buy Cyclistic annual memberships?
3. How can Cyclistic use digital media to influence casual riders to become members?


### Data Description
The cyclistic historic trip dataset is collected and stored on the Amazon Web Server by Cyclistic. The 2023 dataset was downloaded from the Amazon Web Server where it is stored. The data is a csv file containing 12 months usage for riders. All files had 13 variables including rider ID, ride type, start and end station name and IDs, user type and latitude and longitude coordinates. The data is credible and with no bias.



### Data Preparation
installed and loaded packages  needed for the analysis library(tidyverse), library(dplyr), library(skimr),library(readr) in R Studio
After installation, each .csv file was loaded into RStudio, aggregated, and examined with the tidyverse package. Since locational data for individual users is unavailable for analysis, geographic data (latitude and longitude) is unnecessary; this was dropped from the dataset. Created new column for ride length, day  of week, day, month, year using the R function.
Data was subsequently cleaned for nulls and duplicates, which were dropped from the dataset to avoid calculation errors during analysis. This dataset was reduced from 5,719,877  observations to 4,331,823 observations 


### Analysis
preformed data aggregation using R studio
```
divvy_tripdata23 %>%
group_by(member_casual) %>%
  count(rideable_type)

rider_typeday_peruser<- divvy_tripdata23 %>%
  select(rideable_type, day_of_week, member_casual) %>%
  count(rideable_type, day_of_week, member_casual)
head(rider_typeday_peruser)
```
```
#Bike type most used
bike_used<-divvy_tripdata23%>%
  select(rideable_type) %>%
  count(rideable_type)
head(bike_used)
```
```
 #Total and average ride length for both casual and member user
memcas<-divvy_tripdata23 %>%
  group_by(member_casual) %>%
  summarise(total_ride_length=sum(ride_length),
            avg_ride_length=mean(ride_length),
            max_ride_length=max(ride_length),
            min_ride_length=min(ride_length))
head(memcas)
            
```


### Results
- Member users makeup 64.6% of the cyclistic bike share company.
- Casual users makeup 35.4% of the cyclistic bike share company .
- Cyclistic Member users rode an average of 727 secs in a year.
- Casual users rode an average of 1376 secs in a year.
- Member users ride considerably the same all through the week.
- casual riders tend to ride longer on weekends(Sat and Sun)(Figure 6).
- The analysis revealed that both member and casual users showed a preference for the classic bike type, with the electric bike being the second most popular choice (Figure 3). The docked bike was the least favored option and was used  by casual riders only.


#### Five most visited stations by member users are;
- Clinton St & Washington Blvd 
-  Kingsbury St & Kinzie St     
-  Clark St & Elm St            
-  Wells St & Concord Ln
-  Clinton St & Madison St       


#### Five most visited stations by casual users are;
- Streeter Dr.Grand ave
- Millennium park
- Michigan Ave & Oak st
- shedd aquizuim
- Theater on the lake.

### Summary
In conclusion, while casual members make up a smaller proportion of the bike share company's user base, they accounted for the highest number of borrows in 2023 and also tended to have longer rides compared to members. Therefore, a crucial strategy for the company's future growth would be to focus on converting casual riders into annual members to maximize the number of annual memberships.


### Recommendation
- A campaign should be exclusively organized for casual users via advert, mailing, messages etc.
- A considerable amount of discount should be given to casuals who are willing to convert to member users.
-Promo plans should be marked out for weekend rides which will only apply to users who are members. (e.g getting a free 10 mins off any ride).
-There should be other benefit offers for members. Like preference given to members in terms of rideable type since both like to use classic bike types.
 












