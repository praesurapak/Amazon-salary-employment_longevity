# Amazon's Human Resources: Sensitivity Analysis of Employee's Salary & Employment Longevity

This project is a final project of BUS-G 492: Predictive Analytics Business Strategy at Kelley School of Business (Fall 2021)

Project by: Prae Kongchan

Assuming that the corporation is interested in the sensitivity of its employees' salary to employment longevity, this report contains an analysis for Amazon's human resources, focusing on the causal relationship between salary changes and longevity. By using Stata, this analysis is based on observational data that contains information about average employee longevity, average salary, and other variables for multiple groups of employees of Amazon at one point in time.

# The Effect of Salary Changes on Longevity
To find the effect of salary changes on employment longevity, the estimation that comes from the simple regression model of average salary and average longevity is not a good estimate of the causal effect of salary changes on employment longevity in the population. This happens because salary is a strategic variable that does not have the feature of a randomly assigned treatment. What this means is the treatment (higher salary) probably was given to observations (employees) where the effect was greater. For example, giving a higher salary to older employees might make them stay at the company longer; different groups of employees have a different response to the treatment of higher or lower salaries.

# Confounding Factors
To find potential confounding factors which arise because of different entities, the first step is finding the differences between a group of high salary workforce (treated group) and a group of low salary workforce (untreated group) at Amazon. The possible differences include position, age, education years, location of work, possibly race, and gender. The factors mentioned are automatically correlated with salary, given that they are the reasons why two groups are different. However, factors such as race and gender do not directly impact longevity. With this, the major confounding factors are position, age, education years, and location of work. The list of confounding factors also confirm that there is an endogeneity issue posed.

# Tools to Reduce Endogeneity Issue
What is needed to estimate a causal relationship is an exogenous model, meaning that a model should not have any endogenous X variables. Because the data is cross-sectional where there is no variation in time, attacking an endogeneity problem by adding control variables can reduce the endogeneity issues. A control variable is any independent variable that has been confounding factors, but can be added to a regression model to reduce an endogeneity problem.

## Adding Control Variables
The first model is a regression of average salary on employment longevity, controlling for age, education years, and location of work, utilizing the code reg on Stata. The control variables include average age, average education years, unemployment rate, and dummy variable coast, which is a binary variable where 1 means the office location is near to coast and 0 means the office location is not near to the coast. Locations that are near to the the coast and have low unemployment rate tend to have stronger labor market and more job availability that may refrain employees from retaining at Amazon for a long period.

<img width="456" alt="1" src="https://user-images.githubusercontent.com/112535634/218336727-6bfc3dad-8aba-48c8-95e7-b4367b562900.png">


The result of the regression indicates that by holding age, education years, unemployment rate, and coast constant, the coefficient of average longevity indicates that every $1000 increase in average salary is correlated with 0.026 years increase in employment longevity of employees at Amazon. The t-statistics shows that the observation of 0.026 is 3.85 standard errors above the null hypothesis of the salary having no effect. The p-value is equal to 0, which means that it is statistically significant, so we do reject the null hypothesis of salary has no effect. The insignificant variables are average years of education and unemployment rate. Yet, this method likely does not entirely solve the endogeneity problem because of the unavailability of data which restricts us from including every confounding factors into the model.

# Tools to Eliminate Endogeneity Issue Instrumental Variables
At this point, it is reasonable to believe that X variables is correlated with U or other possible omitted factors outside the model that correlates with salary changes and directly affect longevity. To replicate random assignment and get rid of endogeneity to make model exogenous, utilizing instrumental variable is an appropriate method. Instrumental variable is a variable that varies with salary changes, but does not impact employment longevity.

Suppose budget boost does not impact employment longevity for Amazon, meaning two locations with the same salary, age, and geographic have the same expected longevity, even if their budget boost differ. In the other word, the observed group with budget boost is not special.

To expand, budget boost is a valid instrument for salary because:

1) It is exogenous; budget boost does not correlated with anything in U or other possible omitted factors outside the model that correlates with salary changes and directly affect longevity. Budget boost does not help predict employment longevity.

2) It is relevant; budget boost correlates with salary changes, but do not directly impact employment longevity. The correlation between salary and budget boost is 0.18. Although the correlation might be weak, it is still useful for the regression since it would preserve more of the good part. Additionally, in a business perspective, this would make sense because budget boost is the available budget which is likely to be passed on to employees through salary.

The second model is a two-staged least squares regression that utilized the code ivreg on Stata. 2SLS can control more than 1 confounding factors, keep good variations, and remove bad variations. Because 2SLS can leave behind some good parts, including significant variables of average age and coast as control variables into the model can retain some good variations. For this regression, supposed average age and coast are exogenous, meaning that those variables are not correlated with other possible omitted factors outside the model.

<img width="446" alt="2" src="https://user-images.githubusercontent.com/112535634/218336953-e25f8e3e-534f-4dfc-9dee-7df7355f8f27.png">

From the regression, the coefficient of average salary indicates that $1000 increase in average salary will result in 0.034 years increase in employment longevity of employees at Amazon. The t-statistics tells us that the observation of 0.034 is 28.15 standard errors above the null hypothesis of the salary having no effect. We can infer the causal relationship because using the budget boost as an instrumental variable, the model is exogenous. All coefficients are significant because the p-values are less than 0.05.

## Recommendation
Based on empirical findings of positive causal relationship, salary changes is explicitly link to employment longevity. To meet its long-term human resources strategic objective of increasing employment longevity, Amazon should increase salary to employees. The indirect cost like time and direct financial costs associated with losing employees along with hiring and training replacements for an enterprise like Amazon, given its size and specialization, can be significantly high.

If Amazon fail to offer competitive monetary compensation, Amazon may be at risk of a higher turnover rate. A high turnover rate can negatively impact workplace morale as well as company's reputation, which may ultimately decrease customer loyalty. By increasing salary, Amazon will be able to retain its valued and marketable employees, decrease turnover, and increase employment longevity.
