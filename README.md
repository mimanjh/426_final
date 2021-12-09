# Introduction

Throughout the years, plenty of technology companies have emerged. Within the technology field, five companies are known for being the most prominent technological companies of America. They are known as the FAANG company. FAANG company contains Facebook, Amazon, Apple, Netflix and Google. STEM major graduates that work within these companies are known for receiving high compensations. Our question of interest is to determine which working demographics in the STEM field yield the highest total yearly compensation.
With a given dataset that contains different companies, positions, and salary, through data cleaning and wrangling, we can use models to predict and see which FAANG company gives the best compensation. 
Our main focus of interest for this given project is to see which working scenario would give the best total compensation per year.

# Data Cleaning

The dataset given contains the following variables:
* totalyearlycompensation: Total Yearly Salary per given person.
* yearsofexperience: Total experience/years in field per given person
* yearsatcompany: Total years working at the company per given person
* basesalary: Total base salary for given position per given person
* bonus: Bonus given per given person
* company_Amazon: binary variable of whether the company is Amazon or not (1,0)
* company_Apple: binary variable of whether the company is Apple or not (1,0)
* company_Netflix: binary variable of whether the company is Netflix or not (1,0)
* company_Google: binary variable of whether the company is Google or not (1,0)
* company_Facebook: binary variable of whether the company is Facebook or not (1,0)
* title_Mechanical Engineer: binary variable of the person is Mechanical Engineer or not (1,0)
* title_Product Designer: binary variable of the person is Product Designer or not (1,0)
* title_Product Manager: binary variable of the person is Project Manager or not (1,0)
* title_Recruiter: binary variable of the person is Recruiter or not (1,0)
* title_Sales: binary variable of the person is Sales person or not (1,0)
* title_Software Engineer: binary variable of the person is Software Engineer or not (1,0)
* title_Software Engineering Manager: binary variable of the person is Software Engineering Manager or not (1,0)


With further inspection of the dataset, we realized that there are duplicates within some variables of the dataset. The duplicates mostly showed up within the education status of the given person. For example, if someone had a bachelors (1) and a masters (1) then we reclassify that row that they only have a masters (1) and not bachelors (0).
Also, we removed rows that contained zero within the base salary variable. We then noticed that there are also zero values for some 'yearsofexperience' and 'yearsatcompany' variables. In this case, we will assume that they are newly hired people and will not drop those 0 values. Because there would be a correlation between the companies and the location of where the companies are based in in relation to the total yearly compensation variable, we decided to drop the location variable.


# Exploratory Data Analysis
To make sure the data summary is accurate, we made sure that non of our variables had missing values. Given the dataset summary, we were able to look through the count, mean, standard deviation, minimum, maximum and three quartiles. 
*insert image*

For further analysis, we created bar graphs and scatter plots. The given bar graphs compares total yearly compensation between the FAANG companies. It has shown that Netflix has the highest pay and Amazon has the lowest pay.
*insert box plot image*

With further inspections, we created a scatterplot to compare the total yearly compensation with the years of experience from the employees of the different companies. We also created a scatterplot to compare the total yearly compensation with the years at the different companies.
We can see that google has the most dispersed area of pay with employees of different experience levels and years at the company. Highest pay from most of the FAANG company is within the 10-20 years of experience range. The years at company variable contains pretty similar compensation throughout the graph. We can see that facebook employees usually stay in the company within 10 years. Google employees usually stay within the company for 15 years with some exception that stayed for more that 15 years. Amazon has employees ranged from 0 years in the company to 20 years in the company.
*insert scatter plot images*

To cmpare 




# Methods/Models
The Methods we selected

# Model Justification
(the cross validated results)


# Results

KNN gave the lowest RMSE, but it's results are not very interpretable, therefore we will go with the second best model which was the decision tree with 15 leaves. Its variable importance features are given below.


# Conclusion

**possible next steps

This is for the final project of Stat 426.

Data should be stored in data directory.

Companies of interest: Google, Amazon, Apple, Netflix, and Facebook

- Jacob Hunsaker, Emily Liu, Felicia Seng
