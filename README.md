# Analysis of Data of Power Outages in the United States from 2000 - 2016

## Introduction
This dataset is a culmination of information on Power Outages aggregated by Purdue University
I will use this data to attempt to answer the following question: 
**Geographically, what causes longer power outages?** 
This question is aimed to figure out where power outages are longer, with the 
eventual aim to find out what causes longer power outages

This dataset originally has **1534** rows from 1534 different individual power outages, 
and **56** columns, namely: 
- 'OUTAGE.DURATION': the duration, in minutes of the power outage
- 'NERC.REGION' : the geographical region designated by the NERC (North American Electric Reliability Corporation)
- 'U.S._STATE' : the name of the U.S. State the outage occured
- 'CLIMATE.REGION' : the climate region the outage occured (e.g. West, Northeast, Central, etc.)
- 'CLIMATE.CATEGORY' : the climate category the outage occured (e.g. normal, cold, warm)
- 'CAUSE.CATEGORY' : the general cause of the outage (e.g. severe weather, intentional attack, etc.)
- 'CAUSE.CATEGORY.DETAIL' : the specific cause of the outage (e.g. heavy wind, thunderstorm, etc.)
- 'PCT_LAND' : the percentage of the state that the outage occured that is land
- 'CUSTOMERS.AFFECTED' : The number of customers affected by the outage



## Data Cleaning and Exploratory Data Analysis

After looking through the dataset, only one notable addition was made:
- Added 'DURATION_TIME': the duration, in time elapsed

The dataframe looks like the following :

