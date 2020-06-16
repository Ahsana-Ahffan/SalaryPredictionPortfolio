

## Introduction:

   The goal of this project is to predict the salary of a new job posting with the help of job details like education,experience, seniority etc. The model is then later tested on a test data set to validate the accuracy of the model. 

The three datasets used for this project are train , test  and train salaries. The model is trained using train  dataset which has the features jobid, companyid,  jobtype, major, degree,  industry and the train salaries dataset which has the features jobid and the target variable salary.

The tool used is Python 3 along with its libraries and packages such as numpy, pandas, matplotlib, seaborn and sklearn to do data manipulation, data visualization and building the predictive model

## Exploratory Data Analysis(EDA):

Numerical and categorical varibles were identified and summarized separately. There are two numeral features - yearsExperience and milesFromMetropolis. The feature jobId is unique for all entry and it is not used to buld the model. The other categorical features are companyId with 63 unique values, jobType with 8 unique values, degree, major and industry with 5,9,7 unique values respectively.

### Visualizing Target Variable

![myimage-alt-tag](https://github.com/Ahsana-Ahffan/salarypredictionportfolio/blob/master/Images/Salary%20boxplot.png)

In the target variable's plot there were some suspicious potential outliers. 1.5 IQR rule was used to find the upper and lower bound of suspected outliers. There are 20 Junior positions with salary above the upper bound 220.5. But later after more examination of the data, it was clear that those data should be good as those entries had atleast 18 years of experience and almost most of them has masters or doctoral degree.

### Visualizing relation between features and the target

Each feature was plotted against the mean salary(target). 

![myimage-alt-tag](https://github.com/Ahsana-Ahffan/salarypredictionportfolio/blob/master/Images/JobType%20plot.png) ![myimage-alt-tag](https://github.com/Ahsana-Ahffan/salarypredictionportfolio/blob/master/Images/degree%20plot.png) ![myimage-alt-tag](https://github.com/Ahsana-Ahffan/salarypredictionportfolio/blob/master/Images/major%20plot.png) ![myimage-alt-tag](https://github.com/Ahsana-Ahffan/salarypredictionportfolio/blob/master/Images/Industry%20plot.png) 
![myimage-alt-tag](https://github.com/Ahsana-Ahffan/salarypredictionportfolio/blob/master/Images/CompanyId%20plot.png) ![myimage-alt-tag](https://github.com/Ahsana-Ahffan/salarypredictionportfolio/blob/master/Images/yearsExperience%20plot.png)![myimage-alt-tag](https://github.com/Ahsana-Ahffan/salarypredictionportfolio/blob/master/Images/milesFromMetropolis%20plot.png)

From the plots we can see that
1. Job type has a strong positve correlation with salary. That is senior job types has highest salary
2. Having advanced degree helps the job seeker to get higher salary
3. Those with Engineering, Business, Math and Computerscience majors are paid higher
4. Oil and finance are the highest paying industries.
5. The feature companyId has no correlation with the target,salary
6. Those with more years of experience and paid higher
7. As the distance from metropolis decreases, salary increases

Apart from this to get an idea about the correlation between features, a heatmap was plotted and it showed that jobtype as the most strongly correlated feature with salary. Also Degree and Major have the strongest positive relationship.

![myimage-alt-tag](https://github.com/Ahsana-Ahffan/salarypredictionportfolio/blob/master/Images/Correlation%20plot.png)

## Feature Engineering:

The training data was cleaned, shuffled and reindexed and using one hot encoding categorical data was encoded to get the final training and test dataframes.

## Model Selection and Evaluation:

The four different regreesion algorithms selected were
1.Linear Regression
2 StandardScaler,PCA, Linear Regression Pipeline
3.Random Forest Regression
4.Gradient Boosting Regressor

Mean Squared Error(MSE) is selected as the evaluation metric. The model with lowest MSE is selected has the best model.

### Best Model
After doing 5 fold cross validation on each selected models, the following MSE was measured for corresponding models

1.Linear Regression                              -     384.46814580352583 
2 StandardScaler,PCA, Linear Regression Pipeline -     384.4675895960695
3.Random Forest Regression                       -     369.0068823587397
4.Gradient Boosting Regressor                    -     356.8304819975119

So Gradient Boosting Regressor with the lowest MSE was selected as the best model. The model was trained on the entire data set and prdeictions were created based on the test data.
Key predictors for this model are yearExperience and milesFrom Metropolis as shown in the Feature Importances plot.

![myimage-alt-tag](https://github.com/Ahsana-Ahffan/salarypredictionportfolio/blob/master/Images/Feature%20imp%20plot.png)







