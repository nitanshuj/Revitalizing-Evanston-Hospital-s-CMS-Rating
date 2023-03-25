# Revitalizing Evanston Hospital's CMS Rating: Innovative Solutions and Recommendations

------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------

This Capstone Project was a part of my Post Graduate Diploma in Data Science from Upgrad & IIIT-Bangalore. <br>
They provided me with the problem statement.

The datasets was taken from the CMS official website - 
https://downloads.cms.gov/medicare/HospitalCompare/2016/October/Hospital_Revised_FlatFiles_20161110.zip

A video of the presentation made by me on the Capstone Project is also present at the following link - 
https://drive.google.com/file/d/1i58IJKcW5N2AQqJTwdxViwfwh2uusNGq/view?usp=sharing

------------------------------------------------------------------------------------------

## Business Understanding
------------------------------------------------------------------------------------------

The Centers for Medicare & Medicaid Services (CMS), a federal agency based in the US, is responsible for administering the country’s major healthcare programs, including Medicare and Medicaid. CMS collects, analyses the data and produces research reports. It then works to eliminate the instances of fraud and abuse within the healthcare system. The agency aims to provide a healthcare system with better care, access to coverage and improved health services to the citizens. CMS also aims to reduce the overall health costs such as hospital expenses and insurance premiums for the citizens.

The CMS rates hospitals in the US on a scale of 1-5, with the objective of making it easier for patients and consumers to compare the quality of services offered by various hospitals.

The ratings directly influence the consumers’ choice of hospitals and may significantly impact hospitals' revenues. Thus, it is extremely important for hospitals to identify the key factors that affect their ratings so that they can work on improving them.

------------------------------------------------------------------------------------------

## Objective
------------------------------------------------------------------------------------------

Evanston Hospital is a comprehensive acute-care facility in Illinois, US. The hospital offers a wide range of services and surgical specialties, in addition to having high-end lab capabilities. 

Despite spending a considerable number of resources on improving its services, the hospital’s CMS rating has remained at 3 for the past 5 years, and this has led to a steady decline in revenue for the hospital.
 
For hospitals like Evanston, these ratings directly influence the choice made by consumers who are looking for a healthcare provider and would, therefore, have a significant impact on the hospitals’ revenues. As a consulting company hired by Evanston, our task is to identify possible root causes for the hospital getting such an average rating and recommend measures to mitigate this problem.

------------------------------------------------------------------------------------------

## Solving Methdology:
------------------------------------------------------------------------------------------

### Task 1 - Root Cause Analysis (Structured Problem Solving).

`Given`:<br>
After a conversation with Evanston Hospital regarding the reasons why its profits were not increasing despite investing for improving its services. The following facts were found out.<br>
- It was found that the Evanston Hospital’s net profit has had a steady decline of around 7% for the last 6 quarters.
- The team mentioned that the number of customers and insurance companies opting for the hospital's services had declined by around 5% every year for the last 5 years. 
- The overall number of customers opting for private healthcare had also increased in that region, leading the team at Evanston to believe that a lot of them prefer other hospitals in the city as their healthcare providers.
- The hospital had conducted a survey 10 months back to identify the reasons for this drop in the number of customers and identified that because of their average CMS rating (which was 3 at that time) most people, as well as insurance providers, are preferring the other better-rated hospitals.
- To increase the rating, the hospital’s upper management decided to invest in several new types of equipment, a highly trained staff, and even set up a new lab for thorough testing of high-risk obstetrics and also a state-of-the-art Infant Special Care Unit for safe birthing. Despite these changes, the hospital's rating didn't improve.
- Upon further questioning, it was revealed that the management team at Evanston was actually unaware of which services were affecting its rating the most and the decision for which areas to invest upon was taken based on guesswork and internal discussion only. 

Here I proceeded with the root cause analysis using the Issue Tree Framework - <br>
The Tree is shown in the figure below. <br>


![Profits_havent_increased_for_Evanston_Hospital](https://user-images.githubusercontent.com/30548563/147801868-e033af3d-1d2e-45c1-a776-d530219f05fd.png)

Some of the high priority questions that arise from Issue Tree Framework that Evanston Hospital has to answer are:
- 1) Are you aware of the measures on which the ratings are generated?
- 2) Are you aware on which measures your hospital lack?
- 3) Are the doctors of your hospital polite and professional towards their patients?
- 4) Do doctors follow the correct treatment protocols?
- 5) Do you utilize your resources well?


### Task 2 - Selection of Datasets to analyze.

Before proceeding with the analysis, we need to get the data. The dataset are present in the CMS official website - 
https://downloads.cms.gov/medicare/HospitalCompare/2016/October/Hospital_Revised_FlatFiles_20161110.zip