|   OBS |   YEAR |   MONTH | U.S._STATE   | POSTAL.CODE   | NERC.REGION   | CLIMATE.REGION     |   ANOMALY.LEVEL | CLIMATE.CATEGORY   | OUTAGE.START.DATE   | OUTAGE.START.TIME   | OUTAGE.RESTORATION.DATE   | OUTAGE.RESTORATION.TIME   | CAUSE.CATEGORY     | CAUSE.CATEGORY.DETAIL   |   HURRICANE.NAMES |   OUTAGE.DURATION |   DEMAND.LOSS.MW |   CUSTOMERS.AFFECTED |   RES.PRICE |   COM.PRICE |   IND.PRICE |   TOTAL.PRICE |   RES.SALES |   COM.SALES |   IND.SALES |   TOTAL.SALES |   RES.PERCEN |   COM.PERCEN |   IND.PERCEN |   RES.CUSTOMERS |   COM.CUSTOMERS |   IND.CUSTOMERS |   TOTAL.CUSTOMERS |   RES.CUST.PCT |   COM.CUST.PCT |   IND.CUST.PCT |   PC.REALGSP.STATE |   PC.REALGSP.USA |   PC.REALGSP.REL |   PC.REALGSP.CHANGE |   UTIL.REALGSP |   TOTAL.REALGSP |   UTIL.CONTRI |   PI.UTIL.OFUSA |   POPULATION |   POPPCT_URBAN |   POPPCT_UC |   POPDEN_URBAN |   POPDEN_UC |   POPDEN_RURAL |   AREAPCT_URBAN |   AREAPCT_UC |   PCT_LAND |   PCT_WATER_TOT |   PCT_WATER_INLAND | OUTAGE.START        | OUTAGE.RESTORATION   | DURATION_TIME   |
|------:|-------:|--------:|:-------------|:--------------|:--------------|:-------------------|----------------:|:-------------------|:--------------------|:--------------------|:--------------------------|:--------------------------|:-------------------|:------------------------|------------------:|------------------:|-----------------:|---------------------:|------------:|------------:|------------:|--------------:|------------:|------------:|------------:|--------------:|-------------:|-------------:|-------------:|----------------:|----------------:|----------------:|------------------:|---------------:|---------------:|---------------:|-------------------:|-----------------:|-----------------:|--------------------:|---------------:|----------------:|--------------:|----------------:|-------------:|---------------:|------------:|---------------:|------------:|---------------:|----------------:|-------------:|-----------:|----------------:|-------------------:|:--------------------|:---------------------|:----------------|
|     1 |   2011 |       7 | Minnesota    | MN            | MRO           | East North Central |            -0.3 | normal             | 2011-07-01 00:00:00 | 17:00:00            | 2011-07-03 00:00:00       | 20:00:00                  | severe weather     | nan                     |               nan |              3060 |              nan |                70000 |       11.6  |        9.18 |        6.81 |          9.28 |     2332915 |     2114774 |     2113291 |       6562520 |      35.5491 |      32.225  |      32.2024 |     2.30874e+06 |          276286 |           10673 |       2.5957e+06  |        88.9448 |        10.644  |       0.411181 |              51268 |            47586 |          1.07738 |                 1.6 |           4802 |          274182 |       1.75139 |             2.2 |  5.34812e+06 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 | 2011-07-01 17:00:00 | 2011-07-03 20:00:00  | 2 days 03:00:00 |
|     2 |   2014 |       5 | Minnesota    | MN            | MRO           | East North Central |            -0.1 | normal             | 2014-05-11 00:00:00 | 18:38:00            | 2014-05-11 00:00:00       | 18:39:00                  | intentional attack | vandalism               |               nan |                 1 |              nan |                  nan |       12.12 |        9.71 |        6.49 |          9.28 |     1586986 |     1807756 |     1887927 |       5284231 |      30.0325 |      34.2104 |      35.7276 |     2.34586e+06 |          284978 |            9898 |       2.64074e+06 |        88.8335 |        10.7916 |       0.37482  |              53499 |            49091 |          1.08979 |                 1.9 |           5226 |          291955 |       1.79    |             2.2 |  5.45712e+06 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 | 2014-05-11 18:38:00 | 2014-05-11 18:39:00  | 0 days 00:01:00 |
|     3 |   2010 |      10 | Minnesota    | MN            | MRO           | East North Central |            -1.5 | cold               | 2010-10-26 00:00:00 | 20:00:00            | 2010-10-28 00:00:00       | 22:00:00                  | severe weather     | heavy wind              |               nan |              3000 |              nan |                70000 |       10.87 |        8.19 |        6.07 |          8.15 |     1467293 |     1801683 |     1951295 |       5222116 |      28.0977 |      34.501  |      37.366  |     2.30029e+06 |          276463 |           10150 |       2.58690e+06 |        88.9206 |        10.687  |       0.392361 |              50447 |            47287 |          1.06683 |                 2.7 |           4571 |          267895 |       1.70627 |             2.1 |  5.3109e+06  |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 | 2010-10-26 20:00:00 | 2010-10-28 22:00:00  | 2 days 02:00:00 |
|     4 |   2012 |       6 | Minnesota    | MN            | MRO           | East North Central |            -0.1 | normal             | 2012-06-19 00:00:00 | 04:30:00            | 2012-06-20 00:00:00       | 23:00:00                  | severe weather     | thunderstorm            |               nan |              2550 |              nan |                68200 |       11.79 |        9.25 |        6.71 |          9.19 |     1851519 |     1941174 |     1993026 |       5787064 |      31.9941 |      33.5433 |      34.4393 |     2.31734e+06 |          278466 |           11010 |       2.60681e+06 |        88.8954 |        10.6822 |       0.422355 |              51598 |            48156 |          1.07148 |                 0.6 |           5364 |          277627 |       1.93209 |             2.2 |  5.38044e+06 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 | 2012-06-19 04:30:00 | 2012-06-20 23:00:00  | 1 days 18:30:00 |
|     5 |   2015 |       7 | Minnesota    | MN            | MRO           | East North Central |             1.2 | warm               | 2015-07-18 00:00:00 | 02:00:00            | 2015-07-19 00:00:00       | 07:00:00                  | severe weather     | nan                     |               nan |              1740 |              250 |               250000 |       13.07 |       10.16 |        7.74 |         10.43 |     2028875 |     2161612 |     1777937 |       5970339 |      33.9826 |      36.2059 |      29.7795 |     2.37467e+06 |          289044 |            9812 |       2.67353e+06 |        88.8216 |        10.8113 |       0.367005 |              54431 |            49844 |          1.09203 |                 1.7 |           4873 |          292023 |       1.6687  |             2.2 |  5.48959e+06 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 | 2015-07-18 02:00:00 | 2015-07-19 07:00:00  | 1 days 05:00:00 |


