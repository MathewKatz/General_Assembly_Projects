## MLB Win Projections

(2020 Season was not predicted due to a covid-shortened season)

### Table of Contents
Below is a table of contents, which contains the file name, file order, and file description. The file order column represents which order the files should be opened and read. File Order 1 should be started with. 

**File Name**|**File Order**|**File Description**
:-----:|:-----:|:-----:
README.md|1|The README file contains the executive summary and overview of the project as a whole.
01_Gathering_and_Cleaning_Data.ipynb|2|Python Notebook contains how I acquired and cleaned the data recquired to make the win projections. 
02_Preprocessing_&_EDA.ipynb|3| Python Notebook contains some preprocessing and exploratory data analysis.
03_Modeling.ipynb|4|Python Notebook contains all the models and their RMSE scores. It also includes some predictions at the end. 
04_Evaluation_Conclusion.ipynb|5|Python Notebook contains final evaluations and conclusions.
powerpoint-presentation.pdf|6|A pdf containing the powerpoint slides I  used during project presentations.
Data|7|The folder with all of the data used.

#### The Problem
Is there a way to predict how many wins each team in the MLB will have in the upcoming season? It could be very beneficial to a sports gambler but also interesting to the common fan.  

#### The Solution
Use the statistics that are highly correlated to wins, and create a regression model that can accurately predict a team's wins based on the previous season's stats. 

#### Evaluation Metrics
The goal was to create a model which performed above the null model in RMSE. The null model is a starting point to compare the performance of future models to. I used the DummyRegressor from sklearn. It predicted the mean of the training target values. The RMSE score for the null model was a 13.06166647 RMSE.

RMSE is a quadratic scoring rule that also measures the average magnitude of the error. It’s the square root of the average of squared differences between prediction and actual observation. RMSE was the best predictor of model accuracy in this case.


#### Data Acquisition, Preprocessing, and Modeling 
The dataset of MLB stats was pulled from a collection of yearly statistics posted by 'Fangraphs.'
An example of one of the years is shown here :
(https://www.fangraphs.com/leaders.aspx?pos=all&stats=bat&lg=all&qual=0&type=8&season=2020&month=0&season1=2020&ind=0&team=0,ts&rost=0&age=0&filter=&players=0&startdate=&enddate=)
After downloading the very many datasets, (both pitching and hitting team stats for the years 2009-2019,) I added a win column from the previous year to each pitching dataset before merging it with the hitting statsistic. For example, if I pulled the statistics from the year, then the wins from 2018 were added. './P' was added to the pitching statistics to be able to distinguish columns that are in both the hitting and pitching statistics such as WAR. I then made sure that all the columns were the 'full' team names and not just the team initials. Nextly, the NaNs (NaN stands for Not A Number and is a common missing data representation,) were removed. That left us with 300 rows (30 teams x 10 years) and 527 columns (different hitting and pitching statistics.)     

<<<<<<< HEAD
Thousands of models were run using: 'K/9./P','ERA./P','FIP./P','WAR./P','H./P','R./P','K/BB./P','AVG./P','WHIP./P','WPA./P','REW./P','WPA/LI./P','RBI','wOBA','wRC+','WAR','OPS','WPA','REW','WPA/LI', and 'OBP+' as the features to try and predict wins. Here are the results:
<img src = "Data/Model_RMSEs.png" width="500" height="500">
=======
Thousands of models were run using saves./P, ERA./P, fWAR./P, hits./P, runs./P', AVG./P, WHIP./P, WPA./P, REW./P, WPA/LI./P, wRC+, fWAR, WPA, REW, WPA/LI, and OBP+ as the features to try and predict wins. Here are the results:
<img src = "Data/Regressor RMSEs.png" width="500" height="500">
>>>>>>> df59351041deffbdcc7323b769385464b1c488c5


#### Final Production Models
There were two final models. One was the ridge model and the other was the random forest regressor. Random Forest Regressor was used for the 2019 predicton and Ridge for the 2021 prediction. 
Ridge parameters were {'rid__alpha': 1.0, 'rid__copy_X': True, 'rid__fit_intercept': True, 'rid__normalize': True, 'rid__solver': 'auto', 'rid__tol': 1e-05}
and Random Forest parameters were {'rfr__n_estimators': 175}.


#### The Conclusion
My venture to create a regressor model which performed above the null model was successful. The Final Production model for 2019 was relatively successful in predicting wins for teams in the MLB. The average difference between my Model's Projections for the 2019 Season and the actual wins was about 5 wins. Most team win projections were actually closer but due to outliers like the Marlins, Tigers, and the Twins, it became a higher average. As for the 2021 season. We will see how well it did in October.     


#### Improvements
Though the model showed strong predictive power, there are improvements to note going forward. The size of the dataset was small, so in the future it would be highly beneficial to continue to improve model performance with more data. Although I obtained a strong predictive model, it did not take offseason acquisitions into consideration. That is something I'd love to add to my model in the future. 




