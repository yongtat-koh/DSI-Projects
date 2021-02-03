# Project 1: SAT & ACT Analysis

## Problem Statement
We will look at the participation rates of ACT and SAT for each state in the United States. If the overall participation rates of the ACT is higher than SAT, we will try to find a possible cause and decide on future directions and plans to improve the participation rates of SAT. For states that have low participation rates for SAT, we will need to gather feedback from the schools why they are not administering the SAT.

## Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|ACT/SAT|name of the state|
|act2017_partrate|float|ACT|Based on the number of graduates in the state, the percentage who took **ACT test**.|
|act2017_english|float|ACT|The average **english** act score for each state. Score is from 1 to 36.|
|act2017_math|float|ACT|The average **math** act score for each state. Score is from 1 to 36.|
|act2017_reading |float|ACT|The average **reading** act score for each state. Score is from 1 to 36.|
|act2017_science|float|ACT|The average **science** act score for each state. Score is from 1 to 36.|
|act2017_composite|float|ACT|The average **composite** act score for each state. *Composite* is the *average* of eng, math, reading, science. Score is from 1 to 36.|
|sat2017_partrate|float|SAT|Based on the number of graduates in the state, the percentage who took **SAT test**.|
|sat2017_erw|int|SAT|The average **Evidence-Based Reading and Writing** sat score for each state. Score is from 400 to 800.|
|sat2017_math|int|SAT|The average **math** sat score for each state. Score is from 400 to 800.|
|sat2017_total|int|SAT|The average **total** sat score for each state. Score is from 800 to 1600.|
|act2018_partrate|float|ACT|Based on the number of graduates in the state, the percentage who took **ACT test**.|
|act2018_composite|float|ACT|The average **composite** act score for each state.**Composite** is the **average** of eng, math, reading, science. Score is from 1 to 36.|
|act2018_english|float|ACT|The average **english** act score for each state. Score is from 1 to 36.|
|act2018_math|float|ACT|The average **math** act score for each state. Score is from 1 to 36.|
|act2018_reading |float|ACT|The average **reading** act score for each state. Score is from 1 to 36.|
|act2018_science|float|ACT|The average **science** act score for each state. Score is from 1 to 36.|
sat2018_partrate|float|SAT|Based on the number of graduates in the state, the percentage who took **SAT test**.|
|sat2018_erw|int|SAT|The average **Evidence-Based Reading and Writing** sat score for each state. Score is from 400 to 800.|
|sat2018_math|int|SAT|The average **math** sat score for each state. Score is from 400 to 800.|
|sat2018_total|int|SAT|The average **total** sat score for each state. Score is from 800 to 1600.|

## Executive Summary

It is found that Iowa, Mississippi and North Dakota have the lowest participation rate for SAT in 2017 and 2018. The participation rate of ACT is higher than that of SAT in 2017 and 2018. In our dataset, for both SAT and ACT, when participation rate is low, the score is high. When participation rate is high, the score is low. This is likely due to States that have low SAT/ACT participation rates have the tendency or practice to send their best students to take SAT/ACT and have the highest scores.

## Conclusions and Recommendations

**Key findings:**
1. ACT participation rate is higher than SAT participation rate for 2017 and 2018.
2. For states with low SAT participation rate, the SAT score is higher.
3. When SAT participation rate increases, the SAT score drops. It is the same for ACT.

**Possible Reasons for lower overall ACT/SAT participation rates**
- It could be due to the schools having the practice of sending their best students to take the ACT/SAT.

- However, the overall participation rate of ACT is still higher than SAT. Schools will want their students to succeed in the exams so that they can enter university. This suggests the SAT is more difficult to score than ACT. Hence, more states send their better students to take SAT compared to ACT.

**Recommendation**
- College Board may wish to give sample test papers to universities to get feedback and improve their tests so that it matches the standard of ACT.

**For Iowa**
- College Board may want to approach arts college and emphasize on the benefits of SAT on how it can help them assess students using only the ERW portion of SAT.

**Additional Data required**
- College Board may wish to get the feedback from teachers and students from the schools. From there, further analysis can be done to look at the trend for the schools' sentiments towards SAT.