# school_district_analysis
School district analysis using Pandas  

### Table of Contents
- [1 Overview of School District Analysis](#1-overview-of-school-district-analysis)
  - [1.1 Requirements](#11-requirements)
- [2 Results](#2-results)
- [3 Summary](#3-summary)


## 1 Overview of School District Analysis 

The purpose of the overall school district analysis is to assist Maria in analyzing students' standardized test scores for math and reading as well as supplemental information on the schools they attend. In this portion of the analysis, Maria has been notified of evidence of academic dishonesty - specifically with the math and reading scores for Thomas High School. Grades appear to have been altered, and the challenge was to replace grades for THS and rerun the school district analysis. The insights derived from this analysis should be used to inform discussions and strategic decisions at the school and district level. The following sections discuss the results of the school district analysis and a summary highlighting significant changes to the school district analysis after scores were updated. 

### 1.1 Requirements 

- [x] Select all the reading and math scores from the ninth grade at Thomas High School

Additionally, the following metrics were recreated: 
- [x] The district summary
- [x] The school summary
- [x] The top 5 and bottom 5 performing schools, based the overall passing rate
- [x] The average math score for each grade level from each school
- [x] The average reading score for each grade level from each school
- [x] The scores by school spending per student, by school size, and by school type

## 2 Results

### 2.1 How is the district summary affected?

The changes between the original and recreated school district summary only differ slightly - 

- the Average Math Score for the school district decreased by **0.1** from 79.0 to 78.9; 
- % Passing Math decreased by **0.2** from 75% to 74.8%; 
- % Passing Reading decreased by **0.3** from 86% to 85.7%; and 
- % Overall Passing decreased by **0.1** from 65% to 64.9%. 

Images of the two DataFrames are portrayed below: 

#### Original: 
<img width="922" alt="Screen Shot 2022-02-01 at 6 54 01 PM" src="https://user-images.githubusercontent.com/95978097/152086127-d03b5cc5-e289-4fff-af68-d3bb45dffb46.png">

#### Updated:
<img width="922" alt="Screen Shot 2022-02-01 at 6 52 28 PM" src="https://user-images.githubusercontent.com/95978097/152085978-3a3892fa-a6f4-4a5d-a647-46ddb91f83d7.png">

### 2.2 How is the School Summary Affected?

The per school summary was affected because incorrect standardized test scores for Thomas High School were included in this DataFrame. Between the original and updated per school summary, the following columns and values differed for Thomas High School:

- average math score decreased by **0.05** points from 83.41 to 83.36
- average reading score increased by **0.05** points from 83.85 to 83.9
- % passing math decreased **26.36%** from 93.27% to 66.91%
- % passing reading decreased **27.65%** from 97.31% to 69.66%
- % overall passing decreased **25.87%** from 90.95% to 65.08%

Images of the original and updated DataFrames for the Per School Summary are shown below: 
##### Original: 
<img width="893" alt="Screen Shot 2022-02-01 at 7 29 49 PM" src="https://user-images.githubusercontent.com/95978097/152088802-d43f3b61-28e3-4f03-b901-7745572a5cc2.png">

##### Updated:
<img width="893" alt="Screen Shot 2022-02-01 at 7 31 34 PM" src="https://user-images.githubusercontent.com/95978097/152088949-0271e4b5-04ca-4f00-b1a0-05d2442f0fd0.png">


### 2.3 Replacing Ninth Grade Scores

Replacing the ninth grade math and reading scores to NaN for Thomas High School greatly reduced its perceived performance against the other schools in the district. 
Without recalculating the new student count for THS, inaccurate data were included to get % Passing Math, % Passing Reading, and % Overall Passing - making it appear that THS had one of the lowest passing percentages in the district (which ultimately is incorrect.) 

#### *Math and Reading Scores by Grade*

When analyzing other metrics in this analysis, replacing the reading and math scores for THS' ninth graders eliminated any data for standardized testing scores for ninth graders at THS, making any *valid* comparison for ninth grade inaccurate. A code snippet and DataFrames for math and reading scores by grade are displayed below: 

````
# Combine each Series for average math scores by school into single data frame.
math_scores_by_grade = pd.DataFrame({
               "9th": ninth_grade_math_scores,
               "10th": tenth_grade_math_scores,
               "11th": eleventh_grade_math_scores,
               "12th": twelfth_grade_math_scores})

# Combine each Series for average reading scores by school into single data frame.
reading_scores_by_grade = pd.DataFrame({
              "9th": ninth_grade_reading_scores,
              "10th": tenth_grade_reading_scores,
              "11th": eleventh_grade_reading_scores,
              "12th": twelfth_grade_reading_scores})
````
##### Average Math Score by Grade: 
<img width="386" alt="Screen Shot 2022-02-02 at 8 19 30 AM" src="https://user-images.githubusercontent.com/95978097/152193599-8cd2a179-9122-447e-9b86-2c98c6a726f3.png">

##### Average Reading Score by Grade: 
<img width="386" alt="Screen Shot 2022-02-02 at 8 23 23 AM" src="https://user-images.githubusercontent.com/95978097/152194313-915104a7-44b3-4884-afc6-2c6d4f23f83b.png">

#### *Scores by School Spending*
Alternatively, replacing ninth grade scores did not change the outcome of the updated scores by school spending metric. Thomas High School still has a spending range (per student) of $630-$644 while values in each column remain the same. Images and code snippets of the original and updated DataFrames for the two analyses are shown below:

````
# Establish the spending bins and group names.
spending_bins = [0, 585, 630, 645, 675]
group_names = ["<$584", "$585-629", "$630-644", "$645-675"]
# Categorize spending based on the bins.
per_school_summary_df["Spending Ranges (Per Student)"] = pd.cut(per_school_capita, spending_bins, labels=group_names)

# Calculate averages for the desired columns. 
spending_math_scores = per_school_summary_df.groupby(["Spending Ranges (Per Student)"]).mean()["Average Math Score"]

spending_reading_scores = per_school_summary_df.groupby(["Spending Ranges (Per Student)"]).mean()["Average Reading Score"]

spending_passing_math = per_school_summary_df.groupby(["Spending Ranges (Per Student)"]).mean()["% Passing Math"]

spending_passing_reading = per_school_summary_df.groupby(["Spending Ranges (Per Student)"]).mean()["% Passing Reading"]

overall_passing_spending = per_school_summary_df.groupby(["Spending Ranges (Per Student)"]).mean()["% Overall Passing"]
````
##### Original:
<img width="734" alt="Screen Shot 2022-02-02 at 8 40 46 AM" src="https://user-images.githubusercontent.com/95978097/152197469-10e5c974-3905-4d3c-9307-3c875786cbec.png">

##### Updated: 
<img width="734" alt="Screen Shot 2022-02-02 at 8 41 10 AM" src="https://user-images.githubusercontent.com/95978097/152197539-19cbb05d-5073-4582-8f2c-63a73564c1a1.png">

#### *Scores by School Size*
