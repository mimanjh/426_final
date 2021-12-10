# Introduction

Throughout the years, plenty of technology companies have emerged. Within the technology field, five companies are known for being the most prominent technological companies of America. They are known as the FAANG company. FAANG company contains Facebook, Amazon, Apple, Netflix and Google. STEM major graduates that work within these companies are known for receiving high compensations. Our question of interest is to determine which working demographics in the STEM field yield the highest total yearly compensation.
With a given dataset that contains different companies, positions, and salary, through data cleaning and wrangling, we can used a decision tree model to investigate which features influenced the total yearly compensation of these FAANG companies.

# Data Cleaning

The data that we used in this analysis was found here: https://www.kaggle.com/jackogozaly/data-science-and-stem-salaries. It contains 125,000 observations of different employees (de-identified), the company they work at, their job position, their salary, and other information. After reading in the data, we had to perform extensive data cleaning and wrangling in order to answer our question of interest.

Although this dataset included many different features, the features that were of interest to us in this dataset included the following variables:
* **totalyearlycompensation**: Total yearly salary per given person
* **yearsofexperience**: Total experience/years in field per given person
* **yearsatcompany**: Total years working at the company per given person
* **basesalary**: Total base salary for given position per given person
* **bonus**: Bonus given per given person
* **company**: the names of many different STEM companies
* **title**: the job position of each company
* **location**: the location of the company office

Because our question of interest only pertained to the five FAANG companies, we had to select those specific rows to create a new, cleaner dataset. It is important to note that within the dataset, the names of the companies were termed with different capitalization styles as well as titles (i.e Amazon, Amazon Inc., amazon, Amazon Web Services, Google, google, etc). Therefore, in order to effectively prepare the dataset for modeling, we had to select all rows regardless of terming style and rename the company names. The data cleaning for this particular portion of the analysis can be found in three different files on this repository called emily_wrangle.ipynb, jacob_wrangle.ipynb, and Felicia-Wrangling.ipynb.

Furthermore, as part of the data cleaning process, we created dummy variables for the company names, the location, and the job title as they were categorical variables.

Upon additional consideration, we felt the company location feature would have a high correlation with the company would thus add additional possibly weighted effects to our results. Therefore, we excluded this variable from our analysis.

Our newly cleaned dataset that we used in our modeling contained the following variables:
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
* **Highschool**: binary variable of whether the individual has went to high school or not (1,0)
* **Bachelors_Degree**: binary variable of whether the individual has a bachelor's degree or not (1,0)
* **Masters_Degree**: binary variable of whether the individual has a master's degree or not (1,0)
* **Doctorate_Degree**: binary variable of whether the individual has a PhD or not (1,0)
* **Some_College**: binary variable of whether the individual has some college experience or not (1,0)
* **title_Mechanical Engineer**: binary variable of the person is Mechanical Engineer or not (1,0)
* **title_Product Designer**: binary variable of the person is Product Designer or not (1,0)
* **title_Product Manager**: binary variable of the person is Project Manager or not (1,0)
* **title_Recruiter**: binary variable of the person is Recruiter or not (1,0)
* **title_Sales**: binary variable of the person is Sales person or not (1,0)
* **title_Software Engineer**: binary variable of the person is Software Engineer or not (1,0)
* **title_Software Engineering Manager**: binary variable of the person is Software Engineering Manager or not (1,0)

With further inspection of the dataset, we found duplicates within the education features of the dataset that we thought were unnecessary for the analysis and would introduced unwanted bias into the data. For example, if someone had a bachelors (1) and a masters (1) it is possible that this observation would affect the results of both the Masters_Degree and Bachelors_Degree. Therefore, we reclassified rows similar to this to only mark the highest degree of education degree as (1) and all other degrees of education as (0).

We removed rows containing zero values within the base salary variable. We also noticed existing zero values for several values for 'yearsofexperience' and 'yearsatcompany' variables. In this case, they are newly hired people and so we did not drop these zero values.

# Exploratory Data Analysis
To make sure the data summary is accurate, we made sure that none of our variables had missing values. Given the dataset summary, we were able to look through the count, mean, standard deviation, minimum, maximum and three quartiles.
![plots](/figures/1.png)

