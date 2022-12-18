# Projects

## Scenario

You are a junior data analyst working on the marketing analyst team at Bellabeat, a high-tech manufacturer of health-focused products for women. Bellabeat is a successful small company, but they have the potential to become a larger player in the global smart device market. Urška Sršen, cofounder and Chief Creative Officer of Bellabeat, believes that analyzing smart device fitness data could help unlock new growth opportunities for the company. You have been asked to focus on one of Bellabeat’s products and analyze smart device data to gain insight into how consumers are using their smart devices. The insights you discover will then help guide marketing strategy for the company. You will present your analysis to the Bellabeat executive team along with your high-level recommendations for Bellabeat’s marketing strategy.In order to answer the key business questions, you will follow the steps of the
data analysis process: ask, prepare, process, analyze, share, and act.

## ASK
    
**The business task at hand:** 
   
- The current task is to use smart device data from existing Bellabeat customers to track how they’re using their devices in order to leverage these trends to inform Bellabeat’s future marketing strategy.
   
**Key Stakeholders**
   
- Urška Sršen: Bellabeat’s cofounder and Chief Creative Officer <br>
- Sando Mur: Mathematician and Bellabeat’s cofounder; key member of the Bellabeat executive team <br>
- Bellabeat marketing analytics team

## PREPARE

**Data to be used in our analysis:**
   
- All data is public domain, derived from [Fitbit Fitness Tracker Data](https://www.kaggle.com/datasets/arashnic/fitbit). The Kaggle data set contains personal fitness tracker from thirty fitbit users. Thirty eligible Fitbit users consented to the submission of personal tracker data, including minute-level output for physical activity, heart rate, and sleep monitoring. It includes information about daily activity, steps, and heart rate that can be used to explore users’ habits across various excel spreadsheets.

**How is it organized?** 
   
- Data is organized by both time and category. The categories are daily activity, daily calories, daily intensity, daily steps, and daily sleep, broken out into separate sheets giving these metrics per day, per hour, or per minute. For this case study, we’ll focus on these categories broken out per day. 
   
**Potential issues:**
   
- Data is said to have been collected from 30 FitBit users from 3/12/2016 - 5/12/2016. This data is not current and also does not differentiate between male/female users, so the data is likely biased against information about female users. While the sample size of 30 is also a small sample size, it still satisfies the Central Limit Theorem for how many unique variables should be included in a dataset.

## PROCESS

**Cleaning or data manipulation documentation:**

Given the size of the datasets, much of the cleaning was able to occur in Excel. I first verified the number of unique participants who provided data for each category and also verified the length of time which they provided that data. 

*daily_activity_merged* <br>
    Number of Unique Users -- 33 <br>
    Min Date -- 4/12/2016 <br>
    Max Date --5/12/2016 <br>

*daily_calories_merged* <br>
    Number of Unique Users -- 33 <br>
    Min Date -- 4/12/2016 <br>
    Max Date -- 5/12/2016 <br>

*daily_intensities_merged* <br>
    Number of Unique Users -- 33 <br>
    Min Date -- 4/12/2016 <br>
    Max Date -- 5/12/2016 <br>

*daily_sleep_merged* <br>
    Number of Unique Users -- 24 <br>
    Min Date -- 4/12/2016 <br>
    Max Date -- 5/12/2016 <br>

*daily_steps_merged* <br>
    Number of Unique Users -- 33 <br>
    Min Date -- 4/12/2016 <br>
    Max Date --5/12/2016 <br>
    
    We now see that all datasets other than daily_sleep_merged contained information from 33 unique users (rather than 30), with all information having been provided between 4/12/2016 and 5/12/2016 (rather than between 3/12/2016 and 5/12/2016). I then verified that the 33 respondants for the applicable datasets were the same respondants across all datasets that had 33 users, which was verified as true. Given that 4 of the 5 datasets have 33 identical users providing data, daily_activity_merged, daily_calories_merged, daily_intensities_merged, and daily_steps_merged will be the primary datasets we work with, while we'll work with daily_sleep_merged for the sake of supplimentary data.

I then performed the following cleaning steps in Excel: 

- Changed all column headers to consistent formatting while renaming different columns that provided the same information (such as "ActiveDay" and "SleepDay" as "date")
- Used conditional formatting to identify any cells that contained errors or blanks 
- Changed the datatypes of all columns to their applicable type
- Verified no rows contained any "NA" cells 
- Verified no rows contained duplicate information 
- Columns are being added to each dataset that indicate the day of the week that the data was collected using the following formula: =CHOOSE(WEEKDAY(B2),"Sun","Mon","Tue","Wed","Thu","Fri","Sat")
- I then saved all spreadsheets as .csv for data import 

Additional SQL Cleaning  

- Checked that all datatypes are consistent with the type of data each column is intended to display, no need for CAST function to change 
- Confirmed number of unique user ID’s using DISTINCT 

Additional R Cleaning 

- Packages downloaded into R:
