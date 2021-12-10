# Introduction

Throughout the years, plenty of technology companies have emerged. Within the technology field, five companies are known for being the most prominent technological companies of America. They are known as the FAANG company. FAANG company contains Facebook, Amazon, Apple, Netflix and Google. STEM major graduates that work within these companies are known for receiving high compensations. Our question of interest is to determine which working demographics in the STEM field yield the highest total yearly compensation.
With a given dataset that contains different companies, positions, and salary, through data cleaning and wrangling, we can use models to predict and see which FAANG company gives the best compensation. \
Our main focus of interest for this given project is to see which working scenario would give the best total compensation per year.

# Data Cleaning

The dataset given contains the following variables:
* **totalyearlycompensation**: Total Yearly Salary per given person.
* **yearsofexperience**: Total experience/years in field per given person
* **yearsatcompany**: Total years working at the company per given person
* **basesalary**: Total base salary for given position per given person
* **bonus**: Bonus given per given person
* **company_Amazon**: binary variable of whether the company is Amazon or not (1,0)
* **company_Apple**: binary variable of whether the company is Apple or not (1,0)
* **company_Netflix**: binary variable of whether the company is Netflix or not (1,0)
* **company_Google**: binary variable of whether the company is Google or not (1,0)
* **company_Facebook**: binary variable of whether the company is Facebook or not (1,0)
* **title_Mechanical Engineer**: binary variable of the person is Mechanical Engineer or not (1,0)
* **title_Product Designer**: binary variable of the person is Product Designer or not (1,0)
* **title_Product Manager**: binary variable of the person is Project Manager or not (1,0)
* **title_Recruiter**: binary variable of the person is Recruiter or not (1,0)
* **title_Sales**: binary variable of the person is Sales person or not (1,0)
* **title_Software Engineer**: binary variable of the person is Software Engineer or not (1,0)
* **title_Software Engineering Manager**: binary variable of the person is Software Engineering Manager or not (1,0)


With further inspection of the dataset, we realized that there are duplicates within some variables of the dataset. The duplicates mostly showed up within the education status of the given person. For example, if someone had a bachelors (1) and a masters (1) then we reclassify that row that they only have a masters (1) and not bachelors (0).\
Also, we removed rows that contained zero within the base salary variable. We then noticed that there are also zero values for some 'yearsofexperience' and 'yearsatcompany' variables. In this case, we will assume that they are newly hired people and will not drop those 0 values. Because there would be a correlation between the companies and the location of where the companies are based in in relation to the total yearly compensation variable, we decided to drop the location variable.


# Exploratory Data Analysis
To make sure the data summary is accurate, we made sure that non of our variables had missing values. Given the dataset summary, we were able to look through the count, mean, standard deviation, minimum, maximum and three quartiles. \
![plots](/figures/1.png)

For further analysis, we created bar graphs and scatter plots. The given bar graphs compares total yearly compensation between the FAANG companies. It has shown that Netflix has the highest pay and Amazon has the lowest pay.\
*insert box plot image* \

With further inspections, we created a scatterplot to compare the total yearly compensation with the years of experience from the employees of the different companies. We also created a scatterplot to compare the total yearly compensation with the years at the different companies.
We can see that google has the most dispersed area of pay with employees of different experience levels and years at the company. Highest pay from most of the FAANG company is within the 10-20 years of experience range. The years at company variable contains pretty similar compensation throughout the graph. We can see that facebook employees usually stay in the company within 10 years. Google employees usually stay within the company for 15 years with some exception that stayed for more that 15 years. Amazon has employees ranged from 0 years in the company to 20 years in the company.\
*insert scatter plot images* \

To see the relation between education level and total yearly compensation of each company, we created a bar plot. We can see that Netflix and Google give the highest compensation for workers that has education level of some college. Surprisingly, Apple gives a higher compensation for workers with high school diploma. Facebook and Amazon, on the other hand, compensate more for employees with PhD. \
*insert bar chart* \

Lastly, we created a histogram to see the distribution of compensasion within all of the FAANG companies. \
*insert histogram* \


# Methods/Models
To try differnet modeling methods, we first need to crete a training set and a test set from the dataset. We set **totalyearlycompensation** as our predicting variable and the rest of the dataset is set as dependent variable. We made our test size 25% due to the large data collected. \
We selected different regression methods like Linear Regression, knn, Lasso, Decision Tree, Naive bayes, and Forest to test our dataset. Using GridSearchCV we were able to find the appropriate parameter values. By doing so, we were able to calcualte model metrics. We retrieved the **root-mean-square-error** (rmse) and the **cross validation** (cv) from the models that we have tested. 

# Model Justification
**Linear Model**:
rmse:  7.362988708711129e-10 \
cv:  2.8467565565876175e-10 
 
**KNN Model**:
rmse:  62610.592543503764 \
cv:  15803.461720104542 
 
**Lasso**:
rmse:  4.239566307252631e-06 \
cv:  3.3784014691009395e-06 
 
**Tree Regressor**:
rmse:  68087.21755274128 \
cv:  20522.0325581909 
 
**Forest**:
rmse:  117870.44830855382 \
cv:  79758.59977031744 
 
**Naive Bayes**: 
rmse:  143560.01764258926 \
cv:  147268.57615946242 

*The given list is the rmse and cv we have retrieved from the models*
To find the best model, we would want a model with the lowest rmse. Linear model and lasso regression has the lowest retrieveble rmse, yet due to assumptions not met, we look for the next lowest model. KNN contains the thrid lowest RMSE. However, it's results are not very interpretable. Therefore we will go with the next best model which was the decision tree with 15 leaves. (Decision Tree model with 15 leaves contains the 2nd lowest RMSE.)

# Results
As we run decision tree, we sorted the values to see the relation and the importance between variables. 

*insert coefficient value table below* \

From the given table, we can see the coefficient value between **totalyearlycompensation** and the independent variables. From then, we can see which variables correlates to **totalyearlycompensation**. This can help us analyze which scenarios would give us the great **totalyearlycompensation**
From the table, **totalyearlycompensation** has coefficient values with variables **bonus, basesalary, yearsatcompany, title_Software Engineer, yearsofexperience, company_Facebook, company_Google, company_Amazon, Masters_Degree**

# Conclusion
From results, we can conclude a scenario that would give the best total compensation per year. It is more idealistic for someone who has been in the company for some years with bonus and a base salary to receive a higher yearly compensation. Software Engineers receive a higher pay from other job positions within the companies. Facebook, Google, Amazon give the highest compensation within the FAANG company. Between the three, Facebook has the highest compensation. Lastly, having a masters degree may contribute more to a higher compensation. 
Thus, idealistically, if someone wants to have a high salary working in a FAANG comapny, he or she should have a masters degree in software engineering and work for Facebook, Amazon, and Google for a few years with a base salary and a bonus.

**Possible Next Steps**
Because our coefficient values are not very significant. Our possible next steps may be adjusting the coefficient value or the variables to find a more significant value. We can also create prediction by allowing people manually type in numbers for different variables.

by Jacob Hunsaker, Emily Liu, Felicia Seng
