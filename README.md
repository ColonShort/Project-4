# Project-4
### Tableau Notebooks
[Notebook 1](https://public.tableau.com/app/profile/rod.hughes/viz/Project4_16890380242060/SalaryStory?publish=yes)

[Notebook 2](https://public.tableau.com/app/profile/kelly.hendre/viz/PayGapinTechRoles/PayGapinTechRoles?publish=yes)

## Machine Learning Report

### Background
According to recently published Census Bureau data, women of all races in the U.S. earn on average 82 cents for every $1 earned by men of all races, and women in high-paying industries like tech are not immune to this norm. To further provide context, companies with 250+ employees must publish a yearly report detailing their gender pay gap and the latest reports show that in tech, 91.1% of companies pay their male employees more than their female staff. This puts the tech industry’s gender pay gap at 16%, higher than the national average of 11.6%.

To explore this problem in greater depth, we downloaded 2022 data from the Stack Overflow Annual Developer Survey and examined several key data points, including gender, languages, salary, continent, education level, and experience.

### Machine Learning

After thoroughly cleaning the data, we implemented supervised machine learning methods to explore relationships among features that most heavily impact yearly compensation.

First, we utilized the seaborn data visualization library to explore our data distributions by using pairplots and a heatmap. Both visualizations allowed us to better understand which features to use to investigate relationships in our data. After our initial exploration, we used the multiple linear regression algorithm to predict the outcome of “YearlyComp” (yearly compensation) based on the various independent variables we included in our model. In total, we attempted to optimize our model 6 times. Further discussion regarding each attempt is detailed below:

- First Attempt
  
For our first attempt, we used all relevant variables in our data frame, including employment type, gender(s), languages, continent, education level, and experience. Our statistical outputs for this model are as follows:

    R-squared Error – Test (R2)/Linear Regression Model Score: 0.12581609156350138
    Rounded Mean Squared Error (RMSE): 108875.69719
    Std. Dev: 111837.37456

- Second Attempt
  
For our second attempt, we dropped the “Trans” variable from our model to see if there would be any improvements, but we discovered that our model score remained approximately the same. Our statistical outputs for this model are as follows:

    R-squared Error – Test (R2)/Linear Regression Model Score: 0.12567399260042655
    Rounded Mean Squared Error (RMSE): 108884.54573
    Std. Dev: 111837.37456

- Third Attempt
  
From our exploratory data analysis, we know that “YearsCodePro” (years coded professionally) is heavily skewed and highly correlated with “WorkExp” (work experience), and thus, for our third attempt, we dropped the “YearsCodePro” variable from our model to see if there would be any improvements. However, as shown below, our model score decreased by .001. The statistical outputs for this model are as follows:

    R-squared Error – Test (R2)/Linear Regression Model Score: 0.12430002190921807
    Rounded Mean Squared Error (RMSE): 108970.06614
    Std. Dev: 111837.37456

- Fourth Attempt
  
For our fourth attempt, we used the scikit-learn library to perform feature transformations using decision tree regression, transformed target regressor, and quantile transformer. In this case, feature transformation did not yield any model improvements. Our statistical outputs for this model are as follows:

    R-squared Error – Test (R2): -0.185
    Mean Absolute Error (MAE): 56154.05
    Rounded Mean Square Error (RMSE): 126743.84

- Fifth Attempt
  
For our fifth attempt, we attempted to improve our model by additional feature selection. Specifically, we dropped “Emp” (employment), “EdLevel” (education level), “Trans” (transgender), and “Gender.” Once again, the R2 Error value decreased by .001, as shown below:

    R-squared Error – Test (R2)/Linear Regression Model Score: 0.12394276642616553
    Rounded Mean Squared Error (RMSE): 108992.2919
    Std. Dev: 111837.37456

- Sixth/Final Attempt

Lastly, for our final optimization attempt, we executed hyperparameter tuning from TensorFlow using the keras tuner. Our model accuracy came out to be 0.0.

### Conclusions:
Our model did not perform well likely due to the skewed dataset. Specifically, the gender distribution is heavily skewed toward men, as men are more frequently employed by tech companies and hold the majority of roles. Similarly, a large portion of survey respondents were men, specifically 6,602 vs. 264 women and 59 non-binary, further revealing the major disparities in gender representation in the tech sector. Our best R-squared Error from our optimization attempts was from our very first linear regression, which resulted in an R-squared error value of 0.125, which is considered a low R-squared value. Thus, we can assume that our independent variables do not thoroughly explain much variation in our dependent variable, yearly compensation. Provided more time, our team would have examined data spanning over 5-10 years, as opposed to just 2022.

### Additional Insights:
An essential step in any machine learning model is to evaluate the accuracy of the model. The Mean Squared Error, Mean Absolute Error, Root Mean Squared Error, and R-Squared or Coefficient of determination metrics are used to evaluate the performance of the model in regression analysis.

### Definitions:
R-squared Error (coefficient of determination) - statistical measure that represents the proportion of the variance for a dependent variable that’s explained by an independent variable(s) or the linear regression model. It is a scale-free score i.e. irrespective of the values being small or large, the value of R-squared will be less than one.

Mean Squared Error (MSE) - represents the average of the squared difference between the original and predicted values in the data set. It measures the variance of the residuals

Rounded Mean Squared Error (RMSE) - the square root of Mean Squared Error. It measures the standard deviation of residuals
Standard Deviation - a measure of the amount of variation or dispersion of a set of values. A low SD indicates that the values tend to be close to the mean (also called the expected value). A high SD indicates that the values are spread out over a broader range.

Mean Absolute Error - represents the average of the absolute difference between the actual and predicted values in the dataset. It measures the average of the residuals in the dataset.

Val_accuracy - indicates the accuracy of the predictions of a randomly separated validation set after each training period.


