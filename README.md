# Pwc Switzerland Power BI virtual case experience - Gender Diversity and Inclusion Analysis

![GenderDiversityDashboard ](https://github.com/Harsh-2412/Gender-Diversity-And-Inclusion/assets/110857650/49e666fe-9fbe-4129-9dda-5005710a3b23)

## Business Problem 
> Human Resources at our telecom client is highly into diversity and inclusion.
 They’ve been working hard to improve gender balance at the executive management level, but they’re not seeing any progress.
They’re reaching out to us for help.
At PwC Switzerland we are often approached by clients seeking support with diversity and inclusion.
Companies need a workforce of diverse talents and backgrounds to succeed in an increasingly complex and heterogeneous world.
To us, diversity and inclusion are business imperatives, not just nice-to-haves. We aim for all of our teams to feel welcome and appreciated.
But actually achieving this and unlocking its potential involves a whole set of practical challenges.

## Project Task Overview
> The following measures were used to define proper KPIs:
> * '#' of men
> * '#' of women
> * '#' of leavers
> * % employees promoted (FY21)
> * % of women promoted
> * % of hires men
> * % of hires women
> * % turnover 
> * Average performance rating: men
> * Average Performance rating: women

---

##  Table of Contents
> * Data Sourcing
> * Data Preparation
> * Data Modeling
> * Data Visualization
> * Data Analysis
> * Insights
> * Shareable link

## Data Sourcing
 >The Dataset used for this analysis was presented by Pwc Switzerland and available at:

[Diversity-Inclusion-Dataset](https://github.com/Harsh-2412/Gender-Diversity-And-Inclusion/files/11545937/03.Diversity-Inclusion-Dataset.xlsx)

----
## Data Preparation
> Data transformation was done in Power Query and the dataset was loaded into Microsoft Power BI Desktop for modeling.
> The diversity and inclusion dataset is given by a table named:  
> PharmaData which has 32 columns and 500 rows of observation. 
> 
> The tabulation below shows the PharmaData table with its column names and their description :  
---
### Column Names and Descriptions

| Column Name                           | Description                                                    |
|---------------------------------------|----------------------------------------------------------------|
| Employee ID                           | Represents the unique number of the employee in the dataset     |
| Gender                                | Describes the gender of the employee                            |
| DAX Measures                          | Desvcribes the various Measures used to define KPI's            |
| Job Level after FY20 promotions       | Describes the job level of the employee after being promoted in FY20 |
| New hire FY20?                        | Describes if the employee is a new hire in FY20                |
| FY20 Performance Rating               | Represents the performance rating of the employee in FY20       |
| Promotion in FY21?                    | Describes if the employee is being promoted in FY21             |
| In base group for Promotion FY21      | Describes if the employee is being selected for promotion in FY21 |
| Target hire balance                   | Describes the target hire balance of the employee              |
| FY20 leaver?                          | Describes if the employee is a leaver in FY20                   |
| In base group for turnover FY20       | Describes if the employee is in a group for turnover in FY20    |
| Department @01.07.2020                | Describes the department each employee belongs to as at January 7, 2020 |
| Leaver FY                             | Describes if the employee is a leaver in a FY                   |
| Job Level after FY21 promotions       | Describes the job level of the employee after being promoted in FY21 |
| Last Department in FY20               | Describes the last department each employee belongs in FY20     |
| FTE group                             | Describes if the employee belongs to an FTE group               |
| Time type                             | Describes the contract type of the employee                     |
| Department & JL group PRA status      | Describes the department and JL group PRA status of the employee |
| Department & JL group for PRA         | Describes the department and JL group PRA of the employee       |
| Job Level group PRA status            | Describes the job level group PRA status of the employee        |
| Job Level group for PRA               | Describes the job level group PRA of the employee               |
| Time in Job Level @01.07.2020         | Describes the time in job level of the employee                 |
| Job Level before FY20 promotions      | Describes the job level of the employee before being promoted in FY20 |
| Promotion in FY20?                    | Describes if the employee is being promoted in FY20             |
| FY19 Performance Rating               | Describes the performance rating of the employee in FY19        |
| Age group                             | Describes the age group of the employee                         |
| Age @01.07.2020                       | Represents the age of the employee as at January 07, 2020       |
| Nationality 1                         | Describes the nationality of the employee at the state level    |
| Region group: nationality 1           | Describes the nationality of the employee at the country level  |
| Broad region group: nationality 1     | Describes the nationality of the employee at the regional level |
---
## Data Modeling
> Post the cleansing and transformation of Dataset used it was ready to be modeled in  Power BI Desktop).
> The fact and dimension have been combined into a single table and is shown in the data model below.
---
## Data Visualization
>Data visualization for the dataset was done in 2 folds using Microsoft Power BI Desktop:
---
> Diversity & Inclusion Analysis (1/2) Page: Shows the Hirees KPI, Promotions KPI  and Turnover Rate (FY20 leavers) KPI, e.t.c
> Diversity & Inclusion Analysis (2/2) Page: Shows the Performance rating KPI,   Age Group KPI, Executive Gender Balance KPI e.t.c
----
## Data Analysis
There were Various Measures used to define KPI's , Namely :
### Expressions

| Name                  | Expression                                                                                                                                                        |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Male employees        | Calculate(distinctcount('PharmaData'[Employee ID]),Filter('PharmaData','PharmaData'[Gender] = "Male"))                                                           |
| Female Employees      | COUNTROWS(FILTER('PharmaData', 'PharmaData'[Gender] = "Female"))                                                                                                  |
| Exiting Employees     | COUNTROWS(FILTER('PharmaData', 'PharmaData'[FY20 leaver?] = "Yes"))                                                                                                |
| FemalePromotee%       | DIVIDE( COUNTROWS(FILTER('PharmaData', 'PharmaData'[Gender] = "Female")), COUNTROWS('PharmaData'))                                                                |
| MalePromotee%         | DIVIDE( COUNTROWS(FILTER('PharmaData', 'PharmaData'[Gender] = "Male")), COUNTROWS('PharmaData'))                                                                  |
| % of Males Hired      | DIVIDE('PharmaData'[Male employees], 'PharmaData'[Male employees] + 'PharmaData'[Female Employees])                                                               |
| % of Females Hired    | DIVIDE('PharmaData'[Female Employees], 'PharmaData'[Male employees] + 'PharmaData'[Female Employees])                                                             |
| Avg Rating Men        | CALCULATE( AVERAGE(PharmaData[FY20 Performance Rating]), FILTER('PharmaData' ,PharmaData[Gender] = "Male"))                                                        |
| Avg Rating Women      | CALCULATE( AVERAGE(PharmaData[FY20 Performance Rating]), FILTER('PharmaData' ,PharmaData[Gender] = "Female"))                                                      |
| Turnover %            | Divide( CALCULATE( DISTINCTCOUNT('PharmaData'[Employee ID]), FILTER('PharmaData', 'PharmaData'[FY20 leaver?] = "Yes")), Divide(Calculate(distinctcount('PharmaData'[Employee ID]),Filter('PharmaData','PharmaData'[In base group for turnover FY20]="Y"))+Calculate(distinctcount('PharmaData'[Employee ID]),Filter('PharmaData',NOT('PharmaData'[Department @01.07.2020]=BLANK()))),2)) |

---

## Insights
Insights post Analysis and Visualisation :

> * 41% of Hirees were Female.  
> * 59%  of Hirees were male.  
> * 53% of women were hired for Junior Manger role.   
> * Only 12 Male and 7 Female employees had an perfomance rating of 4.  
> * 52% percent of Feamle workers were promoted to the post OF Senior Manager. 
> * Avg Perofmance Rating Women 2.42  .  
> * Avg Perfomance Rating Men 2.41 .  
> * The majority of the workforce consists of 223 employees in the age group of (20 to 29).
---
## Checkout The Dashboard here 
[Gender Diversity & Inclusivity Dashboard](https://app.powerbi.com/view?r=eyJrIjoiZTIxYzVmNTQtZTJkZS00YWEyLTg5MzktMmNmYzg1NTJhMzVjIiwidCI6ImE2Y2E4Mzc0LTgwOWUtNGYwYi05Mzg2LTkzN2E0YjQ0NmEwYiIsImMiOjEwfQ%3D%3D)





