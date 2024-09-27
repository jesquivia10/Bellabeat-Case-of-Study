# Bellabeat Case of Study: How Can a Wellness Technology Company Play It Smart?
Data analysis for Bellabeat, a high-tech company that manufactures health-focused smart products. We will focus on one of Bellabeat’s products and analyze smart device data to gain insight into how consumers are using their smart devices.  

# **Table of Content**

- [1. Introduction](#introduction)
  - [1.1. About the Company](#about_the_company)
- [2. Ask Phase](#ask_phase)
  - [2.1. Business Task](#business_task)
  - [2.2. Key Stakeholders](#key_stakeholders)
- [3. Prepare Phase](#prepare_phase)
  - [3.1. Description of Data Sources](#description_of_data_sources)
- [4. Process Phase](#process_phase)
  - [4.1. Installing Packages](#installing_packages)
  - [4.2. Importing Datasets](#importing_datasets)
  - [4.3. Checking the Datasets](#checking_the_datasets)
  - [4.4. Checking number of participants and number of rows](#checking_number_of_participants_and_number_of_rows)
  - [4.5. Look for Duplicates](#look_for_duplicates)
  - [4.6. Delete Duplicates](#delete_duplicates)
  - [4.7. Formatting Column names](#formatting_column_names)
  - [4.8. Formatting Date Columns](#formatting_date_columns)
  - [4.9. Merging Datasets](#merging_datasets)
- [5. Analyze and Share Phase](#analyze_and_share_phase)
- [6. Conclusion and Recommendations](#conclusion_and_recommendations)
  - [6.1. Summary of Key Findings](#summary_of_key_findings)
  - [6.2. Recommendations for Bellabeat](#recommendations_for_bellabeat)

 ## **1. Introduction** <a class="anchor"  id="introduction"></a>

You are a junior data analyst working on the marketing analyst team at Bellabeat, a high-tech manufacturer of health-focused products for women. Bellabeat is a successful small company, but they have the potential to become a larger player in the global smart device market. Urška Sršen, cofounder and Chief Creative Officer of Bellabeat, believes that analyzing Smart device fitness data could help unlock new growth opportunities for the company. You have been asked to focus on one of Bellabeat’s products and analyze smart device data to gain insight into how consumers are using their smart devices. The insights you discover will then help guide marketing strategy for the company. You will present your analysis to the Bellabeat executive team along with your high-level recommendations for Bellabeat’s marketing strategy.


### **1.1. About the Company** <a class="anchor"  id="about_the_company"></a>

Urška Sršen and Sando Mur founded Bellabeat, a high-tech company that manufactures health-focused smart products. Sršen used her background as an artist to develop beautifully designed technology that informs and inspires women around the world. Collecting data on activity, sleep, stress, and reproductive health has allowed Bellabeat to empower women with knowledge about their own health and habits. Since it was founded in 2013, Bellabeat has grown rapidly and quickly positioned itself as a tech-driven wellness company for women. 

By 2016, Bellabeat had opened offices around the world and launched multiple products. Bellabeat products became available through a growing number of online retailers in addition to their own e-commerce channel on their website. The company has invested in traditional advertising media, such as radio, out-of-home billboards, print, and television, but focuses on digital marketing extensively. Bellabeat invests year-round in Google Search, maintaining active Facebook and Instagram pages, and consistently engages consumers on Twitter. Additionally, Bellabeat runs video ads on Youtube and display ads on the Google Display Network to support campaigns around key marketing dates. 

Sršen knows that an analysis of Bellabeat’s available consumer data would reveal more opportunities for growth. She has asked the marketing analytics team to focus on a Bellabeat product and analyze smart device usage data in order to gain insight into how people are already using their smart devices. Then, using this information, she would like high-level recommendations for how these trends can inform Bellabeat marketing strategy.


## **2. Ask Phase** <a class="anchor"  id="ask_phase"></a>

### **2.1. Business Task** <a class="anchor"  id="business_task"></a>

The business task in this scenario is to analyze smart device data to gain insights into how consumers are using their Bellabeat smart devices and to use those insights to inform marketing strategy and unlock new growth opportunities for the company. This involves:

**Data Analysis:** Collecting and analyzing data from Bellabeat's smart devices to understand user behavior, preferences, and usage patterns.
Insight Generation: Deriving meaningful insights from the analyzed data to identify opportunities for product improvement, marketing targeting, and business growth.

**Marketing Strategy Development:** Using the insights to inform and develop effective marketing strategies that resonate with Bellabeat's target audience and drive sales.

**Business Growth:** Ultimately, the goal is to use the insights to unlock new growth opportunities for Bellabeat and strengthen its position in the global smart device market.

### **2.2. Key Stakeholders** <a class="anchor"  id="key_stakeholders"></a>

**Urška Sršen:** Bellabeat’s cofounder and Chief Creative Officer.

**Sando Mur:** Mathematician and Bellabeat’s cofounder; key member of the Bellabeat executive team.


## **3. Prepare Phase** <a class="anchor"  id="prepare_phase"></a>

### **3.1. Description of Data Sources** <a class="anchor"  id="description_of_data_sources"></a>

Our stakeholders recommended to use FitBit Fitness Tracker Data, which is a dataset from Kaggle.com. All data was downloaded and stored on my personal computer and Google Drive, in a folder dedicated to the project.

Data is organized in a long format; each row is a one-time point per subject. So each subject will have data in multiple rows. Any variables that don’t change across time will have the same value in all the rows.

Because of the number of the sample (30), there might be bias issues with the data pointed out by the stakeholders. 

Regarding licensing, privacy, and security, the data originates from a public domain and was accessed through Mobius. Thirty eligible Fitbit users consented to submit their personal tracker data, which includes minute-level outputs for physical activity, heart rate, and sleep monitoring. This dataset provides detailed information on daily activity, steps, and heart rate, allowing for an in-depth exploration of users’ habits.



Out of the total eighteen datasets, I will be using the following six:

| Dataset                  | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| dailyActivity_merged     | Daily Activity over 31 days of 33 users. Tracking daily: Steps, Distance, Intensities, Calories. |
| sleepDay_merged          | Daily sleep logs, tracked by: Total count of sleeps a day, Total minutes, Total Time in Bed. |
| hourlyCalories_merged    | Hourly Calories burned over 31 days of 33 users.                            |
| hourlySteps_merged       | Hourly Steps over 31 days of 33 users.                                      |
| hourlyIntensities_merged | Hourly total and average intensity over 31 days of 33 users.                |
| minuteStepsNarrow_merged | Steps tracked every minute over 31 days of 33 users (Every minute in single row). |

## **4. Process Phase** <a class="anchor"  id="process_phase"></a>

The datasets selected are relatively small. Therefore, I will primarily use spreadsheets to review the data. Subsequently, I will utilize R for data cleaning, processing and analyse. Additionally, I will employ the R Markdown feature to organize the final document.

I used Excel for Data Validation, Data Quality Checks, Data Consistency, Source Reliability, Data Documentation, Statistical Analysis and Visualization methods in order to ensure Data's integrity. However I will use R to confirm.


### **4.1. Installing Packages** <a class="anchor"  id="installing_packages"></a>

First we start by installing the packages and libraries we need to analyze the data.

```{r message=FALSE, warning=FALSE}
library(tidyverse)
library(lubridate)
library(dplyr)
library(ggplot2)
library(tidyr)
library(ggpubr)
library(here)
library(skimr)
library(janitor)
library(ggrepel)
library(ggthemes)
library(pracma)
library(knitr)
library(kableExtra)
```


### **4.2. Importing Datasets** <a class="anchor"  id="importing_datasets"></a>
​
In order to perform the analysis I will study the datasets as follow:
​
**Activity & Sleep:**
​
Analyze how daily activity levels affect sleep duration or sleep quality using dailyActivity_merged and sleepDay_merged.
​
**Hourly Trends:**
​
Combine hourlyCalories_merged with hourlySteps_merged and hourlyIntensities_merged to understand the relationship between activity intensity, step count, and calorie burning throughout the day.
​
**Detailed Analysis:**
​
Use minuteStepsNarrow_merged to identify peak activity times and analyze user behavior in detail. However, keep in mind the large data volume and processing requirements.
​
Therefore let's import the following six datasets:

```{r message=FALSE, warning=FALSE}
daily_activity <- read_csv(file= "dailyActivity_merged.csv")
daily_sleep <- read_csv(file= "sleepDay_merged.csv")
hourly_calories <- read_csv(file= "hourlyCalories_merged.csv")
hourly_steps <- read_csv("hourlySteps_merged.csv")
hourly_intensities <- read_csv(file= "hourlyIntensities_merged.csv")
minutes_steps_narrow <- read_csv(file= "minuteStepsNarrow_merged.csv")
```

### **4.3. Checking the Datasets** <a class="anchor"  id="checking_the_datasets"></a>

We can use the head(), and colnames() function in order to check everything was imported correctly and get a preview of the data. We use the kable() function to give it table format to the data.

```{r message=FALSE, warning=FALSE}

kable(head(daily_activity), align = "c", caption = "Daily Activity Dataframe")
colnames(daily_activity)

kable(head(daily_sleep), align = "c", caption = "Daily Sleep Dataframe")
colnames(daily_sleep)

kable(head(hourly_calories), align = "c", caption = "Hourly Calories Dataframe")
colnames(hourly_calories)

kable(head(hourly_steps), align = "c", caption = "Hourly Steps Dataframe")
colnames(hourly_steps)

kable(head(hourly_intensities), align = "c", caption = "Hourly Intensities Dataframe")
colnames(hourly_intensities)

kable(head(minutes_steps_narrow), align = "c", caption = "Minutes Steps Dataframe")
colnames(minutes_steps_narrow)
```
![image](https://github.com/user-attachments/assets/60df0789-2e30-4ab0-b15b-79b3aebc4c01)

![image](https://github.com/user-attachments/assets/b4f7609c-9b82-47a3-99a5-2dcc763967a4)

![image](https://github.com/user-attachments/assets/a179a892-7b77-4fe3-878c-9ba5f203d044)

![image](https://github.com/user-attachments/assets/c039121d-c802-4e07-8974-5b9c52f3ba3b)

![image](https://github.com/user-attachments/assets/b2eb7a51-a871-40e1-9a14-3698743364f2)

![image](https://github.com/user-attachments/assets/52b560ba-2765-4ec5-9a51-a1e563f9078b)

### **4.4. Checking number of participants and number of rows** <a class="anchor"  id="checking_number_of_participants_and_number_of_rows"></a>

We would like to now how many individuals participated for each dataframe. And also how many observations are in each table.

```{r}
# How many unique participants are there in each dataframe?

n_distinct(daily_activity$Id)
n_distinct(daily_sleep$Id)
n_distinct(hourly_calories$Id)
n_distinct(hourly_steps$Id)
n_distinct(hourly_intensities$Id)
n_distinct(minutes_steps_narrow$Id)

# How many observations are there in each dataframe?

nrow(daily_activity)
nrow(daily_sleep)
nrow(hourly_calories)
nrow(hourly_steps)
nrow(hourly_intensities)
nrow(minutes_steps_narrow)

```
![image](https://github.com/user-attachments/assets/dbc5b4b8-6af2-41d2-ae48-4014c6393822)
![image](https://github.com/user-attachments/assets/ed8d858c-5b16-4c4b-baa1-8fc0d5257d35)

### **4.5. Look for Duplicates** <a class="anchor"  id="look_for_duplicates"></a>

We will now check for any duplicates in our data.

```{r message=FALSE, warning=FALSE}
sum(duplicated(daily_activity))
sum(duplicated(daily_sleep))
sum(duplicated(hourly_calories))
sum(duplicated(hourly_steps))
sum(duplicated(hourly_intensities))
sum(duplicated(minutes_steps_narrow))
```
![image](https://github.com/user-attachments/assets/96810a7b-f6fd-4e89-b95e-be7429cf89d8)

### **4.6. Delete Duplicates** <a class="anchor"  id="delete_duplicates"></a>
​
As observed, there are three duplicate rows in the 'daily_sleep' dataset. We will now proceed to remove them.
​
```{r message=FALSE, warning=FALSE}
daily_sleep <- daily_sleep %>%
  distinct() %>%
  drop_na()
```
Now, let’s verify that the duplicates have been removed.

```{r message=FALSE, warning=FALSE}
sum(duplicated(daily_sleep))
```
![image](https://github.com/user-attachments/assets/59dd940f-74a2-4b60-a3ce-f22cccee4859)

### **4.7. Formatting Column names** <a class="anchor"  id="formatting_column_names"></a>

We now want to ensure that every column name has consistent syntax and format across all datasets, as this is crucial for merging them later.

First, we change all column names to lower case.

```{r message=FALSE, warning=FALSE}
kable(head(clean_names(daily_activity)), align = "c", caption = "Daily Activity Dataframe")
daily_activity <- rename_with(daily_activity, tolower)

kable(head(clean_names(daily_sleep)), align = "c", caption = "Daily Sleep Dataframe")
daily_sleep <- rename_with(daily_sleep, tolower)

kable(head(clean_names(hourly_calories)), align = "c", caption = "Hourly Calories Dataframe")
hourly_calories <- rename_with(hourly_calories, tolower)

kable(head(clean_names(hourly_steps)), align = "c", caption = "Hourly Steps Dataframe")
hourly_steps <- rename_with(hourly_steps, tolower)

kable(head(clean_names(hourly_intensities)), align = "c", caption = "Hourly Intensities Dataframe")
hourly_intensities <- rename_with(hourly_intensities, tolower)

kable(head(clean_names(minutes_steps_narrow)), align = "c", caption = "Minutes Steps Dataframe")
minutes_steps_narrow <- rename_with(minutes_steps_narrow, tolower)
```
![image](https://github.com/user-attachments/assets/08224fce-98de-4038-9f29-dd897758069f)
![image](https://github.com/user-attachments/assets/8205b801-2378-4c87-9b45-3d026e6aa19c)
![image](https://github.com/user-attachments/assets/b07e3c79-b2dd-41d8-b8ab-8d9ac2f07a73)
![image](https://github.com/user-attachments/assets/f6f5b1f3-3f25-42d2-a6c2-62c4fedcc58a)
![image](https://github.com/user-attachments/assets/751c24e5-55f6-4796-b1a9-8f5ad3064907)
![image](https://github.com/user-attachments/assets/ec774bb3-77c5-4b83-a2fd-32902132bc7b)

### **4.8. Formatting Date Columns** <a class="anchor"  id="formatting_date_columns"></a>

Now, we need to ensure that the 'daily_activity' and 'daily_sleep' datasets have the same date format to facilitate merging them later. We can remove the hours from the date in 'daily_sleep' since they are all set to 12:00 AM, which is irrelevant.

```{r message=FALSE, warning=FALSE}
daily_activity <- daily_activity %>%
  rename(date = activitydate) %>%
  mutate(date = mdy(date))

daily_sleep <- daily_sleep %>%
  rename(date = sleepday) %>%
  mutate(date = mdy_hms(date)) %>%
  mutate(date = as_date(date))
```

Now we verify the consistency of both datasets:

```{r message=FALSE, warning=FALSE}
kable(head(daily_activity), align = "c", caption = "Daily Activity Dataframe")
kable(head(daily_sleep), align = "c", caption = "Daily Sleep Dataframe")
```
![image](https://github.com/user-attachments/assets/a3b83622-b0b8-4435-b192-cdc9f16312a4)

![image](https://github.com/user-attachments/assets/ec83947e-4ff0-427d-ac5c-82e2137ceac9)

We now need to change the format of 'hourly_calories', 'hourly_steps', and 'hourly_intensities' from character to date-time.

```{r message=FALSE, warning=FALSE}
hourly_calories<- hourly_calories %>% 
  rename(date_time = activityhour) %>% 
  mutate(date_time = mdy_hms(date_time, tz=Sys.timezone()))

hourly_steps<- hourly_steps %>% 
  rename(date_time = activityhour) %>% 
  mutate(date_time = mdy_hms(date_time, tz=Sys.timezone()))

hourly_intensities<- hourly_intensities %>% 
  rename(date_time = activityhour) %>% 
  mutate(date_time = mdy_hms(date_time, tz=Sys.timezone()))
```

```{r message=FALSE, warning=FALSE}
kable(head(hourly_calories), align = "c", caption = "Hourly Calories Dataframe")
kable(head(hourly_steps), align = "c", caption = "Hourly Steps Dataframe")
kable(head(hourly_intensities), align = "c", caption = "Hourly Intensities Dataframe")

```
![image](https://github.com/user-attachments/assets/64efd9cd-9cb4-426b-9822-26c583abf9fe)

![image](https://github.com/user-attachments/assets/5d8ba398-5dab-4e3f-85e5-613af8eabeb8)

![image](https://github.com/user-attachments/assets/5467a93f-5c1d-41ef-bf25-1f8914b085cb)

Now we have to change the format of 'minutes_steps_narrow', from character to date-time.

```{r message=FALSE, warning=FALSE}
minutes_steps_narrow<- minutes_steps_narrow %>% 
  rename(date_time = activityminute) %>% 
  mutate(date_time = mdy_hms(date_time, tz=Sys.timezone()))

kable(head(minutes_steps_narrow), align = "c", caption = "Minutes Steps Dataframe")
```
![image](https://github.com/user-attachments/assets/f3990bcc-8bbb-4855-aba6-c2a4bebf532b)

### **4.9. Merging Datasets** <a class="anchor"  id="merging_datasets"></a>

We will now merge the 'daily_activity' and 'daily_sleep' datasets to analyze how daily activity levels affect sleep duration and sleep quality.

```{r message=FALSE, warning=FALSE}
daily_activity_sleep <- merge(daily_activity, daily_sleep, by=c ("id", "date"))
glimpse(daily_activity_sleep)
```
![image](https://github.com/user-attachments/assets/366adf04-a69a-4e21-b428-1fd5d05d80c7)

Now we will combine 'hourly_calories' with 'hourly_steps' and 'hourly_intensities' to understand the relationship between activity intensity, step count, and calorie burning throughout the day.

```{r message=FALSE, warning=FALSE}
hourly_data_a <- merge(hourly_calories, hourly_steps, by=c ("id", "date_time"))

hourly_data <- merge(hourly_data_a, hourly_intensities, by=c ("id", "date_time"))

glimpse(hourly_data)
```
![image](https://github.com/user-attachments/assets/c581ceae-ae83-41ea-a686-15499d342e80)


## **5. Analyze and Share Phase** <a class="anchor"  id="analyze_and_share_phase"></a>

Now that we have properly organized our data and ensured consistent formatting across the datasets, we can begin analyzing the data to find answers for the business task.

Let's start exploring what's the relationship between steps taken in a day and sedentary minutes:

```{r message=FALSE, warning=FALSE}
ggplot(data=daily_activity, aes(x=totalsteps, y=sedentaryminutes)) + geom_point()+geom_smooth()+
  labs(title = "Total Steps vs Sedentary Minutes",
       x = "Total Steps",
       y = "Sedentary Minutes",
       )+
  theme_stata()
```
![image](https://github.com/user-attachments/assets/106de141-e1cd-47e4-9155-dc891ea59b89)

Although the last graph does not show a strong trend, we observe a slight decrease in sedentary minutes as the total steps taken increase. However, there are still instances where significant sedentary minutes are recorded despite a high number of steps. Therefore, the graph is not very conclusive.


Now let's see what's the relationship between minutes asleep and time in bed:

```{r message=FALSE, warning=FALSE}
ggplot(data=daily_sleep, aes(x=totalminutesasleep, y=totaltimeinbed)) + geom_point()+geom_smooth()+
  labs(title = "Total Minutes Asleep vs Total Time Bed",
       x = "Total Minutes Asleep",
       y = "Total Time Bed",
       )+
  theme_stata()
```
![image](https://github.com/user-attachments/assets/a2c84071-84fe-4e00-9e14-92ce645ecf59)

The last graph shows an almost completely linear relation as expected, more time asleep means more time in bed.

Now we want to analyze how total steps can be correlated to sleep duration and sleep quality. First we going to calculate Sleep Efficiency dividing total sleep by total time in bed on the 'daily_activity_sleep' data frame.

```{r message=FALSE, warning=FALSE}
daily_activity_sleep <- daily_activity_sleep %>%
  mutate(sleep_efficiency = totalminutesasleep/totaltimeinbed)

kable(head(daily_activity_sleep), align = "c", caption = "Daily Activity & Sleep Dataframe")
```
![image](https://github.com/user-attachments/assets/3b8b0a54-9b5d-48ff-beb1-0d107b6c8dd6)

Now let's visualize total steps vs total minutes asleep, and sleep_efficiency:

```{r message=FALSE, warning=FALSE}
ggplot(data=daily_activity_sleep, aes(x=totalsteps, y=totalminutesasleep)) + geom_point()+ geom_smooth() + labs(title = "Total Steps vs Total Minutes Asleep",
       x = "Total Steps",
       y = "Total Minutes Asleep",
       )+
  theme_stata()

ggplot(data=daily_activity_sleep, aes(x=totalsteps, y=sleep_efficiency)) + geom_point()+ geom_smooth() + labs(title = "Total Steps vs Sleep Efficiency",
       x = "Total Steps",
       y = "Sleep Efficiency",
       )+
  theme_stata()
```
![image](https://github.com/user-attachments/assets/4c028b68-c4b6-46cf-bd87-388768550ac3)

![image](https://github.com/user-attachments/assets/1d3dae46-c447-4b5c-acc4-fd6aa474eb28)


There is no correlation or trend evident in the data. We observe that some individuals with good sleep quality take few steps during the day, while others who take many steps have similar sleep quality.

Another metric we would like to examine is sedentary minutes, which we will compare against sleep duration and sleep efficiency. Let’s visualize this using scatter plots.

```{r message=FALSE, warning=FALSE}
ggplot(data=daily_activity_sleep, aes(x=sedentaryminutes, y=totalminutesasleep)) + geom_point()+ geom_smooth() + labs(title = "Sedentary Minutes vs Total Minutes Asleep",
       x = "Sedentary Minutes",
       y = "Total Minutes Asleep",
       )+
  theme_stata()

ggplot(data=daily_activity_sleep, aes(x=sedentaryminutes, y=sleep_efficiency)) + geom_point()+ geom_smooth() + labs(title = "Sedentary Minutes vs Sleep Efficiency",
       x = "Sedentary Minutes",
       y = "Sleep Efficiency",
       )+
  theme_stata()
```
![image](https://github.com/user-attachments/assets/330b0d7f-9a3f-4244-95ac-c1b6b3fffb07)

![image](https://github.com/user-attachments/assets/9b729679-82df-4004-8571-a710497c1b11)

These graphs reveal some interesting insights. Firstly, we observe a negative correlation between sleep duration and sedentary minutes, as sleep duration decreases with an increase in sedentary minutes. However, the second graph shows that most individuals with sedentary minutes between 500 and 1000 tend to have better sleep efficiency.

Although sleep efficiency levels are generally high across various amounts of sedentary minutes, there is a noticeable concentration of higher sleep efficiency within the 500 to 1000 sedentary minutes range. Interestingly, this range also includes individuals with lower sleep efficiency. 

Now we want to analyse if there is any trends in activity levels and sleep metrics over time. let's start calculating the total active minutes on the daily_activity_sleep data frame:

```{r message=FALSE, warning=FALSE}
daily_activity_sleep <- daily_activity_sleep %>%
  mutate(total_active = veryactiveminutes + fairlyactiveminutes + lightlyactiveminutes)

kable(head(daily_activity_sleep), align = "c", caption = "Daily Activity & Sleep Dataframe")
```
![image](https://github.com/user-attachments/assets/342ec7b7-b810-4a0e-89cc-111551936bad)

```{r message=FALSE, warning=FALSE}
# Create the time series plots
ggplot(data = daily_activity_sleep, aes(x = date)) +
  geom_line(aes(y = total_active, color = "Total Active Minutes")) +
  labs(title = "Time Series of Activity Levels",
       x = "Date",
       y = "Total Active Minutes",
       color = "Metrics") +
  theme_stata() +
  scale_color_manual(values = c("Total Active Minutes" = "blue"))

#Total minutes Asleep
ggplot(data = daily_activity_sleep, aes(x = date)) +
  geom_line(aes(y = totalminutesasleep, color = "Total Minutes Asleep")) +
  labs(title = "Time Series of Sleep Metrics",
       x = "Date",
       y = "Total Minutes Asleep",
       color = "Metrics") +
  theme_stata() +
  scale_color_manual(values = c("Total Minutes Asleep" = "red"))
```
![image](https://github.com/user-attachments/assets/bc809003-c6ba-44f4-a2e1-e350468418fc)

![image](https://github.com/user-attachments/assets/f30e62f5-9fc8-4af3-b289-e2347b6cff64)

As we can observe, there are no evident trends in any of the graphs. The sleep metrics and total active time of users show fluctuations over time, suggesting that people are not significantly changing their behavior when using the Bellabeat product.


Now, we would like to understand how activity levels can be classified based on sleep metrics. Let’s begin by gaining a comprehensive understanding of the activity levels:

```{r message=FALSE, warning=FALSE}
# Group data by total active minutes and calculate summary statistics
summary_stats <- daily_activity_sleep %>%
    summarize(
    min_total_active = min(total_active),
    max_total_active = max(total_active),
    median_total_active = median(total_active),
    mean_total_active = mean(total_active),
    sd_total_active = sd(total_active)
  )

# Print the summary statistics
kable(summary_stats, align = "c", caption = "Summary Stats of Activity Levels")
```
![image](https://github.com/user-attachments/assets/a089dfcb-4cbc-4f08-9a45-b0898ee6f8be)

Based on the results, we can classify activity levels as follows: active minutes below 200 are considered Low, a range between 200 and 270 is considered Medium, and above 270 is considered High.

```{r message=FALSE, warning=FALSE}
daily_activity_sleep <- daily_activity_sleep %>%
  mutate(activity_levels = case_when(
    total_active < 200 ~ "low",
    total_active >= 200 & total_active < 270 ~ "medium", 
    total_active >= 270 ~ "high"
  ))

kable(head(daily_activity_sleep), align = "c", caption = "Daily Activity & Sleep Dataframe")
```
![image](https://github.com/user-attachments/assets/31e1ab6d-1597-4dee-bbac-53175ac04c08)


Now, we are going to calculate the mean total minutes asleep and sleep efficiency for each activity level:

```{r message=FALSE, warning=FALSE}
# Group data by activity_levels and calculate average sleep metrics
average_sleep_metrics <- daily_activity_sleep %>%
  group_by(activity_levels) %>%
  summarize(
    average_sleep_duration = mean(totalminutesasleep),
    average_sleep_efficiency = mean(sleep_efficiency)
  )

# Print the average sleep metrics
kable(average_sleep_metrics, align = "c", caption = "Average Sleep Metrics by Activity Levels")
```
![image](https://github.com/user-attachments/assets/8ad76b06-1388-4da0-9669-ae5ea8011e92)

Now, let’s visualize the data using a bar chart:

```{r message=FALSE, warning=FALSE}

# Set the desired order of activity levels to show on the bar chart
activity_levels_order <- c("low", "medium", "high")

# Create the bar chart
ggplot(average_sleep_metrics, aes(x = factor(activity_levels, levels = activity_levels_order), y = average_sleep_duration, fill = activity_levels)) +
  geom_bar(stat = "identity") +
  labs(title = "Average Sleep Duration by Activity Level",
       x = "Activity Level",
       y = "Average Sleep Duration (minutes)") +
  theme_stata()

ggplot(average_sleep_metrics, aes(x = factor(activity_levels, levels = activity_levels_order), y = average_sleep_efficiency, fill = activity_levels)) +
  geom_bar(stat = "identity") +
  labs(title = "Average Sleep Efficiency by Activity Level",
       x = "Activity Level",
       y = "Average Sleep Efficiency") +
  theme_stata()
```
![image](https://github.com/user-attachments/assets/65c3d625-7f1e-4415-a51d-114af4df873f)

![image](https://github.com/user-attachments/assets/a4811b9f-93fe-493a-a52e-e72e16d841b4)

We observe something very interesting here. The first graph shows that individuals with a low activity level have longer sleep duration. However, the second graph does not provide conclusive evidence that activity level affects sleep quality, as the average sleep efficiency is quite similar across all activity levels.

Now, we will focus on the hourly trends. For this analysis, we will use the 'hourly_data' dataframe, which we previously created by merging 'hourly_calories', 'hourly_steps', and 'hourly_intensities'.

Let’s begin by visualizing the relationship between calories burned and steps taken. We expect to see a positive correlation, as it is reasonable to assume that people who take more steps burn more calories.

```{r message=FALSE, warning=FALSE}
# Scatter plot of calories vs. steps
ggplot(hourly_data, aes(x = steptotal, y = calories)) +
  geom_point() +
  labs(title = "Calories Burned vs. Steps Taken",
       x = "Steps Taken",
       y = "Calories Burned")+
  theme_stata()
```
![image](https://github.com/user-attachments/assets/8e858726-6186-48e0-b94d-c33c79b735a9)

As we expected there is a positive correlation between calories burned and steps taken. Now let's explore the relationship between intensity and calorie burn. We going to use two scatter plots, one to graph total intensity vs calories, and another to graph average intensity vs calories.

```{r message=FALSE, warning=FALSE}
# Scatter plot of  intensity vs. calories
ggplot(hourly_data, aes(x = totalintensity, y = calories)) +
  geom_point() +
  labs(title = " Total Intensity vs. Calories Burned",
       x = "Total Intensity",
       y = "Calories Burned")+
  theme_stata()

# Scatter plot of  average intensity vs. calories
ggplot(hourly_data, aes(x = averageintensity, y = calories)) +
  geom_point() +
  labs(title = " Average Intensity vs. Calories Burned",
       x = "Average Intensity",
       y = "Calories Burned")+
  theme_stata()
```
![image](https://github.com/user-attachments/assets/1ee4f87e-378e-4866-9992-aaec7b4f179a)

![image](https://github.com/user-attachments/assets/75f8de9d-ae9c-4a40-8cff-748cc6e38d24)

As we can see, both graphs are consistent, showing a positive correlation between the variables. This indicates that as the activity intensity of individuals increases, they burn more calories.

Now we will create time series plots to observe how calories, total steps, and total intensity or average intensity change throughout time. This can help identify patterns and trends.

```{r message=FALSE, warning=FALSE}
# Create the time series plots - Calories over time
ggplot(data = hourly_data, aes(x = date_time)) +
  geom_line(aes(y = calories, color = "Calories Burned")) +
  labs(title = "Time Series of Calories Burned",
       x = "Date Time",
       y = "Calories Burneds",
       color = "Metrics") +
  theme_stata() +
  scale_color_manual(values = c("Calories Burned" = "blue"))

# Create the time series plots - Total Steps over time
ggplot(data = hourly_data, aes(x = date_time)) +
  geom_line(aes(y = steptotal, color = "Total Steps")) +
  labs(title = "Time Series of Total Steps",
       x = "Date Time",
       y = "Total Steps",
       color = "Metrics") +
  theme_stata() +
  scale_color_manual(values = c("Total Steps" = "red"))

# Create the time series plots - Total Intensity over time
ggplot(data = hourly_data, aes(x = date_time)) +
  geom_line(aes(y = totalintensity, color = "Total Intensity")) +
  labs(title = "Time Series of Total Intensity",
       x = "Date Time",
       y = "Total Intensity",
       color = "Metrics") +
  theme_stata() +
  scale_color_manual(values = c("Total Intensity" = "green"))

# Create the time series plots - Average Intensity over time
ggplot(data = hourly_data, aes(x = date_time)) +
  geom_line(aes(y = averageintensity, color = "Average Intensity")) +
  labs(title = "Time Series of Average Intensity",
       x = "Date Time",
       y = "Average Intensity",
       color = "Metrics") +
  theme_stata() +
  scale_color_manual(values = c("Average Intensity" = "purple"))
```
![image](https://github.com/user-attachments/assets/1526d43d-b2d9-4361-a8f2-9a509a7d37c0)

![image](https://github.com/user-attachments/assets/399a0faa-07f2-4f3e-895d-c7ede53a2426)

![image](https://github.com/user-attachments/assets/6e95573e-3a18-4800-9d08-f7b6aee70209)

![image](https://github.com/user-attachments/assets/33800fa6-5b4a-4d55-8ed4-65f67d07087d)

From the four graphs visualized earlier, we can see that although there are no evident trends, a repeating pattern is present in each variable. This suggests that most individuals follow a certain daily routine.

Now, we would like to create some heat maps to analyze the variables across different hours. To do this, we will start by extracting the hour from the 'date_time' column and then plot the heat maps.

```{r message=FALSE, warning=FALSE}
# Create a new column for the hour of the day
hourly_data$hour <- format(hourly_data$date_time, format = "%H")

# Create the heatmap of Average Intensity
hourly_data$hour <- as.numeric(hourly_data$hour)

ggplot(hourly_data, aes(x = hour, y = averageintensity, fill = calories)) +
  geom_tile() +
  scale_fill_gradient(low = "yellow", high = "red", name = "Calories")+
  scale_x_continuous(limits = c(0, 23)) +
  labs(title = "Hourly Calories Burned vs. Average Intensity",
       x = "Hour of the Day",
       y = "Average Intensity") +
  theme_stata()
```
![image](https://github.com/user-attachments/assets/01949202-833c-4257-8648-dee6190ebe96)

According to the graph, although the trend is not very clear, it appears that there is more activity between 8-11 AM and 5-7 PM. Additionally, we can see that most individuals do activities of low intensity with small amounts of calories burned. To further validate this, let’s create bar chart focusing solely on the calories burned throughout the day. 

```{r message=FALSE, warning=FALSE}
# Summarize the data to get the average calories for each hour
barchart_data <- hourly_data %>%
  group_by(hour) %>%
  summarize(avg_calories = mean(calories, na.rm = TRUE))

# Create the bar chart
ggplot(barchart_data, aes(x = hour, y = avg_calories, fill = avg_calories)) +
  geom_bar(stat = "identity") +
  scale_fill_gradientn(colors = c("blue", "red"), name = "Avg Calories",
                       breaks = seq(min(barchart_data$avg_calories), max(barchart_data$avg_calories), by = 13),
                       labels = scales::comma) +
  labs(title = "Calories Burned Across Different Hours of the Day",
       x = "Hour of the Day",
       y = "Calories Burned") +
  theme_stata()
```
![image](https://github.com/user-attachments/assets/ae62d7f1-dc40-4c9d-98f3-727395d4afcd)

Based on the last graph, we can confirm that the periods of highest activity and more calories burned are from 8 AM to 2 PM and from 5 PM to 7 PM.

Let's see now how the steps taken change across the hours of the day.

```{r message=FALSE, warning=FALSE}
# Summarize the data to get the average steps for each hour
barchart_data_s <- hourly_data %>%
  group_by(hour) %>%
  summarize(avg_steps = mean(steptotal, na.rm = TRUE))

# Create the bar chart
ggplot(barchart_data_s, aes(x = hour, y = avg_steps, fill = avg_steps)) +
  geom_bar(stat = "identity") +
  scale_fill_gradientn(colors = c("yellow", "red"), name = "Avg Steps",
breaks = seq(min(barchart_data_s$avg_steps), max(barchart_data_s$avg_steps), by = 142),
                       labels = scales::comma) +
  labs(title = "Steps Taken Across Different Hours of the Day",
       x = "Hour of the Day",
       y = "Average Steps Taken") +
  theme_stata()
```
![image](https://github.com/user-attachments/assets/2b73b4a1-e90c-44ec-a830-3db0b5586e05)

This graph aligns with the findings from the bar chart of calories. Additionally, we can clearly identify that the period between 6 and 7 PM is when users take the most steps. 

Let's continue analyzing the steps taken across time, but now using the 'minutes_steps_narrow' data frame.


```{r message=FALSE, warning=FALSE}
# Extract hour from date_time
minutes_steps_narrow$hour <- hour(minutes_steps_narrow$date_time)

# Calculate hourly step counts
hourly_steps <- minutes_steps_narrow %>%
  group_by(id, hour) %>%
  summarize(total_steps = sum(steps), .groups = 'drop')

# Create a time series plot
ggplot(data = hourly_steps, aes(x = hour, y = total_steps,color = "Total Steps", group = id)) +
  geom_line() +
  labs(title = "Hourly Step Counts",
       x = "Hour of the Day",
       y = "Total Steps",
       color = "Metrics") +
  theme_stata()+
  scale_color_manual(values = c("Total Steps" = "blue"))+
  theme(axis.text.y = element_text(size = 10, angle = 0))
```
![image](https://github.com/user-attachments/assets/ede006f6-43ca-4406-8c38-ee314e606868)

As we can see, there are peaks in the number of steps at 8 AM, 2 PM, and 7 PM, with smaller peaks at 9 AM, 12 PM, and 1 PM. We could use this information to send notifications reminding users to walk during these times.


## **6. Conclusion and Recommendations** <a class="anchor"  id="conclusion_and_recommendations"></a>

After analyzing the data and reviewing the results, we can summarize our findings and provide recommendations to address the business task: informing the marketing strategy and unlocking new growth opportunities for the company.

We recommend the company to collect more data to enable a deeper analysis. Currently, the sample size is too small, which can lead to biased information.

### **6.1. Summary of Key Findings:** <a class="anchor"  id="summary_of_key_findings"></a>

**Sedentary Behavior:**

There’s a slight negative correlation between sedentary minutes and total steps, but it’s not very strong. Many users remain sedentary even if they take a significant number of steps.

**Sleep Metrics:**

Sleep duration and time in bed are positively correlated. However, there’s no clear link between steps and sleep metrics. Sleep efficiency remains high across different activity levels.

**User Behavior:**

Users show consistent daily routines, with activity levels and calorie burn fluctuating over time.

**Activity Patterns:**

Most activity happens during specific periods (8-11 AM, 5-7 PM). Low-intensity activities are predominant, with peaks in steps at 8 AM, 2 PM, and 7 PM.


### **6.2. Recommendations for Bellabeat:** <a class="anchor"  id="recommendations_for_bellabeat">

**Promote Sedentary Breaks:**

Encourage users to take short breaks throughout the day to reduce sedentary time, even if they’re active. This could involve integrating reminders or suggestions into the app.

**Personalized Activity Recommendations:**

Use data to provide personalized activity recommendations based on individual goals and lifestyles. This could include suggestions for specific exercises or activities to complement their daily routine.

**Sleep Optimization:**

Explore features to improve sleep quality, such as sleep tracking, relaxation techniques, or bedtime reminders. This could enhance user satisfaction and overall well-being.

**Gamification:**

Incorporate gamification elements to motivate users to increase activity levels and meet their goals. This could involve challenges, rewards, or leaderboards.

**Community Building:**

Foster a sense of community among users to encourage support, motivation, and shared experiences. This could involve online forums or social features within the app.

**Targeted Marketing:**

Use insights from the analysis to tailor marketing campaigns to specific user segments. For example, target individuals with high sedentary levels, those seeking to improve sleep quality, or those who are not taking enough steps a day.

**Product Enhancements:**

Explore new features or product enhancements based on user needs and preferences. This could include additional sensors, integration with other devices, or personalized coaching.


As mentioned earlier, we encourage Bellabeat to continue collecting this kind of data and increase the sample size. Adding information about the users’ locations could also be useful. This would allow for deeper analysis and more targeted marketing strategies, including demographic considerations. 






































