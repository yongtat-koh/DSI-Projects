# Project 2 - Ames Housing Data and Kaggle Challenge

# Problem Statement

From the Ames Housing Dataset, the aim is to create a regression model that can predict the price of a house at sale based on the SalePrice and variables available. The model should have the RMSE (root mean squared error) score as close to 0 as possible. A small RMSE score implies that the model is able to predict the price of the house at sale accurately. The variables that will be selected to build the best regression model will be based on the Exploratory Data Analysis.

# Data Dictionary

|Feature Name|Dataset|Description|
|---|---|---|
|ID|ames| Unique ID number for each entry.
|PID|ames|Individual homes that can be referenced directly from the Ames City Assessor webpage.|
|MS SubClass|ames|Identifies the type of dwelling involved in the sale.|
|MS Zoning|ames|Identifies the general zoning classification of the sale.|
|Lot Frontage|ames|Linear feet of street connected to property.|
|Lot Area|ames|Lot size in square feet.|
|Street|ames|Type of road access to property.|
|Alley|ames|Type of alley access to property.|
|Lot Shape|ames|General shape of property.|
|Land Contour|ames|Flatness of the property.|
|Utilities|ames|Type of utilities available.|
|Lot Config|ames|Lot configuration.|
|Land Slope|ames|Slope of property.|
|Neighborhood|ames|Physical locations within Ames city limits.|
|Condition1|ames|Proximity to various conditions.|
|Condition2|ames|Proximity to various conditions (if more than one is present).|
|Bldg Type|ames|Type of dwelling.|
|House Style|ames|Style of dwelling.|
|Overall Qual|ames|Rates the overall material and finish of the house.|
|Overall Cond|ames|Rates the overall condition of the house.|
|Year Built|ames|Original construction date.|
|Year Remod/Add|ames|Identifies the general zoning classification of the sale.|
|Roof Style|ames|Type of roof.|
|Roof Matl|ames|Roof material.|
|Exterior 1st|ames|Exterior covering on house.|
|Exterior 2nd|ames|Exterior covering on house (if more than one material).|
|Mas Vnr Type|ames|Masonry veneer type.|
|Mas Vnr Area|ames|Masonry veneer area in square feet.|
|Exter Qual|ames|Evaluates the quality of the material on the exterior .|
|Exter Cond|ames|Evaluates the present condition of the material on the exterior.|
|Foundation|ames|Type of foundation.|
|Bsmt Qual|ames|Evaluates the height of the basement.|
|Bsmt Cond|ames|Evaluates the general condition of the basement.|
|Bsmt Exposure|ames|Refers to walkout or garden level walls.|
|Bsmt Fin Type1|ames|Rating of basement finished area.|
|Bsmt Fin SF1|ames|Type 1 finished square feet.|
|Bsmt Fin Type2|ames|Rating of basement finished area (if multiple types).|
|Bsmt Fin SF2|ames|Type 2 finished square feet.|
|Bsmt Unf SF|ames|Masonry veneer type.|
|Total Bsmt SF|ames|Total square feet of basement area.|
|Heating|ames|Type of heating.|
|Heating QC|ames|Heating quality and condition.|
|Central Air|ames|Central air conditioning.|
|Electrical|ames|Electrical system.|
|1st Flr SF|ames|First Floor square feet.|
|2nd Flr SF|ames|Second floor square feet.|
|Low Qual Fin SF|ames|Low quality finished square feet (all floors).|
|Gr Liv Area|ames|Above grade (ground) living area square feet.|
|Bsmt Full Bath|ames|Basement full bathrooms.|
|Bsmt Half Bath|ames|Basement half bathrooms.|
|Full Bath|ames|Full bathrooms above grade.|
|Half Bath|ames|Half baths above grade.|
|Bedroom|ames|Bedrooms above grade (does NOT include basement bedrooms).|
|Kitchen|ames|Kitchens above grade.|
|Kitchen Qual|ames|Kitchen quality.|
|Tot Rms Abv Grd|ames|Total rooms above grade (does not include bathrooms).|
|Functional|ames|Home functionality (Assume typical unless deductions are warranted).|
|Fireplaces|ames|Number of fireplaces.|
|Fireplace Qu|ames|Fireplace quality.|
|Garage Type|ames|Garage location.|
|Garage Yr Blt|ames|Year garage was built.|
|Garage Finish|ames|Interior finish of the garage.|
|Garage Cars|ames|Size of garage in car capacity.|
|Garage Area|ames|Size of garage in square feet.|
|Garage Qual|ames|Garage quality.|
|Garage Cond|ames|Garage condition.|
|Paved Drive|ames|Paved driveway.|
|Wood Deck SF|ames|Wood deck area in square feet.|
|Open Porch SF|ames|Open porch area in square feet.|
|Enclosed Porch|ames|Enclosed porch area in square feet.|
|3Ssn Porch|ames|Three season porch area in square feet.|
|Screen Porch|ames|Screen porch area in square feet.|
|Pool Area|ames|Pool area in square feet.|
|Pool QC|ames|Pool quality.|
|Fence|ames|Fence quality.|
|MiscFeature|ames|Miscellaneous feature not covered in other categories.|
|MiscVal|ames|$Value of miscellaneous feature.|
|Mo Sold|ames|Month Sold (MM).|
|Yr Sold|ames|Year Sold (YYYY).|
|SaleType|ames|Type of sale.|
|Sale Condition|ames|Condition of sale.|

# Summary of findings when checking Data:

#### Findings:

1) Null entries are checked. The percentage and number of null entries are found.

2) Possible explanation for null entries are in the glossary.

3) Data is checked for duplicates. There are no duplicates.

4) There are no negative values in dataset.

#### Glossary of Possible Explanation for columns that have > 10% empty cells.

Lot Frontage: If Nan, property is not connected to inear feet of street.

Alley: If Nan or NA, property has no alley access. This variable will be not considered to because it has 93% empty cells. 

Fireplace Qu: If Nan or NA, property has no fireplace.This variable will be not considered to because it has 49% empty cells.

Pool QC: If Nan or NA, property has no pool. This variable will be not considered to because it has close to 100% empty cells.

Fence: If Nan or NA, property has no fence. This variable will be not considered to because it has 80% empty cells.

Misc Feature: If Nan or NA, property has no noticeable miscellaneous features that are not covered in other features, for eg. Tennis Court. This variable will be not considered to because it has 97% empty cells.

# Outliers for SalePrice
Properties with prices more than 340,000 are considered outliers and were dropped.

![box](https://user-images.githubusercontent.com/72869207/99933098-0019cd00-2d95-11eb-9610-8d10c2d22946.png)

# Boxplots were made for SalePrice vs all the categorical variables to see their relationship.
![box_cat](https://user-images.githubusercontent.com/72869207/99933421-ffce0180-2d95-11eb-8aea-39bb80782d2b.png)

# 3 boxplots were replotted for better visual.

![box1](https://user-images.githubusercontent.com/72869207/99933613-8be02900-2d96-11eb-9f89-7760443210cb.png)
![box2](https://user-images.githubusercontent.com/72869207/99933634-9bf80880-2d96-11eb-8159-d1644c152a59.png)
![box3](https://user-images.githubusercontent.com/72869207/99933770-f1341a00-2d96-11eb-9a06-d7cb264dd2bb.png)

# Summary of findings from Boxplots

### Using the boxplot of SalePrice against Neighborhood as an example:

The median SalePrice of BrDale and IDOTRR is 10500 and 10200 respectively. The median SalePrice of StoneBr and NridgHt is 322450 and 317500 respectively. This shows that the neighborhood the property is built in has an effect on the SalePrice.

* Boxplots are evaluated based on the example above. If the categorical variable is deemed to have an effect on the SalePrice, the variables are selected and compiled in the list, ames_cat_select.

### The list of categorical variables are not selected. From their boxplots, these variables seem to have no effect on the SalePrice. 

* Lot Shape
* Land Contour
* Lot Config
* Land Slope
* Bldg Type
* House Style
* Roof Style
* Mas Vnr Type
* Bsmt Cond
* Bsmt Exposure
* BsmtFin Type 1
* BsmtFin Type 2
* Heating QC

# Next, the relationship between SalePrice and each numerical variable is examined.
![num_1](https://user-images.githubusercontent.com/72869207/99933810-0c9f2500-2d97-11eb-9d56-76630d186927.png)

# Numerical features that do not have a high degree of linear correlation with SalePrice were droppped.

# Pairplot was done to see if features that have high correlation with SalePrice are correlated with one another.

![pairplot](https://user-images.githubusercontent.com/72869207/99933838-1f195e80-2d97-11eb-972a-7e01622aff7c.png)

### There seem to have a linear correlation between the numerical variables from the pairplot above:

* Overall Qual is likely to have a linear correlation with Gr Liv Area, 1st Flr SF, Total Bsmt SF.
* Year Built seem to have no linear correlation with other variables.
* Year Remod/Add Built seem to have no linear correlation with other variables.
* Mas Vnr Area seem to have no linear correlation with other variables.
* Total Bsmt SF is likely to have a linear correlation with Gr Liv Area, 1st Flr SF.
* 1st Flr SF is likely to have a linear correlation with Gr Liv Area, Total Bsmt SF.
* Gr Liv Area is likely to have a linear correlation with TotRms AbvGrd, 1st Flr SF, Total Bsmt SF.
* TotRms AbvGrd is likely to have a linear correlation with Gr Liv Area.
* Garage Cars is likely to have a linear correlation with Garage Area.
* Garage Area is likely to have a linear correlation with Garage Cars.

* In summary, Overall Qual, Gr Liv Area, Garage Area will be the selected variables out of these numerical variables. The rest of the variables will be dropped. The 3 selected variables seem to be sufficient to represent the effect of the rest of the variables have on the SalePrice. If all the variables are included, it will have the colinearity effect on the model, hence they should be excluded.

# <span style = 'color:green'> Summary of Exploratory Data Analysis (EDA) <span>
1) Box plots of SalePrice against list of categorical variables in ames are plotted. The list of categorical variables that are evaluated to have an effect on SalePrice are short listed in ames_cat_select.
    
2) The relationship between SalePrice and each numerical variable is evaluated. 
* From the regplots, the numerical variables seem to be linearly correlated with SalePrice. 
* After that Pearson's correlation coefficient was used to evaluate the correlatoin strength of the numerical variables with SalePrice.
* 10 numerical variables are found to have high degree of correlation with SalePrice; their correlation coefficient value is > 0.5 
* Following that, 'Full Bath' and 'Garage Yr Blt' were dropped after evaluating the regplots, they do not have linear correlation with SalePrice.
    
3) The relationship between each numerical variable is checked with pairplot. 'Overall Qual', 'Gr Liv Area', 'Garage Area' are selected as the final numerical variables to build a linear regression model.

# 21 Features were selected after further analysis.

* Overall Qual
- Gr Liv Area
- Garage Area
- Roof Matl_CompShg
- Roof Matl_Membran
- Roof Matl_Tar&Grv
- Roof Matl_WdShake
- Roof Matl_WdShngl
- Roof Matl_nan
- Bsmt Qual_Fa
- Bsmt Qual_Gd
- Bsmt Qual_Po
- Bsmt Qual_TA
- Bsmt Qual_nan
- Kitchen Qual_Fa
- Kitchen Qual_Gd
- Kitchen Qual_TA
- Kitchen Qual_nan
- Garage Finish_RFn
- Garage Finish_Unf
- Garage Finish_nan

# 3 models were built and analyzed

## Linear Regression Model
![lr](https://user-images.githubusercontent.com/72869207/99933866-348e8880-2d97-11eb-9e33-dd9d6d35d29a.png)

##### Observations from the graph of coefficient values in <span style = 'color:teal'> lr</span> model

1) The roof material and basement quality has a strong effect on SalePrice. Here, the excellent external condition quality is used as the base. For properties that do not have excellent quality, they are penalized accordingly. A property with poor basement quality has a negative coefficient around -52,000.

Bsmt Qual is the basement quality, where the height of the basement is rated as below:

|Rating|Description|
|---|---|
       |Ex|	Excellent (100+ inches)|	
       |Gd|	Good (90-99 inches)|
       |TA|	Typical (80-89 inches)|
       |Fa|	Fair (70-79 inches)|
       |Po|	Poor (<70 inches|
       |NA|	No Basement|
       
Based on the article below, it seems that a good quality basement can add value to the house. Hence it may explain why basement quality has a strong effect on the SalePrice.

https://www.thebalancesmb.com/pros-of-finishing-a-basement-for-property-investors-2124861#:~:text=In%20the%20United%20States%2C%20on,the%20property%20by%20about%20%247%2C000.

2) For roofs built with wood shingles and membrane, they have a huge positive effect on the SalePrice of the house. It may imply buyers seem to prefer houses with roofs built with such materials and value them highly.

3) From the link below, roofing materials have different durabilities and price. Here, the materials listed in 1) seems to be the most popular based on the lr model. Wood is a natural insulator, it can help to keep the temperature of the house consistent. It may be commonly chosen because it can help to save bills by reducing the usage or air conditioner or heater.

https://housemethod.com/maintenance/6-best-roofing-materials-ranked-by-durability-and-cost/

## Ridge Linear Regression Model
![Ridge](https://user-images.githubusercontent.com/72869207/99933972-8800d680-2d97-11eb-9cde-c11e6bc7873b.png)

### Observations from the graph of coefficient values in <span style = 'color:blue'> Ridge </span> model

1) In the lr model, the roof material has an effect on the SalePrice. Here, looking at Roof Matl_Membran, Roof Matl_WdShngl, their effect on the SalePrice is small. Their coefficient values are around 2,000.

2) Comparing the coefficient values for the high impact features mentioned in 1), they still have a positive impact on SalePrice, but it is reduced.

3) Garage Area is seen to have a stronger effect on SalePrice, its coefficient is around 10,000. It may be immportant because Americans tend to have their own private transport hence the need for a sizable garage.

4) Kitchen quality also has an effect on SalePrice, its coefficient is around -20,000. It may be immportant because Americans may prefer to cook often.

5) Gr Liv Area and Overall Qual became the features with the highest impact on SalePrice, Gr Liv Area being the first with coefficient value at around 19,000 followed by Overall Qual with coefficient value at around 17,000.

6) For categorical variables, 'Exter Qual', 'Exter Cond', 'Bsmt Qual', 'Kitchen Qual', 'Garage Qual', their quality / condition is rated as:
   
|Rating|Description|
|---|---|
       |Ex |  Excellent|
      | Gd|	Good|
      | TA|	Typical/Average|
       |Fa	|Fair|
      | Po|	Poor|
       |NA	|No Garage|
       
**Ex is the baseline rating for this model. To avoid the dummy variable trap in regression model it was dropped during the categorical variable to discrete variable transformation process. Using an example, if the house kitchen quality is typical rating, it will be 16,000 lesser than a house with excellent quality kitchen, if both houses have the same score / rating for other features.**

7) **Overall Qual** is overall quality of the house, which is a categorical variable which consists of ratings 1 to 10. **GrLivArea** is the Above grade (ground) living area square feet. By referring to the document in the link below, it refers to the total finished square footage measured at and above ground level as it appears from the front view of the building. It consists of the main floor plus any floors above that are finished. To be considered finished, the area must have flooring wall covering (trimmed), and ceiling. Here, it shows that buyers value the degree of finishing for the main floor and second floor, and the overall quality of the house. It makes sense because buyers will prefer good quality houses so that they can minimize the cost of refurbishing the house again. However, this is subjected to the requirements of the buyers; if they wish to customize their own house, they may go for cheaper houses with poorer finishings.

https://cms.cws.net/content/semnrealtors.com/files/Finished%20Above%20Grade%20Square%20Feet.pdf

8) Bsmt Qual is the basement quality, where the height of the basement is rated as below:

|Rating|Description|
|---|---|
       |Ex|	Excellent (100+ inches)|	
       |Gd|	Good (90-99 inches)|
       |TA|	Typical (80-89 inches)|
       |Fa|	Fair (70-79 inches)|
       |Po|	Poor (<70 inches|
       |NA|	No Basement|
       
Based on the article below, it seems that a good quality basement can add value to the house. Hence it may explain why basement quality has a strong effect on the SalePrice.

https://www.thebalancesmb.com/pros-of-finishing-a-basement-for-property-investors-2124861#:~:text=In%20the%20United%20States%2C%20on,the%20property%20by%20about%20%247%2C000.

## Lasso Regression Model
![Lasso](https://user-images.githubusercontent.com/72869207/99934002-a070f100-2d97-11eb-8cb2-89873caeed6e.png)

### Observations from the graph of coefficient values in <span style = 'color:orange'> Lasso </span> model

1) Similar to the Ridge model, looking at Roof Matl_Membran, Roof Matl_WdShngl, their effect on the SalePrice is small. Their coefficient values are around 2,000.

2) Similar to ridge model, Gr Liv Area and Overall Qual are still the features with the highest impact on SalePrice, Gr Liv Area and Overall Qual have coefficient values at around 23,000, followed by Garage Area with coefficient value at around 12,500. In the lr model, these features have little effect on SalePrice.

3) Similar to ridge model, garage area has an effect on SalePrice.

4) Similar to ridge model, Exter Qual, Bsmt Qual, Kitchen Qual and Bmst Qual have a strong effect on SalePrice. The coefficient value is around -17,000 for Basement quality and -20,000 for kitchen quality.

# Use linear regression, ridge linear regression, lasso linear regression models to predict SalePrice in Kaggle Test data

![P2_kaggle_results_24Nov](https://user-images.githubusercontent.com/72869207/99934032-bda5bf80-2d97-11eb-94c2-5cf2423326bf.PNG)

* The Ridge and Lasso Regression models have very close scores.
* The RMSE of lasso is close to its estimated score 35102 (estimated) vs 37444 (kaggle test data).

# Conclusion:

* Lasso is the best model
* Overall Qual, Gr Liv Area, Garage Area, Basement Quality, Kitchen Quality can be used mainly to predict the SalePrice.
* The model can be used to give a price evaluation for property sellers, and buyers can also use it to estimate the price of a property.