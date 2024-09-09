This file contains these sections

Introduction

Objectives

This analysis is expected to determine: 

1.1.1 Which aircraft are the lowest risk for the company to start this new business endeavour. 

1.1.2 I must translate my findings into actionable insights that the head of the new aviation division can use to help decide which aircraft to purchase.


Overview

For this project, I used CRISP - DM methodology to perform data cleaning, imputation, analysis, and visualization and generate insights for the business stakeholder.


Business Understanding

The company is expanding in to new industries to diversify its portfolio. Specifically, it is interested in purchasing and operating airplanes for commercial and private enterprises, but do not know anything about the potential risks of aircraft. 


Source of data
I have sourced my data from the dataset link https://www.kaggle.com/datasets/khsamaha/aviation-accident-database-synopses, from the National Transportation Safety Board that includes aviation accident data from 1962 to 2023 about civil aviation accidents and selected incidents in the United States and international waters.


Links to presentation
C:\Users\HP\Desktop\Assessment\Project 1\AviationData

Link to Tableau dashboard
https://public.tableau.com/app/profile/gilbert.cheruiyot/viz/Project_Tableau_Final_GK_9_09_09_1/Top_10_Model_Per_Total_Uninjured?publish=yes


Data Understanding and Analysis

The first 5 rows of the AviationData assigned to df

Event.Id	Investigation.Type	Accident.Number	Event.Date	Location	Country	Latitude	Longitude	Airport.Code	Airport.Name	...	Purpose.of.flight	Air.carrier	Total.Fatal.Injuries	Total.Serious.Injuries	Total.Minor.Injuries	Total.Uninjured	Weather.Condition	Broad.phase.of.flight	Report.Status	Publication.Date
0	20001218X45444	Accident	SEA87LA080	1948-10-24	MOOSE CREEK, ID	United States	NaN	NaN	NaN	NaN	...	Personal	NaN	2.0	0.0	0.0	0.0	UNK	Cruise	Probable Cause	NaN
1	20001218X45447	Accident	LAX94LA336	1962-07-19	BRIDGEPORT, CA	United States	NaN	NaN	NaN	NaN	...	Personal	NaN	4.0	0.0	0.0	0.0	UNK	Unknown	Probable Cause	19-09-1996
2	20061025X01555	Accident	NYC07LA005	1974-08-30	Saltville, VA	United States	36.922223	-81.878056	NaN	NaN	...	Personal	NaN	3.0	NaN	NaN	NaN	IMC	Cruise	Probable Cause	26-02-2007
3	20001218X45448	Accident	LAX96LA321	1977-06-19	EUREKA, CA	United States	NaN	NaN	NaN	NaN	...	Personal	NaN	2.0	0.0	0.0	0.0	IMC	Cruise	Probable Cause	12-09-2000
4	20041105X01764	Accident	CHI79FA064	1979-08-02	Canton, OH	United States	NaN	NaN	NaN	NaN	...	Personal	NaN	1.0	2.0	NaN	0.0	VMC	Approach	Probable Cause	16-04-1980


the first 5 rows of the US states data assigned to df1


US_State	Abbreviation
0	Alabama	AL
1	Alaska	AK
2	Arizona	AZ
3	Arkansas	AR
4	California	CA



information about the data set
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 88889 entries, 0 to 88888
Data columns (total 31 columns):
 #   Column                  Non-Null Count  Dtype  
---  ------                  --------------  -----  
 0   Event.Id                88889 non-null  object 
 1   Investigation.Type      88889 non-null  object 
 2   Accident.Number         88889 non-null  object 
 3   Event.Date              88889 non-null  object 
 4   Location                88837 non-null  object 
 5   Country                 88663 non-null  object 
 6   Latitude                34382 non-null  object 
 7   Longitude               34373 non-null  object 
 8   Airport.Code            50249 non-null  object 
 9   Airport.Name            52790 non-null  object 
 10  Injury.Severity         87889 non-null  object 
 11  Aircraft.damage         85695 non-null  object 
 12  Aircraft.Category       32287 non-null  object 
 13  Registration.Number     87572 non-null  object 
 14  Make                    88826 non-null  object 
 15  Model                   88797 non-null  object 
 16  Amateur.Built           88787 non-null  object 
 17  Number.of.Engines       82805 non-null  float64
 18  Engine.Type             81812 non-null  object 
 19  FAR.Description         32023 non-null  object 
...
 29  Report.Status           82508 non-null  object 
 30  Publication.Date        75118 non-null  object 
dtypes: float64(5), object(26)
memory usage: 21.0+ MB


Description of data, link C:\Users\HP\Desktop\Assessment\Project 1\AviationData\Graph_images\Descriptive_analytics_Aviation_Accidents.png

	NUMBER.OF.ENGINES	TOTAL.FATAL.INJURIES	TOTAL.SERIOUS.INJURIES	TOTAL.MINOR.INJURIES	TOTAL.UNINJURED
