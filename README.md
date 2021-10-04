**Examining Local Relationships between Age and Underlying Conditions on COVID-19 Mortality**


Data and Computational Steps

Prepared by: Naomi W. Lazarus, PhD

August 20th, 2021
 

**A. Introduction**

A county-level assessment of COVID-19 in relation to age demographics and comorbidities is carried out to provide context to the emerging hotspots of the virus during the early stages of the pandemic.  The two peak periods under investigation were 03/01/20 - 04/30/20 and 06/01/20 - 07/31/20.  The spatial relationships between coronavirus, age, and comorbidities is examined using geographically weighted regression (GWR).  COVID-19 incidence rate and death-case ratio function as the dependent variables. The independent variables include percent population in age cohorts 50 – 74 and above 75, heart disease mortality, diabetes, and obesity.  Data and methodological challenges in defining the GWR model had to be addressed in the interests of reproducibility and transparency.

**B.  Data Sources**


Variable Definition	Source
 
COVID-19 case and death counts	USAFacts.org
https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/ 

Percent population aged 50 - 74	American Community Survey 2018 5-year estimates
data.census.gov

Percent population aged 75 and above	--do--

Percent population diagnosed with diabetes	Centers for Disease Control and Prevention
https://gis.cdc.gov/grasp/diabetes/DiabetesAtlas.html#

Mortality rate – number of deaths per 100,000 of population	Centers for Disease Control and Prevention
https://wonder.cdc.gov/

Percent adult population with diagnosed obesity	Centers for Disease Control and Prevention
https://gis.cdc.gov/grasp/diabetes/DiabetesAtlas.html#


**C.  Dependent Variables**

Death-case ratios during peak period 1  (03/01/20 to 04/30/20)
Death-case ratios during peak period 2  (06/01/20 to 07/31/20)

Calculation of Death-Case ratio:

New covid deaths during the first peak – 03/01/20 to 04/30/20 was obtained by subtracting value in 03/01/20 from 04/30/20.  Use death-case ratio formula to calculate this indicator. 

New covid deaths during the second peak – 06/01/20 to 07/31/20 was obtained by subtracting value in 06/01/20 from 07/31/20. Use death-case ratio formula to calculate this indicator. 

Death to Case Ratio = 
(Number of New Deaths during a specified time period)/(Number of New Cases during that same time period)  x 100

Log Transformation:
Dependent variables were transformed (Log10) to address skewness.  Can be done on Excel or SPSS.

**D.  Datasets**

Counties with no recorded coronavirus cases or deaths during the peak periods were removed. 
Counties with death counts below 10 due to heart disease were removed. 
Counties that recorded zero or unreliable numbers related to the other independent variables were removed.  
Four datasets were compiled.  All datasets contained the same independent variables.  Dependent variable was unique to each dataset.  Size of dataset varied after data clean-up was completed. 


Peak Period	    Dependent Variable	  Number of Observations

Peak 1: 03/01/20 - 04/30/20	Death-Case Ratio	N = 1,445

Peak 2: 06/01/20 - 07/31/20	Death-Case Ratio	N = 1,964

**E.  File Descriptions**

Layer_DR1_1.shp: modified county-level shapefile of contiguous US - contains data for Death-Case Ratio for Peak 1 (03/01/20 - 04/30/20) and all age cohort and comorbidity variables.  Number of observations (counties): 1445

Layer_DR2_1.shp: modified county-level shapefile of contiguous US - contains data for Death-Case Ratio for Peak 2 (06/01/20 - 07/31/20) and all age cohort and comorbidity variables.  Number of observations (counties): 1964

DR1_table.csv:  CSV table containing Dependent Variable - Death-Case Ratio for Peak 1 (03/01/20 - 04/30/20) and all age cohort and comorbidity variables.  Number of observations (counties): 1445

DR2_table.csv: CSV table containing Dependent Variable - Death-Case Ratio for Peak 2 (06/01/20 - 07/31/20) and all age cohort and comorbidity variables.  Number of observations (counties): 1964


**F.  Variable Descriptions**

Dependent Variables:

       IR1_log  -  Log transformed covid-19 incidence rates for peak period 1 (03/01/20 - 04/30/20)
       IR2_log  -  Log transformed covid-19 incidence rates for peak period 2 (06/01/20 - 07/31/20)
	      DR1_log  -  Log transformed covid-19 death-case ratios for peak period 1 (03/01/20 - 04/30/20)
       DR2_log  -  Log transformed covid-19 death-case ratios for peak period 2 (06/01/20 - 07/31/20)

Predictors:

        PCT_50to74  - Percent population aged 50 - 74
        PCT_over75  - Percent population aged 75 and above
        DIAB_PCT  - Percent population diagnosed with diabetes
        CARDIO_MR  - Heart disease mortality rate – number of deaths per 100,000 of population
        OBESE_PCT  - Percent adult population with diagnosed obesity
