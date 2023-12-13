# PPOL5203_FinalProject
Final project for PPOL5203


# Climate Impact on Health in Varying Community Types
This repository aims to explore how climate risk impacts health outcomes in varying community types. Please read the following to learn more about reserach proposal, datasets used, how data was cleaned, methodologies utilized, and final results.

## Datasets

### Orig_Data

`2023_County_Health_Rankings_Data.xlsx`: Dataset from the University of Wisconsin Population Health Institute. The County Health Rankings measures the health of nearly all counties in the United States and includes demographic information, health metrics such as age-adjusted death rate, and social determinants of health. 

`NRIDataDictionary.csv`: FEMA's data dictionary for the `NRI_Table_Counties.csv` file. Describes each variable, its file type, and its version date

`NRI_HazardInfo.csv`: FEMA's description of each natural hazard accounted for in the `NRI_Table_Counties.csv` file and the years they have annual data on each natural hazard.

`NRI_Table_Counties.csv`: The FEMA National Risk Index (NRI) is a multifaceted score that considers a U.S. county's expected risk to 18 different types of natural hazards. Nearly all U.S. counties have an overall composite risk score (RISK_SCORE) and risk rating for all 18 natural hazards, plus the overall Expected Annual Loss, Social Vulnerability, and Community Resilience scores and ratings. The FEMA NRI dataset also provided these data points for each natural hazard. 

Not included is the NRI shape file used for the GIS models because the file size exceeded the GitHub limit

### Clean_Data

`NRI_county_health_data.csv`: dataset that joins together select columns from the `NRI_Table_Counties.csv` and `2023_County_Health_Rankings_Data.xlsx` based on the county unique identifier (county FIPS value) and new variables 'Community_Type", "Population_Density"...

`NRI_county_health_data_southeast.csv`: dataset that is a subset of the `NRI_county_health_data.csv` that only contains observations of the SE region of the United States (from Alabama, Florida, Georgia, Kentucky, Mississippi, North Carolina, South Carolina, Tennessee, West Virginia, and Virginia)

`NRI_county_health_data_predictions.csv`: dataset that includes the predicted outcomes for specified health metrics of each county in the United States. Columns indicate and predict f a county is above or below the national average in Life Expectancy, Age-Adjusted Death Rate, Average Number of Physically Unhealthy Days, and Average Number of Mentally Unhealthy Days.

`NRI_county_health_data_predictions_southeast.csv`: similar to `NRI_county_health_data_predictions` except the data is subsetted to only include the predictions of health metrics for counties in the southeast.



## Python_Code

`Data_Cleaning.ipynb`: file that contains the python code used to pull the select columns of interest from each original dataset and merge on the FIPS variable, create new variables that will be part of the analysis, and reorder the columns for ease of use. Creates and saves the files `NRI_county_health_data.csv` and `NRI_county_health_data_southeast.csv`

`GIS_Models.ipynb`: file that contains the python code to create GIS models that visualize the distribution of the FEMA risk scores and how they relate to the public health outcomes. 

`OLS_Models_National_Data.ipynb`: file that contains the python code to create OLS models based on `NRI_county_health_data.csv` to help better understand the relationship between the NRI composite risk score and 4 dependent health variables: Life Expectancy, Age-Adjusted Death Rate, Average Number of Physically Unhealthy Days, and Average Number of Mentally Unhealthy Days. 

`OLS_Models_SE_Data_only.ipynb`: Similar to `OLS_Models_AllData.ipynb` but contains all OLS models that are based on the `NRI_county_health_data_southeast.csv` dataset.

`OLS_Models_RiskScore_Breakdown.ipynb`: Contains OLS models that include the three components of the composite score as individual variables (Annual Economic Loss, Social Vulnerabilities, and Community Resilience) for both the National and Southeast datasets.

`Machine_Learning.ipynb`: file that contains the python code for exploring different machine learning models and creating the decision tree models that were used for predictions and analysis. Calculates the overall accuracy of each model. Predicts if counties are above or below the national average in Life Expectancy, Age-Adjusted Death Rate, Average Number of Physically Unhealthy Days, and Average Number of Mentally Unhealthy Days. 


## Final_Results

### Final_Paper_files

`final_paper.pdf`: Final Research Paper detailing motivation, research questions, data sources, data cleaning & wrangling, methods & analysis, results, and discussion on how climate risk impacts health outcomes in varying community types. Authors include Bridgette Sullivan, Holt Cochran, and Katharyn Loweth. 

### Final_Presentation files

`PPOL5203_Final_Presentation.pdf`: Final Presentation slide deck; presentation delivered December 5, 2023


### Figures

`gis_age_adjusted_death_rate_accuracy_southeast.jpg`: Image with GIS results for Age-Adjusted Death Rate machine learning accuracy. (Green = Correct, Yellow = Incorrect)

`gis_age_adjusted_death_rate_prediction_southeast.jpg`: Image with GIS results for Age-Adjusted Death Rate machine learning prediction. (Green = Below Average, Red = Above Average)

`gis_life_expectancy_accuracy_southeast.jpg`: Image with GIS results for Life Expectancy machine learning accuracy. (Green = Correct, Yellow = Incorrect)

`gis_life_expectancy_prediction_southeast.jpg`: Image with GIS results for Life Expectancy machine learning prediction. (Green = Above Average, Red = Below Average)

`gis_mental_health_accuracy_southeast.jpg`: Image with GIS results for Average Number of Mentally Unhealthy Days machine learning accuracy. (Green = Correct, Yellow = Incorrect)

`gis_mental_health_prediction_southeast.jpg`: Image with GIS results for Average Number of Mentally Unhealthy Days machine learning prediction. (Green = Below Average, Red = Above Average)

`gis_physical_health_accuracy_southeast.jpg`: Image with GIS results for Average Number of Physically Unhealthy Days machine learning accuracy. (Green = Correct, Yellow = Incorrect)

`gis_physical_health_prediction_southeast.jpg`: Image with GIS results for Average Number of Phyiscally Unhealthy Days machine learning prediction. (Green = Below Average, Red = Above Average)

`Mentally_Unhealthy_Days_Scatterplot_AllData.png`: Image with scatterplot showing the relationship between Risk Score and Average Number of Mentally Unhealthy Days at a national level.

`Mentally_Unhealthy_Days_Scatterplot_SE_Only.png`: Image with scatterplot showing the relationship between Risk Score and Average Number of Mentally Unhealthy Days at a Southeast region level.

`PPOL5203_RegressionSummaryTable.png`: Table with regression outputs from various OLS models using Health Outcomes as dependent variables.

`risk_score_calculation`: Image displaying risk score calculation from FEMA's website.

`SE_RiskScore_Density_Plot.png`: Image displaying a density plot of risk scores by community type in the southeast region.

`table_2_machine_learning_accuracy`: Table with overall accuracy percentages for each machine learning model and accuracy percentages by community type.
