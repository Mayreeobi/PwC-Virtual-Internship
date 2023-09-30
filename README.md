# PwC-Virtual-Internship
The program is divided into 3 tasks, the objective is to create a dashboard in Power BI with relevant Key Performance Indicators KPIs and provide recommendations.

## Task 1: Call Centre Trends 

### Objectives
To create a dashboard in Power BI on Call Centre Trends visualizing customer and agents’ behavior that reflects the following relevant Key Performance Indicators (KPIs) and metrics in the dataset. 
•	Overall customer satisfaction
•	Overall calls answered/abandoned
•	Calls by time
•	Average speed of answer
•	Agent’s performance quadrant -> average handle time (talk duration) vs calls answered

### The Dataset 
The data came in an excel files containing 5,000 unique rows and 10 columns. You can find the dataset ![Here](https://github.com/Mayreeobi/PwC-Virtual-Internship/blob/main/Call_Centre.xlsx)  

### Data Cleaning and Transformation
The data was load in Power Query and the following was done.
-	In the data view, I added 6 columns:
      1.	 Calls Answered =   IF(Call_record[Answered (Y/N)]="y",1,0)  
      2.	 Calls Rejected = IF(Call_record[Answered (Y/N)]="n",1,0)
      3.	 Resolved Calls = IF(Call_record[Resolved]="y",1,0)
      4.	 Unresolved Calls = IF(Call_record[Resolved]="n",1,0)
      5.	 Month Called = FORMAT(Call_record[Date],"MMMM")
      6.	 Hours Called = HOUR(Call_record[Time])
-	Lastly created a table for all my DAX Measures. The following measures was created:
      1.	   Total Calls	COUNT(Call_record[Call Id])
      2.     Avg Customer Satisfaction Rating  	AVERAGE(Call_record[Satisfaction rating])
      3.     Avg Speed of Answer	AVERAGE(Call_record[Speed of answer in seconds])

### Visualization 
![](https://github.com/Mayreeobi/PwC-Virtual-Internship/blob/main/Call_Centre.png)

You can interact with the dashboard [Here](https://app.powerbi.com/view?r=eyJrIjoiYTcwMDg3OGMtM2ZhNy00Mjg1LWE1NWItYzUwMDFhOWFkM2YyIiwidCI6ImExZGNjNGZiLTRlYzAtNGI1Ni04NDg1LTRmOTgzYzMyODY0MiJ9)

### Insights
-	Total Calls is 5,000, and it's made up of 4,054 Answered Calls and 946 Rejected calls.
-	3,646 represents Resolved calls while Unresolved is 1,354.
-	The Average Speed of Answer (seconds) is 67.52 
-	Average Customer Satisfaction Rating is 3.40
-	The Agent with the highest number of Answered calls is Jim (536 calls) while Stewart had the least answered calls 477.
-	There is a positively correlation between Total Calls Answered and Total Calls Rejected.
-	Streaming accounted for 20.44% of Total calls.
-	Across the 10 Hours Called total calls ranged from 14 to 594. Hour 13 has the highest total call at 594; which accounts for 11.88% of total calls
-	January had the highest total calls at 1,772 (35.44%) followed by February and March.
-	Total calls had a downward trend on Sunday December 31st falling by 20% in 28.80 


## TASK 2: Customer Retention

The aim in this task is to define proper KPIs, create a dashboard reflecting the defined KPIs, and make recommendations. The Dashboard was divided into 3 categories namely: Demographics; Account Details and Phone Services.

### The Dataset 
The data came in an excel files containing 7,043 unique rows and 23 columns.  You can find the dataset ![Here](https://github.com/Mayreeobi/PwC-Virtual-Internship/blob/main/Churn_Dataset.xlsx)

### Data Cleaning and Transformation
The data was load in Power Query and the following transformations was done. 
-	I add a conditional column to create the bins for customer_loyalty 
-	Converted MonthlyCharges and TotalCharges to currency.
-	Replace “No” to “Not Senior” and “Yes” to “Senior” in the SeniorCitizen column.
-	Lastly created a table for all my DAX Measures. The following measures were created:
      1.    	% of Partners	DIVIDE(CALCULATE(COUNT(Churn_record[customerID]),Churn_record[Partner]="yes"),COUNT(Churn_record[customerID]))
      2.     % Senior Citizen	DIVIDE(CALCULATE(COUNT(Churn_record[customerID]),Churn_record[SeniorCitizen]="senior"),COUNT(Churn_record[customerID]))
      3.	  Average Monthly Charges	AVERAGE(Churn_record[MonthlyCharges])
      4.	 Churn Rate	[Churned Customers]/[Total Customer]
      5.	 Churned Customer	(CALCULATE(COUNT(Churn_record[Churn]),Churn_record[Churn]="yes"))
      6.	 Total Charges	SUM(Churn_record[TotalCharges])
      7.	 Total Customer	COUNT(Churn_record[customerID])

### Visualization 
![](https://github.com/Mayreeobi/PwC-Virtual-Internship/blob/main/CustomerRetention1.png)

You can interact with the dashboard [Here](https://app.powerbi.com/view?r=eyJrIjoiNDU4NGUxNTgtZjE4Yy00YWI2LTkwYmItMmY2YmVhMzc4Yzk1IiwidCI6ImExZGNjNGZiLTRlYzAtNGI1Ni04NDg1LTRmOTgzYzMyODY0MiJ9)

### Recommendations
1.	Offer seamless payment method especially address any issue regarding the electronic check payment process.
2.	Respond to customer support queries promptly by prioritizing complaints.
3.	Offer incentives such as special offers and discounted long-term contracts instead of the month-to-month contracts. Create subscription packages with a longer duration.
4.	Ask for and act on customer's feedbacks often.
5.	Increase customer engagement by communicating and reaching out to them; and keeping them abreast with the latest or improved products through emails, chats or calls.
6.	Provide better services by providing faster internet services and investing in improving fiber optic related services.
7.	Provide excellent customer service, more emphasis and training should be provided to admin and technical support as they have the most access to customers.


## Task 3: Diversity & Inclusion

### Objectives
Calculate the following measures to help define proper KPIs:
-	Number of men
-	Number of women
-	Number of leavers
-	% employees promoted (FY21)
-	% of women promoted
-	% of hires men
-	% of hires women
-	% turnover 
-	Average performance rating: men
-	Average Performance rating: women

### The Dataset 
The data came in an excel files containing 500 unique rows and 23 columns. You can find the dataset ![Here](https://github.com/Mayreeobi/PwC-Virtual-Internship/blob/main/Diversity_Inclusion.xlsx)

### Data Cleaning and Transformation
The data was load in Power Query, the data had no duplicates, missing values or any inconsistenency  an
The following DAX measures was created:
1.     Total Employees	COUNT('Pharma Group'[Employee ID])
2.     Number of Men	CALCULATE([Total Employees],
            FILTER('PharmaGroup','PharmaGroup'[Gender] =" Male"))
3.     Number of Women=	CALCULATE([Total Employees],
                   FILTER('PharmaGroup','PharmaGroup'[Gender] = "Female"))
4.	   FY20 New Hires=	CALCULATE([Total Employees],
                FILTER('Pharma Group','Pharma Group'[New hire FY20?] = "y"))
5.	   FY20 Men Leavers=	CALCULATE([Total Employees],
                FILTER('Pharma Group','PharmaGroup'[Gender]="Male"),
       'Pharma Group'[FY20 leaver?] = "yes"))
  
7.	   FY20 Women Leavers= CALCULATE([Total Employees],
                 FILTER('Pharma Group','PharmaGroup'[Gender]="Female"), 'Pharma Group'[FY20 leaver?]="yes"))
8.	   % FY21 Promotion=	DIVIDE(CALCULATE(COUNT('Pharma Group'[Promotion in FY21?]), 'Pharma Group'[Promotion in FY21?]="yes"),  CALCULATE([Total Employees]))
9.	   % Promoted (FY20)=	DIVIDE(
                                 CALCULATE(COUNT('Pharma Group'[Promotion in FY20?]), 'Pharma Group'[Promotion in FY20?]="y"), CALCULATE([Total Employees]))
10.  	% Women FY20 Promotion=	DIVIDE(
               CALCULATE(COUNT('Pharma Group'[Promotion in FY20?]), 'Pharma Group'[Promotion in FY20?]="Y", 'Pharma Group'[Gender] = "Female"),
                CALCULATE(COUNT('Pharma Group'[Promotion in FY20?]), 'Pharma Group'[Promotion in FY20?]="Y"))
11.	    % Women FY21 Promotion=		DIVIDE(
           CALCULATE(COUNT('Pharma Group'[Promotion in FY21?]), 'Pharma Group'[Promotion in FY21?]="Yes", 'Pharma Group'[Gender] = "Female"),
             CALCULATE(COUNT('Pharma Group'[Promotion in FY21?]), 'Pharma Group'[Promotion in FY21?]="Yes"))
12.	    % Men FY21 Promoted=	DIVIDE(
                               CALCULATE(COUNT('Pharma Group'[Promotion in FY21?]), 'Pharma Group'[Promotion in FY21?]="Yes", 'Pharma Group'[Gender] = "Male"),
                                CALCULATE(COUNT('Pharma Group'[Promotion in FY21?]), 'Pharma Group'[Promotion in FY21?]="Yes"))
13. 	% Hire men=	DIVIDE(
                     CALCULATE(COUNT('Pharma Group'[New hire FY20?]),'Pharma Group'[New hire FY20?]="Y", 'Pharma Group'[Gender] = "Male"),
                      [FY20 New Hires])
14.  	% Hire Women=	DIVIDE(
                         CALCULATE(COUNT('Pharma Group'[New hire FY20?]),'Pharma Group'[New hire FY20?]="Y", 'Pharma Group'[Gender] = "Female"),
                            [FY20 New Hires])
15. 	% Turnover=	DIVIDE( [No of Leavers],
                          DIVIDE(([# of employees at start of the year] + [employees at end of year]), 2))
16.	    No of Leavers=		CALCULATE([Total Employees],
                 FILTER('Pharma Group','Pharma Group'[FY20 leaver?]="Yes"))
17.	    Employees at end of year=	Calculate(distinctcount('Pharma Group'[Employee ID]),Filter('Pharma Group',NOT('Pharma Group'[Department @01.07.2020]=BLANK()) ))

18.	    Number of Employees at start of the year=	CALCULATE([Total Employees],'Pharma Group'[In base group for turnover FY20] = "Y")

### Visualization
![](https://github.com/Mayreeobi/PwC-Virtual-Internship/blob/main/Diversity1.png)

Find the interactive dashboard [Here](https://app.powerbi.com/view?r=eyJrIjoiNzYyODAwOGEtODc5My00YTJiLThmOTYtNjAyM2YxNGEwODA3IiwidCI6ImExZGNjNGZiLTRlYzAtNGI1Ni04NDg1LTRmOTgzYzMyODY0MiJ9)

### Insights 
The aftermath of the COVID-19 pandemic led to economic recession and thus leading to a decline in hiring. In 2020, women accounted for 51.5% of the new hires and young employees in the age group of 20 - 29 were hired the most. 
There was a huge promotion gap in 2021, as more men (64.7%) were promoted and only 6 nationals were promoted out of the 21 nationals’ employees in the organization. Sweden Nationals had the highest promotion followed by Spain and the least was German. 
The average performance rating for both genders is almost the same; Part-time employees had a higher rating of 2.52% when compared to the full-time employees.

### Recommendations 
-	Mentorship programs should be introduced, as this will reduce the turnover rate. 
-	Promoting qualified women and employee from different nationality can reduce the promotion gaps that already exists. 
-	Employee feedback should be encouraged through survey to ask about the level of diversity and inclusiveness in the organization.
-	More training programs should be organized to boost performance, job satisfaction and lower the turnover rate.

### Thank you for your time. Cheers