### Data Analysis 

This next part is a basic analysis of the data, finding which columns and aggregations methods would be best to answer the question above.

<iframe src="assets/out_distribution.html" width=800 height=600 frameBorder=0></iframe>

*the distribution of the duration of power outages*

The main thing that stands out from the above graph is the skew. It heavily skews right, signaling that there are significant outliers in the dataset.
Further analysis shows that such outliers include a 75 day long outage in Wisconsin, and a 54 day long outage in Michigan. Outliers such as these deserve a case study of their own, but will not be given heavy weight in this analysis. For that reason, when comparing the duration of power outages, the median will be used.


<iframe src="assets/state_out.html" width=800 height=600 frameBorder=0></iframe>

*Relationship between U.S. State and Median Outage Duration*

This graph appears to show a relationship in the Median Power Outage per State and the State. Additionally, some of the states in the top spots, such as New York, New Jersey and West Virginia, all appear in the same region geographiclally. To get a better sense of the geographic relationship, I will look for a broader geographic region that shows a stronger correlation.



| CLIMATE.REGION     |   OUTAGE.DURATION |  
|:-------------------|------------------:|
| West North Central |              59.5 |
| Southwest          |              73   |
| Northwest          |             246.5 |
| West               |             274   |
| Northeast          |             868   |
| South              |             962   |
| Southeast          |            1061   |
| Central            |            1199   |
| East North Central |            3120   |

*Climate Region and Median Outage Duration*

| NERC.REGION   |   OUTAGE.DURATION |
|:--------------|------------------:|
| PR            |             174   |
| WECC          |             219.5 |
| FRCC, SERC    |             372   |
| NPCC          |             494   |
| HECO          |             543   |
| SERC          |             747   |
| TRE           |            1095   |
| SPP           |            1134   |
| MRO           |            1245.5 |
| HI            |            1367   |
| FRCC          |            1419   |
| RFC           |            1672   |
| ECAR          |            5475   |

*NERC Region and Median Outage Duration*

These charts show the Median Power Outage Duration for various regions, one by Climate, one by NERC region. These are both geographical distinctions that appear to show a relationship in Outage Duration. The NERC region appears to show a stronger correlation, and will be used for future analysis.

<iframe src="assets/NERC_out.html" width=800 height=600 frameBorder=0></iframe>

*NERC Region and Median Outage Duration - visualized*

This visualizes the data above, further confirming the assumed correlation. Most notably is the height of the ECAR region compared to the other regions, and that will be explored further.

## Assessment of Missingness

### NMAR Analysis

I believe there are a couple columns in this dataframe that has missingness that can be attributed to **NMAR** (Not Missing at Random). One of these columns is 'CUSTOMERS.AFFECTED'. This has the possiblity of being NMAR, as the values that are missing could be missing due to their inherently large numbers. This could be due to these numbers being too high to be recorded easily, and therefore instead be represented by a *null* value. There is information that would be helpful to better figure out the reason for its missingness. Examples of such information include: City Population Density or Number of Customer Complaints. If these columns were included in the dataset, then the missingess could be attributed to MAR instead, as they should illustrate statistically higher than normal values for missing values.

### Missingness Dependency

Now I am going to analyze the missingess that can be seen in the 'CAUSE.CATEGORY.DETAIL' column. This column contains missing values that appear to have some correlation to certain columns, and no correlation to others. For example:

