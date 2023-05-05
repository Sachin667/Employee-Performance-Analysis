# Employee-Performance-Analysis
 Employee Performance Analysis-IABAC
INX Future Inc Employee Performance - Project
INX Future Inc , (referred as INX ) , is one of the leading data analytics and automation solutions provider 
with over 15 years of global business presence. INX is consistently rated as top 20 best employers past 5 
years. INX human resource policies are considered as employee friendly and widely perceived as best 
practices in the industry.
Recent years, the employee performance indexes are not healthy and this is becoming a growing 
concerns among the top management. There has been increased escalations on service delivery and 
client satisfaction levels came down by 8 percentage points.
CEO, Mr. Brain, knows the issues but concerned to take any actions in penalizing non-performing 
employees as this would affect the employee morale of all the employees in general and may further 
reduce the performance. Also, the market perception best employer and thereby attracting best talents 
to join the company.
Mr. Brain decided to initiate a data science project , which analyses the current employee data and find 
the core underlying causes of this performance issues. Mr. Brain, being a data scientist himself, expects 
the findings of this project will help him to take right course of actions. He also expects a clear indicators 
of non performing employees, so that any penalization of non-performing employee, if required, may 
not significantly affect other employee morals.

The following insights are expected from this project.
1. Department wise performances

2. Top 3 Important Factors effecting employee performance

3. A trained model which can predict the employee performance based on factors as inputs. This 
will be used to hire employees

4. Recommendations to improve the employee performance based on insights from analysis.
5. 
 **Feature Analysis**

 * **EmpNumber**-Unique ID number of employee
 * **Age** - Age of the employee                          
 * **Gender** - Gender of the employee                       
 * **EducationBackground** - Educatiocation background of the employee         
 * **MaritalStatus** - Married,unmarries or divorced                 
 * **EmpDepartment** - The department of the employeee                
 * **EmpJobRole**-Job role of the employee(Sales executive,Developer etc)                    
 * **BusinessTravelFrequency** - If business travelling there,how frequent it is ?      
 * **DistanceFromHome** - Distance of employee home to company              
 * **EmpEducationLevel** -Education level means is highest education level of the employee             
 * **EmpEnvironmentSatisfaction** - Working environmrent Satisfaction rating of employees     
 * **EmpHourlyRate**-Hourly rate he is receiving                 
 * **EmpJobInvolvement** - Involment in job in a scale of 4             
 * **EmpJobLevel**  - Job level of employees in a scale of 4                
 * **EmpJobSatisfaction**- Satisfaction of employees in thier job
 * **numCompaniesWorked** - Number of company worked previously            
 * **OverTime** - Overtime is there or not??                      
 * **EmpLastSalaryHikePercent** - Last salary hike percentage of employees      
 * **EmpRelationshipSatisfaction** - Satisfaction with employer relationship in scale of 4 
 * **TotalWorkExperienceInYears** - Total work experience in years    
 * **TrainingTimesLastYear** - No of trainings attented last year         
 * **EmpWorkLifeBalance** - Worklife balance of employees in a ring of 4            
 * **ExperienceYearsAtThisCompany** -No of years experienccce in the current company  
 * **ExperienceYearsInCurrentRole** - No of years experienccce in the currentjob role  
 * **YearsSinceLastPromotion** - Last promtion year of employees     
 * **YearsWithCurrManager** -No of years with the current manager          
 * **Attrition** - employee left the company or not                   
 * **PerformanceRating** -Target column is Performance rating of the employees (2-low,3-Good,4-High)   

### PROJECT SUMMARY
## EDA
* For Univariate and Bivariate analysis **Seaborn,Matplotlib** libraries are used.. 
 * Pie chats
 * histogram
 * boxplots
 * barcharts
 * countplots 
 
 These are mainly used for visual representation of data ..
 
 * The data contains 1200 rows and 28 columns
* **Numerical columns** -Age,Distance From Home,Employee Hourly Rate,Num Companie sWorked,Emp Last Salary Hike Percent,
Total Work Experience In Years,Experience Years At This Company,Training Times Last Year,Experience Years in Current Role,
Years Since Last Promotion,Years With Current Manager
* **Categorical columns** - Gender, Education Background,Marital StatusEmp Education Level,Emp Environment Satisfaction,
Emp Job Involvement, Emp Department, Emp Job Role, Business Travel Frequency,Emp JobLevel,Emp Job Satisfaction,OverTime',
 Emp Relationship Satisfaction,Emp Work Life Balance,Attrition
 
* While checking descriptive statistical details it indicates maximum value of most of the numerical columns are
far away from its Mean and Median
* There are many categorical columns are there... Most of the numerical columns are positively skewed distributions..
* There is no constant columns(std=0)

##  Data processing 
* Basic Checks - No null values
* Conversion of Categorical Data: Handeled categorical by using  mannual encoding,one hot ending and Label encoding
* For outlier treatment  **Median imputation** and **Quantile based flooring & capping** – (In this technique, the outliers        are capped at a certain value above 90th percentile or floored at a factor below the 10th percentile) are used..Most of          outliers are handled by imputing medians
* **Numerical features are selected by using pearson correlation** heatmap..But there are no highly correlated features  are not there
  * The experience in the current role and years with manager are having the higher correlation with each other.
  * Experience years at this company and years with manager also have a good positive correlation.
  * Experience years at this company and The experience in the current role also have a good positive correlation
      
* For **categorical feature selection** i adopted **chi square test** and p value..Except job satisfaction column,Features           with  higher p value gets removed..From the data analysis it is clealry visible that job satisfaction is an                    important feature.. When company wants to find its employee performance ,this feature should definetly consider..
    Columns with low chi square score
    * Gender,Business Trave Frequency,Education Background,Emp Education Level,Emp Job Involvement,
         Emp Relationship Satisfaction,marital Status,Attrition
     
* check for duplicates - no duplicate rows
    
 * **Data Normalization**-
 
**Min Max scaler** - Min Max scaler is sclaing technique that scales all the data features in the range [0, 1]. Values of columns have years,kilometers,hourly rate etc..,values of these columns are different numeric figures....**MinMaxScaler preserves the shape of the original distribution**,it doesn’t meaningfully change the information embedded in the original data.Most of the columns are poitively skewed even after outlier treatment,the data set is small and treating outliers to a certain extend may leads to change in the total behaviour and pattern
      
      
 * **Data Balancing** - 
 
**SMOTE()** - It is an oversampling technique aims to balance class distribution by randomly increasing minority class examples by replicating them.Our data is highly imbalanced (72% :17% :11%) and any model without balancing would be a dump model..For balancing the data i used SMOTE() oversampling technique...