There were around 50 datasets present in the CMS. For our analysis we need to choose the datasets that contains all the important measures that impacts the CMS ratings. 
To decide which datasets are important for our analysis, we make use of two main documents -
- 1) Overall Hospital Quality Star Ratings on Hospital Compare Methodology Report (v2.0). 
- 2) Overall Hospital Quality Star Rating on Hospital Compare: January 2020 Updates and Specifications Report (Appendix C). 
`Both These files are present in "Important Documents" folder of the project. They have been downloaded from the CMS website` <br>

It was discovered that there were 51 measures divided into 7 groups, which contribute towards the calculation of the overall Star Rating by the CMS.

Hence the important datasets required for are analysis were - 
- 1) - Hospital General Information.csv
- 2) - Readmissions and Deaths - Hospital.csv
- 3) - Complications - Hospital.csv
- 4) - Timely and Effective Care - Hospital.csv
- 5) - Healthcare Associated Infections - Hospital.csv
- 6) - Outpatient Imaging Efficiency - Hospital.csv
- 7) - HCAHPS - Hospital.csv

### Task 3 - Data Analysis and Model Building
`Step 1: Dataset - "Hospital General Information"`
	- Reading & Exploring the Dataset
	- Performing EDA on the "Hospital General Information" dataset

`Step 2: Finding the various measure scores from various datasets`<br>
We will follow the following Modus Operandi for extracting the data regarding the measures
from the datasets .<br>
**1** - We will make the use of Pandas Pivot Table. The table will be of the form - <br>
      | Provider ID    |   Measure 1  | Measure 2  | .......... |   Measure N  |
      | -------------- | ------------ | ---------- | ---------- | ------------ |
      | Provider id 1  |   Score      |   Score    | .......... |  Score       |
      | Provider id 2  |   Score      |   Score    | .......... |  Score       |

**2** - Once the Pivot table is ready, we will select the required measures out of the total measures and make a final dataframe for that measure group.

**3** - Once this is done, we will then rename the measures by prefixing group name to the measure ID

**4 - The final step will be to merge this dataset to our main hosp_gen dataset.**

