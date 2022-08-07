# Electronic House
Test A/B for Electronic House web page.

![image](https://user-images.githubusercontent.com/85264359/183304111-7d3a1138-dccf-490c-8e63-6446132121b1.png)


# 1. Business Case.

Electronic House is an online commerce (e-commerce) of computer products for homes and offices. Customers can buy mice, monitors, keyboards, computers, laptops, HDMI cables, headphones, webcam cameras, among others, through an online website and receive the products in the comfort of their homes. 

The UX designers team has been working on a new sales page, with the objective of increasing the conversion rate of a store product, a keyboard bluetooth.The product manager said the current page conversion rate is 13% on average over the last year. 
The product manager's goal is to increase the conversion rate by 2%, that is, the new sales page, developed by the UX team, would be a success if its conversion rate was 15%.

The bluetooth keyboard has a sale price of R$ 4,500.00 in cash or in installments at 12% without interest on the credit card. Before switching from the old sales page to the new one, the product manager would like to test the effectiveness of the new page on a smaller group of customers, in order to take less risk of falling conversion if the new page shows a worse conversion than the current page.

# 2. Business Problem.
I have been hired as a freelancer by Electronic House to help the Designers of the new page, to validate its effectiveness in a safer way, with more confidence and rigidity in the analysis. The deliverables of your work are as follows:

a. New page conversion is actually better than page conversion current?

b. What is the potential number of sales that the new page can bring?

c. What is the total revenue from the sale of the bluetooth keyboard through the new page?

# 3. Solution Strategy

My strategy to solve this challenge was:

## `Step 00. Settings and Data Extraction`
* Import of required libraries, packages and functions.
* Loading and checking available data via a CSV file.

## `Step 01. Apply the IOT method`

* Input 

       I. Business problem + Kaggle data

* Output 

       I. A sentence saying whether page A is better than page B.
       
       II. Page sales potential
       
       III. Product revenue potential.
       
 * Task
 
       I. Experiment planning.
       II. Get the data.
       III. Check data validation.
       IV. Study the descriptive statistics of the data.
       V. Create the hypotheses. Explore the Data (Understanding Distributions)
       VII. Stipulating a test goal (2%)
       VIII. Stipulate the significance level of the test.
       IX. Define what will be the statistical test
       X. Apply the statistical test (Permutation test)
       XI. Compare the distribution of the 2 pages and see if there is a difference statistically relevant.
       XII. Deliver the result (see Output)

## `Step 02. Solution planning`
* Step 01: Choosing the method
* 1.1. Statistical hypothesis testing
  - Statistical inference method used to decide whether the data available are sufficient to support a particular hypothesis.
* 1.2. A/B testing
  - User experience research methodology that applies statistical hypothesis testing to compare two or more versions of a single variable to determine which of the two variants is more effective.
 
* Step 02: Experiment Design
* 2.1. Formulation of hypotheses:
  - Definition of the null hypothesis
  - Definition of alternative hypotheses
  - Choice of test type: One-tailed or two-tailed test (one-tailed test or two-tailed test)
  - Setting the confidence level of the experiment.
  
* 2.2. Variable choice:
  - Definition of the evaluation metric or dependent variable.

* 2.3. Separation of groups
  - Separation from the control group.
  - Separation of the treatment group.
  - Definition of the sample size of each group.

* Step 03: Collecting and preparing the data
* 3.1. Data collection:
   - Definition of the data collection and storage structure.
   - Creation of the A/B Flag.
   - Choice of A/B Testing tools.

* 3.2. Data preparation:
  - Definition of the data collection and storage structure.
  - Data cleaning and verification.
  
* 3.3. Group conversions:
  - Calculation of the control group conversion.
  - Calculation of treatment group conversion.

* Step 04: Testing the Hypotheses
* 4.1. Definition of the statistical inference method
  - t-test
  - ANOVA
  - Chi-Squared
  
* 4.2. Calculation of p-value

* Step 05: Drawing conclusions
  - Interpretation of p-value.
  - Validation of initial hypotheses.
  - Conclusion.
  - Calculation of the number of potential sales.
  - Calculation of potential revenue.

# 4. Top 3 Data Insights

**Hypothesis 01: The current landing page converts more than the new one.**

**False the convertions are the same.**

![image](https://user-images.githubusercontent.com/85264359/183305429-b4f232c5-9e20-4d7f-9d68-9624f7b2e69d.png)

**Hypothesis 02: The new land page convert more in the first 5 days.**

**FALSE the new page is converting 30 clients less than the current page in the first five days.**

- The total clients converted using the NEW PAGE in the first five days are: 3485
- The total clients converted using the CURRENT PAGE in the first five days are: 3515

**Hypothesis 03: The median converted is the same.**

**TRUE the average converted is the same.**

![image](https://user-images.githubusercontent.com/85264359/183305547-44b949e6-02bf-4919-b0cf-2f6b5a32c99a.png)


# 5. 3.1 Hypotheses Formulation

- H0: The current convertion rate is better than the new page convertion rate.
- H1: The new page convertion overcomes the current page convertion rate.


       confidence_level=0.95
       significance_level=0.05

       # page conversions 
       p1=0.13
       p2=0.15
       effect_size=sms.proportion_effectsize(p1, p2)
       statistical_power=0.80

       # sample size
       sample_n=sms.NormalIndPower().solve_power(effect_size, power=statistical_power, alpha=significance_level)
       sample_n=math.ceil(sample_n)
       sample_n = 4720

# 6. Conversion Rate
![image](https://user-images.githubusercontent.com/85264359/183305911-461b8706-d8dd-4371-93eb-770122f377a3.png)


# 7. Business Results
       df_table=df_ab[['group', 'converted']].groupby('group').agg({'converted':['sum', 'count']})
       df_table.columns=['converted','not_converted']
       df_table.head().reset_index()


       chi_val, pval_chi, dof, expected = chi2_contingency(df_table)

       print(chi_val.round(2))
       print(pval_chi.round(2))


       if pval_chi < 0.05:
           print('There is evidences to reject null hypothesis and assume the alternative - there is effect')
       else:
           print('There is no evidence to reject the hypothesis - no effect')
           
* There is no evidence to reject the hypothesis - no effect

# 8. Conclusions

# 9.Technologies

# 10. Lessons Learned

# 11. Next Steps to Improve


# Author

Djalma Luiz da Silva Junior



[<img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>](https://www.linkedin.com/in/djalmajunior07)
