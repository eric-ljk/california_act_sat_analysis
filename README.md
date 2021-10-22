<img src="http://imgur.com/1ZcRyrc.png" style="float: left; margin: 20px; height: 55px">

# Project 1: Standardized Test Analysis 

--- 

# Problem Statement

## Context:

You are a data science professional for an education startup offering enrichment workshops for both the ACT and SAT. The startup is based in California, USA. As a first step, the startup wants to promote their classes to schools involved with both the SAT and ACT, since they could be bigger clients. However, since there may still be several hundred possible schools, the Business Development team would like to know which ones to start pitching to to get the fastest results. 

## Data Science Problem 

Out of schools in California administering both the ACT and the SAT, this analysis aims to study which schools perform the worst on both these assessments, since these schools would have the greatest need for enrichment workshops. 

# Background

The ACT and SAT are standardized tests that many colleges and universities in the United States require for their admissions process. 

The ACT has 4 sections: English, Mathematics, Reading, and Science, with an additional optional writing section ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html)). 
* Each section has possible scores of 1-36, and the total score is a composite score of 1-36 as well, which is the average of all the sections ([*source*](https://www.act.org/content/dam/act/unsecured/documents/Using-Your-ACT-Results-20-21.pdf)). 
* The 2019 national average ACT composite score was 20.7 ([*source*](https://www.act.org/content/dam/act/unsecured/documents/National-CCCR-2019.pdf))
    * There are College Readiness Benchmarks for each section which indicate that a student "has at least a 50 percent chance of getting a B or higher in a corresponding first-year college course". These range from 18-23. ([*source*](https://www.act.org/content/dam/act/unsecured/documents/pdfs/R1670-college-readiness-benchmarks-2017-11.pdf))

The SAT has two sections of the test: Evidence-Based Reading and Writing (ERW), and Math ([*source*](https://www.princetonreview.com/college/sat-sections)). 

* Each section has possible scores of 200-800, and the total score would be 400-1600 ([*source*](https://collegereadiness.collegeboard.org/sat/scores/understanding-scores/interpreting)). 

* The 2019 national average percentage meeting College and Career Readiness benchmarks for ERW, Math and both sections were 68%, 48% and 45% respectively ([*source*](https://reports.collegeboard.org/pdf/2019-total-group-sat-suite-assessments-annual-report.pdf)). 
    * Meeting the benchmarks indicate a "75% chance of earning at least a C in first-semester, credit-bearing, college-level courses" for the associated subject. Each Grade level has their respective benchmark, and it indicates if the student is on track for the aforementioned estimation. ([*source*](https://reports.collegeboard.org/pdf/2019-total-group-sat-suite-assessments-annual-report.pdf))
    
## Project Organisation:

This repo has been organised into 3 folders: 

### /code

This folder contains 3 Jupyter notebooks. 
* Start with `act_sat_main.ipynb`. 
* Then, refer to `act_sat_data_cleaning_1.ipynb`, and then `act_sat_data_cleaning_2.ipynb` for the data cleaning portion. 
* The rest of the project continues in the main notebook. 

### /data

This folder contains initial and final datasets in .csv files. There should be one pair for ACT and one pair for SAT data.

### /refs

Some of the web links may be inaccessible to Internet users outside of America. PDF versions of the links are found in this folder, named according to either the URL or content.    

## Datasets used

* act_2019_ca.csv: 2019 ACT Scores in California by School 
* sat_2019_ca.csv: 2019 SAT Scores in California by School 

They are from the California Department of Education, and contain information about scores for the ACT and SAT for all the schools in the State of California. There is also further breakdown according to the subcategories of the respective assessments. They are also tagged by the district and county they belong to. In addition, there are also rows for aggregated district, county and state-level data.

# Data Dictionary

The Data Dictionary is as follows:

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**cds_code**|object|ACT/SAT|County-District-School (CDS) Code. A unique identifier for a school. The first two digits are the county code, the next five digits are the school district code, and the remaining six to seven digits are the school code.|
|**s_name**|object|ACT/SAT|School Name. Only schools with 15 or more students taking the test are included in this dataset.|
|**d_name**|object|ACT/SAT|School District Name.|
|**c_name**|object|ACT/SAT|County Name.|
|**enroll_12**|int|ACT/SAT|Grade 12 Enrollment for the school.|
|**act_num_tst_takr**|int|ACT|Number of Grade 12 ACT test takers in the school.|
|**act_avg_scr_read**|int|ACT|Average ACT Reading Score of Grade 12 ACT test takers in the school. The score ranges from 1 to 36.|
|**act_avg_scr_eng**|int|ACT|Average ACT English Score of Grade 12 ACT test takers in the school.. The score ranges from 1 to 36.|
|**act_avg_scr_math**|int|ACT|Average ACT Math Score of Grade 12 ACT test takers in the school. The score ranges from 1 to 36.|
|**act_avg_scr_sci**|int|ACT|Average ACT Science Score of Grade 12 ACT test takers in the school. The score ranges from 1 to 36.|
|**act_num_ge_21**|int|ACT|Number of Grade 12 ACT test takers in the school whose ACT Composite Scores are 21 or above.|
|**act_pct_ge_21**|float|ACT|Percentage of Grade 12 ACT test takers in the school whose ACT Composite Scores are 21 or above (e.g. 64.15 indicates 64.15%).|
|**sat_num_tst_takr**|int|SAT|Number of Grade 12 SAT test takers in the school.|
|**sat_num_erw_benchmark**|int|SAT|Number of Grade 12 SAT test takers in the school who met the SAT Evidence-Based Reading & Writing (ERW) benchmark by the College Board for Grade 12.|
|**sat_pct_erw_benchmark**|float|SAT|Percentage of Grade 12 SAT test takers in the school who met or exceeded the SAT Evidence-Based Reading & Writing (ERW) benchmark by the College Board for Grade 12 (e.g. 80.00 indicates 80%).|
|**sat_num_math_benchmark**|int|SAT|Number of Grade 12 SAT test takers in the school who met or exceeded the SAT Math benchmark by the College Board for Grade 12.|
|**sat_pct_math_benchmark**|float|SAT|Percentage of Grade 12 SAT test takers in the school who met or exceeded the SAT Math test benchmark by the College Board for Grade 12 (e.g. 51.88 indicates 51.88%).|
|**sat_tot_num_both_benchmark**|int|SAT|Total number of Grade 12 SAT test takers in the school who met the benchmark of both the SAT Evidence-Based Reading & Writing (ERW) and Math tests by the College Board for Grade 12.|
|**sat_pct_both_benchmark**|float|SAT|Percentage of Grade 12 SAT test takers in the school who met the benchmark of both the SAT Evidence-Based Reading & Writing (ERW) and Math tests by the College Board for Grade 12 (e.g. 50.00 indicates 50.00%).|

# Summary of Analyses

The dataset provided from the source only contained data on schools with 15 or more students taking the ACT or the SAT. Based on the problem statement, the data was cleaned and taken only where schools had sent students for both the ACT and the SAT. The intent was to find the lowest-performing schools on both the ACT and the SAT. 

Two metrics were used to evaluate the performance of schools; one for each test.   
* The metric for the ACT was: the percentage of Grade 12 ACT test takers in the school whose ACT Composite Scores were 21 or above. 
* The metric for the SAT was: the percentage of Grade 12 SAT test takers in the school who met the benchmark of both the SAT Evidence-Based Reading & Writing (ERW) and Math tests by the College Board for Grade 12. 

The 25th percentile of these metrics were taken, and the schools performing below this value for both the ACT metric and the SAT metric were considered to be lower-performing schools. Lists of the 10 worst-performing schools for the ACT and SAT were obtained respectively from this subset, and for both the lists, schools from the **Los Angeles** county made up 7/10 of the list. 6 of the schools were on both lists. 

**Los Angeles** was the county with the highest number of students enrolled in both the tests.

When this subset was derived, summary statistics, correlation and exploratory data analyses such as plots were done on the subset, and also to compare the subset with the full data. 

For correlations, it was found that there was a low to almost no correlation for the number of test takers for the ACT or SAT in a school with test performance. 

The two metrics of interest were very strongly correlated, with an r value of 0.9. This indicates schools usually performed equally well or equally worse on both tests.

In order to check if the high representation of **Los Angeles** schools in the lowest-performing group was based on the the original and underlying patterns of the population, a comparision was done between the subset and the full set of the data. A conclusion was derived. 

# Conclusion and Recommendations

The Los Angeles county made up nearly half of the schools in the lowest 25% in terms of performance for both the ACT and the ACT. In comparison to the full working dataset cleaned for the project, this proportion was almost twice the proportion of the Los Angeles county in the full dataset. **Hence, it is recommended that the company starts with contacting schools from the Los Angeles county within this subset.** The geographical proximity could streamline operations. There are 89 schools, which could be explored according to their ranking on the list sorted in ascending order by performance. 

Based on analyses of the performance of the subset on the individual test components of the ACT and SAT, **for the ACT, it is recommended to emphasise our educational capabilities for the English test of the ACT** when pitching to potential clients. The English scores are the lowest in general out of the four components, but in the subset, the difference between English and the rest is more pronouced. 

**For the SAT, it is is recommended to emphasise on the Math test**, since the performance is the lowest. However, performance differences between sections were similar when compared to the full data, i.e. the schools performed poorest on math in general as a whole. It can be noted, however, that the Math section appears to be the limiting factor to one meeting both benchmarks on the SAT. 

There are twice the number of SAT test-takers as compared to ACT test-takers in general. Hence, we would have to prepare to invest more resources in the SAT workshops. 

In conclusion, there is thus a clearer and actionable direction on where to start when approaching schools in California to offer our educational services. Future possible directions of this research would be to 1) integrate available data for Grade 11 SAT students in the analysis, 2) explore district-level patterns and 3) conduct geospatial visualisations on the location of lower-performing schools to identify any trends. 