For further exploratory analysis, we created bar graphs and scatter plots. The given bar graphs compares total yearly compensation between the FAANG companies. It was intersting to find that Netflix has the highest pay and Amazon has the lowest pay.
![plots](/figures/2.png)

We created a scatterplot to compare the total yearly compensation with the years of experience from the employees of the different companies. We also created a scatterplot to compare the total yearly compensation with the years at the different companies.
We can see that google has the most dispersed area of pay with employees of different experience levels and years at the company. Highest pay from most of the FAANG company is within the 10-20 years of experience range. The years at company variable contains pretty similar compensation throughout the graph. We can see that facebook employees usually stay in the company within 10 years. Google employees usually stay within the company for 15 years with some exceptions that stayed for more that 15 years. Amazon has employees ranged from 0 years in the company to 20 years in the company.\
![plots](/figures/3.png)

To see the relation between education level and total yearly compensation of each company, we created a bar plot. We can see that Netflix and Google give the highest compensation for workers that has education level of some college. Surprisingly, Apple gives a higher compensation for workers with high school diploma. Facebook and Amazon, on the other hand, compensate more for employees with PhD. \
![plots](/figures/4.png)

Lastly, we created a histogram to see the distribution of compensasion within all of the FAANG companies. \
![plots](/figures/5.png)


# Methods/Models
We created a training set and a test set from the dataset in order to test various models and cross validations. We set **totalyearlycompensation** as our predictor variable and the rest of the dataset is set as dependent variables. We made our test size 25% of our train data set to create our models and perform cross validations. \
We selected different statistical models such as linear regression, KNN, lasso, decision tree, naive bayes, and a random forest model to find which features most impacts the total yearly compensation an employee receives. We retrieved the **root-mean-square-error** (rmse) and the **cross validation** (cv) from the models that we have tested to compare model performances. The following are the results of our in-sample and cross validated results

# Model Justification
**Linear Model**: \
In-sample RMSE:  < 0.01 \
CV:  < 0.01 
 
**KNN Model**: \
In-sample RMSE:  62610.59 \
CV:  15803.46 
 
**Lasso**: \
In-sample RMSE:  < 0.01 \
CV:  < 0.01  
 
**Decision Tree**: \
In-sample RMSE:  68087.21 \
CV:  20522.03 
 
**Random Forest**: \
In-sample RMSE:  117870.448 \
CV:  79758.60 
 
**Naive Bayes**: \
In-sample RMSE:  143560.02 \
CV:  147268.58

It was interesting to find that linear model and lasso regression has the lowest retrieveble RMSE. However, due to models assumptions not being met, we did not consider these models for further interpretation and performance value. KNN and the decision tree model had the next lowest RMSE values with $15,803 and $20,522 respectively. Because our question of interest is to know which variables have the largest influence in an a company's total yearly compensation, we selected the decision tree of our model of choice because of the KNN model's results' lack in interpretability.

# Results
The follow gives a visual of the variable importance values extracted from the decision tree model:

![plots](/figures/coefficient.png)

From the given table, we can see the coefficient value between **totalyearlycompensation** and the independent variables. From then, we can see how each variable influences **totalyearlycompensation**. This can help us analyze which scenarios would give us the great **totalyearlycompensation**.
From the table, **totalyearlycompensation** has variable importance values with variables **bonus, basesalary, yearsatcompany, title_Software Engineer, yearsofexperience, company_Facebook, company_Google, company_Amazon, Masters_Degree**. We conclude that the bonus, base salary, and years at a company are the most important features in affecting the total yearly compensation a company receives from their company.

# Conclusion
In conclusion, it is more idealistic for someone who has been in the company for some years with bonus and a base salary to see their total yearly compensation affected. Therefore, based on our analysis, we recommend those looking for employment in the STEM field within the FAANG companies to consider these variables as a few that would influence the total yearly compensation one would receive.

**Possible Next Steps** \
Our possible next steps may be adjusting the number of observations we have for each company by over and under sampling our data. We found that the imbalance between Netflix company observations (~200) compared to the other companies' observations (~1000) may lead to unwanted bias. We would also consider extending our analysis by using our model to create predictions for certain working scenarios so that other may know exactly how much their total yearly compensation would be given a certain job title, the company they work at, their base salary, etc.

by Jacob Hunsaker, Emily Liu, Felicia Seng