<iframe src="assets/Detail_bar.html" width=800 height=600 frameBorder=0></iframe>

*Distribution of Cause Category based on the missigness of Cause Category Detail*

Here we can see that the distributions of the Cause Category appear to be different, depending on whether the value in 'Cause Category Detail' was missing or not. To investigate this missingness further, I performed a permuation test, assessing the *TVD* (Total Variation Distance) between the observed categories, and 10,000 randomized examples. The results were the following:

<iframe src="assets/TVD_cause.html" width=800 height=600 frameBorder=0></iframe>

*Distribution of TVDs based on randomized Cause Categories. NOTE: Black bar represents the observed TVD*

This resulted in a p-value of 0, which leads us to reject the null hypothesis that: *"the distribution of Cause Category is the same when Cause Category Detail is missing and when column Cause Category Detail is not missing."*, and conclude that the randomness is MAR (Missing at Random) in comparison to this specific column.

Next, I will look at the missingness of the Cause Category Detail in comparison to the percentage of land in the state the outage occured. The distributions of which are below.

<iframe src="assets/land_comp.html" width=800 height=600 frameBorder=0></iframe>

*Distribution of land percentage of the states where power outages occured based on the missingness of Cause Category Detail*

Looking at these distributions, they do not seem overly different. Additionally, most of the percentages are fairly high, with the exception of one group which upon further analysis is Michigan. To analyze the similarities and differences of these distributions, I performed a permutation test, assessing the absolute difference in means of 10,000 randomized examples, and comparing it to the this observed statistic. The results were the following:

<iframe src="assets/Diff_land.html" width=800 height=600 frameBorder=0></iframe>

*Distribution of Absolute Difference of Means based on randomized Land Percentages. NOTE: Black bar represents the observed test statistic

This resulted in a p-value of .1405, which leads us to fail to reject the null hypothesis that: *"the distribution of Land Percentages is the same when Cause Category Detail is missing and when column Cause Category Detail is not missing."*, and conclude that the randomness is MCAR (Missing Completely at Random) in comparison to this specific column. 

Despite the findings of the last test, the overall missingness of the 'Cause Category Detail' column is **MAR**, as it depends on at least one column (Cause Category). 

## Hypothesis Testing

### Question

Which of the major NERC regions is prone to the longer power outages?

- In this case, a *'major'* NERC region is defined as one that has over 1% of the power outages in the dataset

After filtering out the 'not major' NERC regions, the median outage length (in minutes) is defined as the following:


| NERC.REGION   |   OUTAGE.DURATION |
|:--------------|------------------:|
| ECAR          |            5475   |
| RFC           |            1672   |
| FRCC          |            1419   |
| MRO           |            1245.5 |
| SPP           |            1134   |
| TRE           |            1095   |
| SERC          |             747   |
| NPCC          |             494   |
| WECC          |             219.5 |

- We can see that the ECAR region has the highest median power outage duration, at 5475 minutes, with which I will formulate my hypotheses

### Null Hypothesis

NERC Region and Power Outage Duration are not related - The ECAR Region's high median is due to chance alone

### Alternative Hypothesis

Power Outage Duration ARE related - The ECAR Region's higher median is not due to chance alone

### Method

For this hypothesis test, I used the median duration of the NERC region as the test statistic, and a significance level of 0.1. I took *n* random samples from the dataset, where *n* is the number of outages in the ECAR region. I then computed the median, and compared it to the observed median. I repeated this method 100,000 times, and stored it in the following graph:

<iframe src="assets/hyp_test_data.html" width=800 height=600 frameBorder=0></iframe>

*Distribution of ECAR Medians from 100,000 simulations. NOTE: Black bar represents the observed ECAR Median*

This resulted in a p-value of 0, which leads us to reject the null hypothesis. This suggests correlation between NERC Region and Power Outages, due to the significantly improbable median in the ECAR region. This does not confirm causation though, as this is not a randomized controlled trial. 

