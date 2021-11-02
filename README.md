# HR Analytics 

![enter image description here](https://github.com/amar-chakka/HR-Analytics/blob/47eda9752aae42d13745fb7d1526acfe5d132aa6/HR%20Image1.png?raw=true)


### The HR department has hired me as data science consultants. They want to supplement their exit interviews with a more proactive approach.

HR Department at a software company  want to try a new initiative to retain employees. The idea is to use data to predict whether an employee is likely to leave. Once these employees are identified, HR can be more proactive in reaching out to them before it's too late. They only want to deal with the data that is related to permanent employees.

The Business Intelligence Analysts of the Company provided  three datasets that contain information about past employees and their status (still employed or already left).

## department_data

This dataset contains information about each department. The schema of the dataset is as follows:

### dept_id – Unique Department Code

### dept_name – Name of the Department

### dept_head – Name of the Head of the Department

# employee_details_data

This dataset consists of Employee ID, their Age, Gender and Marital Status. The schema of this dataset is as follows:

### employee_id – Unique ID Number for each employee

### age – Age of the employee

### gender – Gender of the employee

### marital_status – Marital Status of the employee

## employee_data

This dataset consists of each employee’s Administrative Information, Workload Information, Mutual Evaluation Information and Status.

## Target variable

### status – Current employment status (Employed / Left).

## EDA 
employee_id:

1.  No Null values
2.  No 0 values
3.  Valid Data type

age:

1.  No Null values
2.  No 0 Values
3.  Valid Data type

gender:

1.  No Null values
2.  Valid entries
3.  Valid Data type

marital_status:

1.  No Null values
2.  Valid entries
3.  Valid Data type

avg_monthly_hrs:

1.  data type is object, it should be converted to float type.
2.  No Null values

department:

1.  706 Null entries
2.  Valid data type
3.  "-IT" to be replaced with "D00-IT" for 207 rows
4.  Missing values are nearly 5% so we cant drop those many rows. Either fill with Mode or KNN imputer

filed_complaint:

1.  2041 non-null values
2.  type = object
3.  Assuming that for employees who ever filed complaints were assigned value of 1
4.  Possibly there are no complaints filed by other employees so can be filled with 0

last_evaluation: Score for most recent evaluation of employee (higher is better)

1.  12629 non-null
2.  type = float64
3.  Missing values could be 0 or there is no evaluation done yet
4.  We filled it with median value

n_projects :

1.  14116 non-null entries
2.  type is int64
3.  No null values
4.  Values ranges from 1 to 7, where there are more people with 3 or 4 projects

recently_promoted :

1.  297 non-null entries
2.  type = float64
3.  Assuming that employees who ever was recently promoted were assigned value = 1.00
4.  Missing values could be 0 as not recently promoted

salary :

1.  14116 non-null entries
2.  type = object as this is a category variable
3.  No null values
4.  Nearly 8% of employees are with high salary from the merged dataframe.

satisfaction : Score for employee’s satisfaction with the company (higher is better)

1.  13966 non-null
2.  type = float64
3.  150 null values in this column
4.  Missing values could be "not satisfied" or "no information". Those missing values can be filled with "median" score as its around 1% .
5.  On a 5 point scale, taking 40% as threshold there are 19.23% of employees not satisfied.
6.  We filled it with median value

tenure : Number of years at the company

1.  13966 non-null entries
2.  type = object
3.  150 null values in this column
4.  Missing values could be "not satisfied" or "no information". Those missing values can be filled with "median/mean" score as its around 1% .
5.  Its an ordinal variable so can be converted to int or float

status : Target variable

1.  2 categories Employed , Left
2.  No null values

Using scikit-learn's train_test_split function to split the dataset into train and test sets. 80% of the data will be in the train set and 20% in the test set, as specified by test_size=0.2
Tried with different classifiers with all one hot encoded columns & selective features  over sampled data.

LogisticRegression 
RandomForestClassifier
DecisionTreeClassifier

Built ensemble model with different classifiers. Measured accuracy_score, roc_auc_score & f1_score for each model for evaluation.
Did the same with different feature set and measured the same metrics.

**Observations:**
roc_auc_scores are : 
LogisticRegression 0.8133010951342978 
RandomForestClassifier 0.9925550110994745 
DecisionTreeClassifier 0.9634689889614394 
VotingClassifier 0.9881266426841416*

F1 scores are : 
LogisticRegression 0.4427767354596623 
RandomForestClassifier 0.9564553093964858 
DecisionTreeClassifier 0.9408284023668638 
VotingClassifier 0.9525959367945824

Selecting the model with highest f1_score > Random Forest classifier with 95.64 % 





To check out my notebook, please click [here](https://github.com/amar-chakka/HR-Analytics/blob/75f073bd4808a1d40835b481c7973527b767623d/1005_GCD_Capstone_Project.ipynb).