count	88889.000000	88889.000000	88889.000000	88889.000000	88889.000000
mean	1.136552	0.693022	0.240491	0.309127	5.303795
std	0.432545	5.123423	1.434614	2.083715	26.969508
min	0.000000	0.000000	0.000000	0.000000	0.000000
25%	1.000000	0.000000	0.000000	0.000000	0.000000
50%	1.000000	0.000000	0.000000	0.000000	1.000000
75%	1.000000	1.000000	0.000000	0.000000	2.000000
max	8.000000	349.000000	161.000000	380.000000	699.000000

Overview of the descriptive statistics on 'NUMBER.OF.ENGINES',	'TOTAL.FATAL.INJURIES',	'TOTAL.SERIOUS.INJURIES',	'TOTAL.MINOR.INJURIES' and	'TOTAL.UNINJURED' columns
- All the analysed columns specified above have 88,889 non-null values

NUMBER.OF.ENGINES
- Most aircrafts have one engine, while the aircraft with the highest number of engines was eight. 
- The variation in the number engines existed at 0.4325.

TOTAL.FATAL.INJURIES
- Most aircrafts accidents had zero fatal injuries with average less than 1.
- The highest fatal injuries was 349. 
- The variability in total fatal injuries was higher at 5.1234.

TOTAL.SERIOUS.INJURIES
- Most aircrafts accidents had zero serious injuries as the average neared zero.
- The highest serious injuries was 161.
- The variation in the total serious injuries existed at 1.4346. 

TOTAL.MINOR.INJURIES
- Most aircrafts accidents had zero minor injuries as the average neared zero.
- The highest minor injuries was 380. 
- There was variability of the number of minor injuries among aircrafts at standard deviation of 2.0837.

TOTAL.UNINJURED
- Most aircrafts accidents had uninjured case averaging around 5.
- The highest uninjured was 699. 
- The variability in total uninjured was high at 26.9695. 


Three visualizations (the same visualizations presented in the slides and notebook)

1. Number of Aircraft Engines vs Total Uninjured During Aviation_Accidents
C:\Users\HP\Desktop\Assessment\Project 1\AviationData\Graph_images\Number_of_Aircraft_Engines_vs_Total_Uninjured_During_Aviation_Accidents.png

2. Total Uninjured Passengers During Aviation Accidents per Engine_Type
C:\Users\HP\Desktop\Assessment\Project 1\AviationData\Graph_images\Total_Uninjured_Passengers_During_Aviation_Accidents_per_Engine_Type.png

3. Total Uninjured Passengers per Aircraft Make During Aviation Accidents
C:\Users\HP\Desktop\Assessment\Project 1\AviationData\Graph_images\Total_Uninjured_Passengers_per_Aircraft_Make_During_Aviation_Accidents.png



Conclusion

Summary of Findings:
 - The manufacturers of aircraft with the highest percentage of uninjured cases during accidents were Boeing, McDonnell Douglas, and Cessna. Boeing led the industry in the number of people who were not wounded during the accident incidents with 209,195, followed far behind by MCDonnel Douglas with 45,292. Cessna ranked third during the review period with 42,522 uninjured. 

- According to an investigation of the Aviation Accident Database & Synopses, up to 2023 dataset, this is the case, the top three aircraft manufacturers in terms of fatal accident injuries are Cessna, Boeing, and Piper, with 13,044, 9,223, and 8,364, respectively. 

- The engine type that had the greatest number of fatalities and uninjuries was reciprocating. 

- The aircrafts build by amateurs were safer with less fatal injuries compared to aircrafts build by non-amateurs

- The most often implicated aircraft models in deadly accidents include the 737, 737-200, and 152 types. 

- The models with the greatest number of undamaged cases during the review period were the 737, 777, and DC-10-10. The 737 model recorded a significant number of uninjured incidents—25,461—while the 777 and DC-10-10 models reported 9,439 and 6,860 uninjured occurrences, respectively. 

- The engine types with the highest uninjired values were Turbo Fan, Reciprocating, and Turbo Jet, with respective values of 211,368, 201,222, and 34,247. 

- There were no fatal injuries in aircraft with six or eight engines between October 1948 and December 2022. 

- Two-engine aircraft saw the most number of unharmed, totalling 198,945; one-engine aircraft came in second, with 176,367 uninjured.


Relevant recommendation

- The business to think about buying aircrafts of Boeing and MCDonnell Douglas make, considering the large proportion of people who were  reported of not getting hurt during the accidents between 1948 and 2023, experienced  by the two makes of aircraft. 
 
- Turbo fan engine type had the highest number of uninjured, making it safe. 

- The aircraft with two engines proved to be the safest, with the maximum number of uninjured—198,945—while the aircraft with one engine came in second with 176,367 uninjured. The corporation should purchase one of these aircrafts. 

- The aircrafts build by amateurs are a good considerations to buy as they were safer with less fatal injuries compared to aircrafts build by non-amateurs.


