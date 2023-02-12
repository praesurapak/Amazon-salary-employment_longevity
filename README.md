# Amazon's Human Resources: Sensitivity Analysis of Employee's Salary & Employment Longevity

Assuming that the corporation is interested in the sensitivity of its employees' salary to employment longevity, this report contains an analysis for Amazon's human resources, focusing on the causal relationship between salary changes and longevity. By using Stata, this analysis is based on observational data that contains information about average employee longevity, average salary, and other variables for multiple groups of employees of Amazon at one point in time.

This project is a final project of BUS-G 492: Predictive Analytics Business Strategy at Kelley School of Business 
Project by: Prae Kongchan

# The Effect of Salary Changes on Longevity
To find the effect of salary changes on employment longevity, the estimation that comes from the simple regression model of average salary and average longevity is not a good estimate of the causal effect of salary changes on employment longevity in the population. This happens because salary is a strategic variable that does not have the feature of a randomly assigned treatment. What this means is the treatment (higher salary) probably was given to observations (employees) where the effect was greater. For example, giving a higher salary to older employees might make them stay at the company longer; different groups of employees have a different response to the treatment of higher or lower salaries.

# Confounding Factors
To find potential confounding factors which arise because of different entities, the first step is finding the differences between a group of high salary workforce (treated group) and a group of low salary workforce (untreated group) at Amazon. The possible differences include position, age, education years, location of work, possibly race, and gender.

# Tools to Reduce Endogeneity Issue
What is needed to estimate a causal relationship is an exogenous model, meaning that a model should not have any endogenous X variables. Because the data is cross-sectional where there is no variation in time, attacking an endogeneity problem by adding control variables can reduce the endogeneity issues. A control variable is any independent variable that has been confounding factors, but can be added to a regression model to reduce an endogeneity problem.

## Adding Control Variables
The first model is a regression of average salary on employment longevity, controlling for age, education years, and location of work, utilizing the code reg on Stata. The control variables include average age, average education years, unemployment rate, and dummy variable coast, which is a binary variable where 1 means the office location is near to coast and 0 means the office location is not near to the coast. Locations that are near to the the coast and have low unemployment rate tend to have stronger labor market and more job availability that may refrain employees from retaining at Amazon for a long period.
<img width="456" alt="1" src="https://user-images.githubusercontent.com/112535634/218336727-6bfc3dad-8aba-48c8-95e7-b4367b562900.png">

The result of the regression indicates that by holding age, education years, unemployment rate, and coast constant, the coefficient of average longevity indicates that every $1000 increase in average salary is correlated with 0.026 years increase in employment longevity of employees at Amazon. The t-statistics shows that the observation of 0.026 is 3.85 standard errors above the null hypothesis of the salary having no effect. The p-value is equal to 0, which means that it is statistically significant, so we do reject the null hypothesis of salary has no effect. The insignificant variables are average years of education and unemployment rate. Yet, this method likely does not entirely solve the endogeneity problem because of the unavailability of data which restricts us from including every confounding factors into the model.


