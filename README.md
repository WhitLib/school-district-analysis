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
#### Original: 
<img width="893" alt="Screen Shot 2022-02-01 at 7 29 49 PM" src="https://user-images.githubusercontent.com/95978097/152088802-d43f3b61-28e3-4f03-b901-7745572a5cc2.png">

#### Updated:
<img width="893" alt="Screen Shot 2022-02-01 at 7 31 34 PM" src="https://user-images.githubusercontent.com/95978097/152088949-0271e4b5-04ca-4f00-b1a0-05d2442f0fd0.png">


### 2.3 Replacing Ninth Grade Scores