Geography/Geometry:

        X  -  X coordinate of geographic centroid of spatial feature (county) in meters
        Y  -  Y coordinate of geographic centroid of spatial feature (county) in meters
Projection:

        USA Contiguous Equidistant Conic Projection
        Linear Unit: Meters
        
Other Variables - not directly referenced in the code sample or not included in the analysis

        CTY_FIPS; countyFIPS  -  County Fips code
        CountyName  -  County name
        State  -  State abbreviation
        population - population count by county
        NEW_DTH_PD1  -  number of new death counts from covid-19 during peak period 1 (03/01/20 - 04/30/20)
        NEW_DTH_PD2  -  number of new death counts from covid-19 during peak period 2 (06/01/20 - 07/31/20) 
        NEW_CASE_PD1 -  number of new case counts from covid-19 during peak period 1 (03/01/20 - 04/30/20)
        NEW_CASE_PD2 -  number of new case counts from covid-19 during peak period 2 (06/01/20 - 07/31/20)
        DR1  -  Death-Case ratio for peak period 1 (03/01/20 - 04/30/20)
        DR2  -  Death-Case ratio for peak period 2 (06/01/20 - 07/31/20)
        IR1 - Incidence rate for peak period 1 (03/01/20 - 04/30/20)
        IR2  -  Incidence rate for peak period 2 (06/01/20 - 07/31/20)
        PCT_0to19  -  Percent population aged 0 - 19
        PCT_20to34 -  Percent population aged 20 - 34
        PCT_35to49 - Percent population aged 35 - 49
        INTPTLAT - Latitudinal coordinate of geographic centroid of spatial feature in decimal degrees
        INTPTLON - Longitudinal coordinate of geographic centroid of spatial feature in decimal degrees
        Shape_Length - perimeter of polygon boundary of spatial feature (county) in meters
        Shape_Area - areal extent of polygon of spatial feature (county) in square meters

**G.  Software**

ArcGIS Pro 2.5

Jupyter Notebook

PySAL – access sample code and definitions
https://mgwr.readthedocs.io/en/latest/generated/mgwr.gwr.GWRResults.html#mgwr.gwr.GWRResults
 

**H.  OLS Regression**

Run OLS regression for each dataset with incidence rates and death-case ratios for each peak period as the dependent variable. 

Code sample:

![image](https://user-images.githubusercontent.com/73550457/135922625-8a8fd2e6-423b-46c9-8229-371bacacbeb6.png)


**I.   GWR – model specification**

Model Type: Continuous

Bandwidth:  Number of Neighbors

Weighting Scheme: Gaussian

Bandwidth:

The golden section search method was used to identify the appropriate number of neighbors for each of the datasets based on the lowest AIC value.

Code sample for testing suitable bandwidth:

![image](https://user-images.githubusercontent.com/73550457/135922777-e91ebe90-27fe-4815-a4c7-a6fb702cf132.png)

 
Bandwidths based on number of neighbors for each dataset provided below:

Peak Period	Dependent Variable	GWR Bandwidth (no. of neighbors)

Peak 1: 03/01/20 - 04/30/20	Death-Case Ratio	210

Peak 2: 06/01/20 - 07/31/20	Death-Case Ratio	137


Code sample for specifying the GWR model:

![image](https://user-images.githubusercontent.com/73550457/135922863-5b674529-8760-40e2-bbd4-22f195e88bfc.png)
 

**J.  Summary of OLS Regression Results**

Example using DR1_log as the dependent variable (dataset 1):

![image](https://user-images.githubusercontent.com/73550457/135923032-8c149f5c-a188-4ef0-98fb-ce2eb3aef6f7.png)

 
**K.  Summary of GWR Results**

Example using DR1_log as the dependent variable (dataset 1).

Code sample and results for model fit statistics:

![image](https://user-images.githubusercontent.com/73550457/135923138-73a4a683-160d-4902-87ec-6329c0b30a47.png)

 
Code sample and results for local b coefficients:

![image](https://user-images.githubusercontent.com/73550457/135923210-f86d91db-e4a8-4d6b-9f91-6fce5a57e622.png)

 
Standardized Residual Map:

![image](https://user-images.githubusercontent.com/73550457/135923301-35eaf8e2-c0cd-4e29-8119-a5eb638d362a.png)

 
Local R2 value map:

![image](https://user-images.githubusercontent.com/73550457/135923353-03665c98-a174-4dac-9b22-22cc532f831b.png)

 
**L.  Jupyter Notebooks**

For complete code sample and results using individual datasets, refer to the detailed notebooks.

Notebook 1: https://cybergisxhub.cigi.illinois.edu/notebook/geographically-weighted-regression-part-i-covid-19-incidence/

Notebook 2: https://cybergisxhub.cigi.illinois.edu/notebook/geographically-weighted-regression-part-ii-covid-19-mortality/


