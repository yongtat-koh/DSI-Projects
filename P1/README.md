## Problem Statement
A) Participation rate of SAT is higher than ACT or vice versa

B) Relationship of SAT and ACT scores

|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|ACT/SAT|name of the state|
|act_2017_participation_percent|float|ACT|Based on the number of graduates in the state, the percentage who took *act* test.|
|act_2017_avg_english|float|ACT|Each row in this column is the average *english* act score for each state.|
|act_2017_avg_math|float|ACT|Each row in this column is the average *math* act score for each state.|
|act_2017_avg_reading |float|ACT|Each row in this column is the average *reading* act score for each state.|
|act_2017_avg_science|float|ACT|Each row in this column is the average *science* act score for each state.|
|act_2017_avg_composite|float|ACT|Each row in this column is the average *composite* act score for each state. *Composite* is the *average* of eng, math, reading, science|
|sat_2017_participation_percent|float|SAT|Based on the number of graduates in the state, the percentage who took *sat* test.|
|sat_2017_erw|int|SAT|Each row in this column is the average *Evidence-Based Reading and Writing* sat score for each state.|
|sat_2017_math|int|SAT|Each row in this column is the average *math* sat score for each state.|
|sat_2017_total|int|SAT|Each row in this column is the average *total* sat score for each state.|
|act_2018_participation_percent|float|ACT|Based on the number of graduates in the state, the percentage who took *act* test.|
|act_2018_avg_composite|float|ACT|Each row in this column is the average *composite* act score for each state. *Composite* is the *average* of eng, math, reading, science|
|act_2018_avg_english|float|ACT|Each row in this column is the average *english* act score for each state.|
|act_2018_avg_math|float|ACT|Each row in this column is the average *math* act score for each state.|
|act_2018_avg_reading |float|ACT|Each row in this column is the average *reading* act score for each state.|
|act_2018_avg_science|float|ACT|Each row in this column is the average *science* act score for each state.|
sat_2018_participation_percent|float|SAT|Based on the number of graduates in the state, the percentage who took *sat* test.|
|sat_2018_erw|int|SAT|Each row in this column is the average *Evidence-Based Reading and Writing* sat score for each state.|
|sat_2018_math|int|SAT|Each row in this column is the average *math* sat score for each state.|
|sat_2018_total|int|SAT|Each row in this column is the average *total* sat score for each state.|

#### 1) Import and cleaning of data
sat17,act17 and sat18,act18 data were imported into Python. Data was cleaned to make the datatypes consistent.

#### 2) Exploratory Data Analysis
Standard deviation was manually calculated and compared against numpy and pandas's describe function.
The manual calculations matched numpy and differs from pandass's a little.

#### 3) Data Visualization
A heatmap is used to visualize correlations between all numeric features. This gives a general overview.
The participation rates of SAT & ACT for 2017 & 2018 plotted in histograms.

Scatterplots were also done to examine if there is a relationship between the variables.
a. SAT is more difficult than ACT based on the trends seen.

b. Students' scores in 2017 has a positive correlation with scores in 2018. This suggests the students' performance are consistent in this 2 years.

Boxplots were done to look at the range of values in each columns, except for the 'state' column.
i. Students prefer to take ACT over SAT. Also, the mean participation rate of ACT is higher than that of SAT for both 2017 and 2018.

ii. Generally, students score better in ACT than SAT, hence students may prefer to take SAT over ACT. This is as reflected in the participation rates also.

#### 4) Descriptive and Inferential Statistics
The distribution of the population of means will be normally distributed after many re-sampling. From the tests, ff the sample size is 3 or more, with repeated sampling, the population of means will be normally distributed.
Correlation of variables does not imply causation. To examine and establish the relationship, linear regression can be used to describe the relationship.

#### 5) Conclusions and Recommendations
1. SAT is more difficult than ACT based on the trends seen.

2. Students' scores in 2017 has a positive correlation with scores in 2018. This suggests the students' performance are consistent in this 2 years.

3. Review the standard for SAT test and ACT test, if the difficulty matches the participation rates may even out.