` We will follow the above 4 steps on all the above mentioned datasets, except the "Hospital General Information.csv".


`Step 3: Here we will merge all the above datasets to get our final dataset.`
	- Inspecting the final dataset.

`Step 4: Performing Exploratory Data Analysis on the final dataset`
	- NULL values treatment
	- Feature Engineering
	- Univariate and Bivariate Analysis

`Step 5: Preparing Data for Modelling`
	- Dummy Encoding
	- Check for Class Imbalance
	- Creating a Dataframe to store the Metrics
	- Separating the Target hospital from the Dataset

`Step 6: Model 1 - Logistic Regression`
	- Logistic Regression without Hyperparamer Tuning with Stratified K-Fold Cross Validation.
	- Logistic Regression with Hyperparamer Tuning with Stratified K-Fold Cross Validation.

`Step 7: Model 2 - Decision Tree Classifier`
	- Decision Tree Classifier with Hyperparameter tuning.

`Step 8: Model 3 - Random Forest`
	- Random Forest Classifier with Hyperparameter tuning.

`Step 9: K-Nearest Neighbor`
	- K-Nearest Neighbor with Hyperparameter tuning.

`Step 10: Results & Important Variable Selection`
For selecting the best model we will take into considerations the following two metrics. <br>
- 1) Accuracy - we can use this here, since we have taken care of the class imbalance using Cross validation technique.
- 2) Precision - since we want to know the True Positives only out of all the positives
Here we will give more weightage to the precision metric. 

We can make the use of **eli5** for selecting the best variables that will determine the model outputs.

--------------------------------------------------------------------------------

## Observations from the various plots in Univariate & Bivariate Analysis
-----------------------------------------------------------------------------------------
- We observed that median rating of the Hospitals are 3.5.
- Nearly all of the hospitals are rated between 2 & 5.
- Most of the Hospitals are Acute care type hospitals.
- Most of the Hospitals are owned by Private voluntary non-profits.
- Most of the Hospitals provide emergency services.
- Most of the Measures for all the hospitals are on a similar level as the national average.
- We observed that Physician Clinics and Hospitals are the most highly rated hospitals as compared to other hospitals. Also, we can see that Tribal Hospitals & State Government hospitals are very low rated.This can be due to the fact that these provides less facilities to the patient.
- We can observe here the the Availability of Emergency services are not impacting the Hospital Overall rating in any way.
- We observed that Critical Access hospitals are a little higher rated than Acute Care Hospitals.
- We observed that the for most of the measures, hospitals with a measure score above or similar to the national average have high overall ratings.
<br><br>
- Mortality Group - We can observe that higher the score for mortalty measures, lower the Overall rating.
- Readmission Group - We observe that a higher Readmission score leads to lower overall rating.
- Safety of Care Measures - We observe that a high rating corresponds to low Safety of Measure average score.
- Patient Experience - We see a postive proportion between Hospital rating and Patient Experience score.
- Effectiveness of Care - We cannot see any relation between Effectiveness of care score and overall rating.
- Timeliness of Care - We can see that a low Timeliness of Care measure average corresponds to low overall rating.
<br><br>
- There is not much pattern for Imaging scores vs Hospital scores. But we observe that regardless of the medical imaging scores, most of the hospitals are rated as 3 star.
- All of the hospitals show similar Mortality group scores with Government type hospitals showing a little higher scores.
- Readmission scores shows a similar trend as Mortality scores with Tribal hospitals with a little higher Readmission scores.
- We observed that Government hospitals show a little higher Safety of Care scores as compared to other hospital types. Physician clinics/hosputals shows the lowest safety of care scores.
- We see that the Physician clinics give the best Patient experience out of all the other hospitals.
- We see that all hospitals except Tribal hospitals shows a similar Effectiveness of Care Score, whereas Tribal hospitals shows a lower score.
- We see a high timeliness of care score for Government type of Hospitals. All the other hospital types show a lower score.
- We observed that Physican clinics are highly rated in terms of Outpatient Imaging.
<br><br>
- We observed for most of the hospitals that mortality score is above the national average for most of the cases, except Physician clinics, Local Government hospitals, State Government hospitals.
- We observed for most of the hospitals that their readmission scores is above the National average for most of the cases.
- We observed that for most of the hospitals, their Timeliness of care is similar or above the national average for most of the cases. Only the Government Federal hospitals have Timeliness of Care as below national average for most of the cases.
- We observed that for all of the hospitals, their Patient Experience score is above the national average for most of the cases.
- We observed that for all of the hospitals, their Safety of Care score is above the national average for most of the cases.
- We observed that for all of the hospitals, their Outpatient Imaging Efficiency score is above the national average for most of the cases, except for physician clinics and Tribal Hospitals.
<br><br>
** Heatmap Analysis **
- Most of the variables have a low correlation with each other.
- Only the measures in a single group seems to show a high correlation with each other.
- We will make the use of Recursive Feature Elimination to take care of all the correlation issues.


------------------------------------------------------------------------------------------

## Results and Conclusion
------------------------------------------------------------------------------------------

Model Performance Metrics: <br>

| S. No. | Model Name | Accuracy with Std. Dev. | Precision with Std. Dev. | Recall with Std. Dev. | F1-Score with Std. Dev. |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | Logistic Regression | 74.11 +/- (1.31) | 77.46 +/- (2.8) | 59.74 +/- (2.62) | 65.33 +/- (2.7) |
| 2 | Losgistic Regression with Hyperparameter Tuning | 74.58 +/- (1.36) | 79.13 +/- (3.62) | 63.65 +/- (3.77) | 68.91 +/- (3.53) |
| 3 | Decision Tree Classifier with Hyperparameter Tuning | 61.72 +/- (2.74) | 37.21 +/- (1.57) | 33.69 +/- (2.43)| 33.73 +/- (2.51) |
| 4 | Random Forest Classifier with Hyperparameter Tuning | 74.2 +/- (0.61) | 80.9 +/- (1.65) | 53.69 +/- (1.97) | 59.2 +/- (2.12)|
| 5 | K-Nearest Neighbor with Hyperparameter Tuning | 68.66 +/- (0.7) | 67.75 +/- (4.54) | 53.24 +/- (3.05) | 57.11 +/- (3.42) |

It was found out that Random Forest & Logistics Regrssion (OVR) both with hyperparameter tuning perfomed good as compared to other models. But here since we are giving more weightage to the precision metric, so we will select Random Forest as our best performing algorithm.


Using the Eli5 library and the random forest best model, some of the important features responsible for the rating system of CMS were found to be - 

| Weight | Feature |
| ------ | ------- |
| 0.1000 ± 0.0564 | Safetyofcare_PSI_90_SAFETY |
| 0.0622 ± 0.0339 | Mortality_MORT_30_PN |
| 0.0520 ± 0.0933 | PatientExperience_H_COMP_7 |
| 0.0452 ± 0.0286 | Mortality_MORT_30_HF |
| 0.0433 ± 0.0415 | Readmission national comparison_Below |
| 0.0416 ± 0.0317 | Readmissions_READM_30_COPD |
| 0.0386 ± 0.0754 | PatientExperience_H_COMP_1 |
| 0.0362 ± 0.0946 | Patient experience national comparison_Below |
| 0.0360 ± 0.0510 | Patient experience national comparison_Same |
| 0.0344 ± 0.0640 | PatientExperience_H_RECMND |


But, since we needed the features responsible for the low rating of Evanston Hospital. We again used the eli5 Library with the Random Forest Best Model to generat the following table.

| Weight | Feature |
| ------ | ------- |
|0.1000 ± 0.0564 | PatientExperience_H_CLEAN|
|0.0622 ± 0.0339 | Readmissions_READM_30_COPD|
|0.0520 ± 0.0933 | PatientExperience_H_HSP_RATING|
|0.0452 ± 0.0286 | Mortality_MORT_30_PN|
|0.0433 ± 0.0415 | Readmission national comparison_Below|
|0.0416 ± 0.0317 | Safetyofcare_HAI_2_SIR|
|0.0386 ± 0.0754 | PatientExperience_H_COMP_2|
|0.0362 ± 0.0946 | Patient experience national comparison_Below|
|0.0360 ± 0.0510 | Patient experience national comparison_Same|
|0.0344 ± 0.0640 | Effectivenessofcare_MORT_30_AMI|
|0.0339 ± 0.0234 | Mortality_MORT_30_HF|
|0.0327 ± 0.0702 | PatientExperience_H_QUIET_HSP|
|0.0297 ± 0.0444 | Safety of care national comparison_Below|
|0.0294 ± 0.0256 | Timelinessofcare_ED_2b|
|0.0281 ± 0.0572 | PatientExperience_H_COMP_5|

#### The top features that Evanston Hospital needs to focus on are - <br><br>
- 1) Patient Experience - Cleanliness of Environment 
- 2) Readmission - Chronic Obstructive Pulmonary Disease 30 days readmission rate
- 3) Patient Experience - Overall rating of the Hospital
- 4) Mortality - Pnemonia 30 days mortality rate
- 5) Readmission national comparison (Below national level)
- 5) Safety of Care - Catherer Associated Urinary tract infection 
- 6) Patient Experience - Doctor Communication
- 7) Patient Experience national comparison (below & same)
- 8) Mortality - Acute Myocardial Infarction (Heart attack) mortality rate 
- 9) Mortality - HEart Failure 30 days mortality rate
- 10) Patient Experience - Quietness of the Hospital

`**These top 10 features carry around 55% of the total weightage of rating.**`

------------------------------------------------------------------------------------------

## Business Insights
------------------------------------------------------------------------------------------

Looking at the analysis of the Evanston Hospital rating criteria, we come across the following 4 measure groups that severely impacts it's ratings.

The main measure group areas where Evanston Hospital needs to improve their services are - 

- **1 - Patient Experience**
- **2 - Readmission Rates / Procedures**
- **3 - Mortality Rates**
- **4 - Safety of Care**    


To be more specific, The Hospital can use the following suggestions

**Patient Experience** - <br><br>
Patient Experience is one of the most important factors that Evanston Hospital should work on improving. Their patient experience score is below the national average, which is a bad sign.<br>
The main areas where the Patient experience can be improved are - 
> - Maintaining the cleanliness and hygiene of the place of and its sourrounding areas, by following good cleaning protocols. This should be an initiative by the hospital.
> - Here the Doctor-Patient Communication is also poor. The doctors can be given some mandatory communications training, so that they could interact with a patient in a more polite and professional manner.
> - Overall Patient Experience Rating (past ratings) matters, so the hospital should look at all the areas where patient is directly interacting or is directly involved in. They should all be improved.
<br><br><br>

**Readmission** - <br><br>
Overall the Readmission score is at par with the national average, but there is still an area where the Hospital can work that is the 
> Readmission rate for Chronic Obstructive Pulmonary Disease 30 days which is higher. Hospital should check that a patient with this illness follows the best and proper recovery procedures.
<br><br><br>

**Mortality** - <br><br>
This is one of the prominent areas where the hospital is lacking. It is witnessing a high amount of mortality rates. The mortality rates are for the following health issues and diseases - 
> - Pnemonia 30 days mortality rate
> - Acute Myocardial Infarction (Heart attack) 30 days mortality rate
> - Heart Failure 30 days mortality rate


The hospital should personally assign a person/counsellor who can make sure that the person recovering from the above mentioned problem is following the best and proper recovery proccedures. A doctor should be always available on call if there is an emergency situation with any of the patients those who are recovering.
<br><br><br>

**Safety of Care**<br><br>
This is also one of the areas where the Hospital is performing poorly as compared the National standards. 

> One of the main areas is the complications of various illness that the patient endures. The most common and important one is the Catherer Associated Urinary tract infection. This generally happens to bed-ridden patients, for who a catherer is administered. The hospital staff should be responsible for cleanliness of the catherer instruments and devices, so that no infectious catherer is used on a patient. This is one of the most easiest the things that the Hospital can improve in.

------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------
