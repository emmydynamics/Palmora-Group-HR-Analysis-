# Palmora Group HR Analysis

### 1. **Project Overview**

The Palmoria Group, a manufacturing company based in Nigeria, is embroiled in issues 
bordering on gender inequality in its 3 regions. Unfortunately, the media recently 
published the news with the headline “Palmoria, the Manufacturing Patriarchy”.

Thisdoesn’t look good for the owners of the business, based on their ambition to scale the 
business to other regions and even overseas. Cases like this can only spiral downwards, 
revealing other issues like the gender pay gap, amongst other possible issues. 
The CEO of Palmoria, Mr Ayodeji Chukwuma, is keen to address these issues before they 
get out of hand.

The CHRO, Mr Yunus Shofoluwe, has been assigned the task to identify 
key areas within the business that could give rise to issues and address them immediately. 
Mr Shofoluwe decided to recruit you as an HR Analytics expert to analyse the company’s 
HR data and come up with recommendations for management’s attention. “Now, the 
future of gender equality in Palmoria lies in your hands” – the exact words of Mr 
Shofoluwe before he handed the data to you. 

#### CASE SCENARIO
●  Analyse the company data and generate insights that the Palmoria management 
team would need to address 

● Your analysis should be visualised using appropriate charts 

● Your focus should be on gender-related issues within the organization and its 
regions 

● The insights required are based on your discretion. However, Mr Gamma, as an 
insider, has offered to give you pointers on areas you need to pay attention to  
Required: 

● Generally, there are two genders in the organization. However, some employees 
refused to disclose their gender. You would need to assign a generic gender status 
to these employees 

● Some employees are without a salary because they are no longer with the company. 
You will need to take those employees out 

● Lastly, some departments are indicated as “NULL”. These departments would also 
need to be taken out. 

#### Pointers from Mr Gamma
1. What is the gender distribution in the organization? Distil to regions and 
departments 
2. Show insights on ratings based on gender 
3. Analyse the company’s salary structure. Identify if there is a gender pay gap. If 
there is, identify the department and regions that should be the focus of 
management 
4. A recent regulation was adopted which requires manufacturing companies to pay 
employees a minimum of $90,000 

● Does Palmoria meet this requirement? 

● Show the pay distribution of employees grouped by a band of $10,000. For example: 

● How many employees fall into a band of $10,000 – $20,000, $20,000 – $30,000, 
etc.? 

● Also visualize this by regions 
Case Questions 

5. Mr Gamma thought to himself that since you were already working on the employee 
data, you could help out with allocating the annual bonus pay to employees based on the 
performance rating. He handed you another data set that contains rules for making bonus 
payments and asked you to: 

●  Calculate the amount to be paid as a bonus to individual employees 

●  Calculate the total amount to be paid to individual employees (salary inclusive of 
bonus) 

● Total amount to be paid out per region and company-wide 


### 2. Data Description

Palmora Group Data

| Column Name | Description        | Data Type |
| ----------- | ------------------ | --------- |
| `Name`      | Employee Names     | Text      |
| `Gender`    | Employee sex       | Text      |
| `Department`| Employee Team      | Text      |
| `Salary`    | Employee pay       | Numeric   |
| `Location`  | Branch location    | Text      |
| `Rating`    |Employee Performance| Text      |
 

Bonus Rules

| Column Name | Description        | Data Type |
| ----------- | ------------------ | --------- |
| `Department`| Employee team      | Text      |
| `Very poor` | Employee Bonus     | Numeric   |
| `Poor`      | Employee Bonus     | Numeric   |
| `Average`   | Employee Bonus     | Numeric   |
| `Good`      | Employee Bonus     | Numeric   |
| `Very Good` |Employee Bonus      | Numeric   |

### 3. Data Cleaning

● Generally, there are two genders in the organization. However, some employees 
refused to disclose their gender. To achieve this i assigned "Not Specefied" to the Null values 
in the gender column.

● Some employees are without a salary because they are no longer with the company. 
You will need to take those employees out. To achive this i had to transform the dataset and remove the Null values in the name column.

● Lastly, some departments are indicated as “NULL”. These departments would also 
need to be taken out. i also taked out department with null use same process above.


### 4. Data Analysis Steps

1. What is the gender distribution in the organization? Distil to regions and 
departments: Kaduna has the highest male representation (172), while the female count also peaks there at 151. Abuja shows a perfect gender balance equal numbers of male and female names. Lagos has nearly equal gender distribution, with a slight edge to males

2. Distribution by department

•   Every department includes a small number of entries where gender isn't specified.

•    Female representation is quite stable across departments (all near 30).

•    Males are most represented in Support, and are also ahead in Sales.

•   Training is equally balanced between male and female.

2. male are more rated average than female
On the good rating female are rated good more than male
On the poor rating men are rated more 
On the very good female are rated more while men less
On the very poor male are rated more 
NOTE: According to the chart most employee are rated average 

3. Analyse the company’s salary structure. Identify if there is a gender pay gap. If there is, identify the department and regions that should be the focus of management.
To deploy this question I made use of the formula below
```
Gender Pay Gap % = 
VAR MaleAvg = CALCULATE(AVERAGE('Palmoria Group emp-data'[Salary]), 'Palmoria Group emp-data'[Gender] = "Male")
VAR FemaleAvg = CALCULATE(AVERAGE('Palmoria Group emp-data'[Salary]), 'Palmoria Group emp-data'[Gender] = "Female")
RETURN 
IF(
    ISBLANK(FemaleAvg), 
    BLANK(), 
    DIVIDE(MaleAvg - FemaleAvg, MaleAvg, 0)
)

```
Note that when out put is “+” the salary favour men while “-“ indicate female
Click to view table check from the palmoria document.

Viewing from the table it show that from each regions male were more favoured than female this signify gender inequality especially from Abuja.

Department in regions with extreme pay gap that should be focused on by the management 
-	Abuja pay gap:
The pay gap favor the male with 30% from Human resources
Then 24% in favor of the female from Marketing department  
Then 20% in favor of the male from the Accounting department
Lastly Research and development  department with 12% in favor to the female

-	Kaduna pay gap: 
This shows that the females are favored more in the Engineering Department with 48%,
Then secondly from the Business Development the male are more favored with 20%,
Then in Accounting department and legal department the female are favor with 11% and while for male in legal department are favored more with 11%,
Lastly the marketing department and support department both favored the male.

-	Lagos pay gap 
This shows that the female are favored more in Marketing department with 18%,
Then in Training department the female are favored more with 16%,
Follow by the Research and Development with male been favored with 15%,
Lastly Sale department with 13% more than the female.


4. A recent regulation was adopted which requires manufacturing companies to pay employees a minimum of $90,000 does Palmoria meet this requirement:
NO, palmoria does not meet this requirement. From the chart most of the employee salary fall between $20K to $80K.

5. - Amount to be paid as a bonus to individual employees: $2.03Million
    - total amount to be paid to individual employees salary inclusive of bonus: [Palmoria Group Bonus.xlsx](https://github.com/user-attachments/files/21209070/Palmoria.Group.Bonus.xlsx)

    - Total amount to be paid out per region and company wide: $66.56Million


### 5. Dashboard

<img width="888" height="493" alt="final" src="https://github.com/user-attachments/assets/1539a9f6-6694-4716-bf0b-5364bc2301c8" />


## LINK TO SECOND PROJECT 
https://github.com/emmydynamics/Kultra-Mega-Stores-Inventory-EDA-with-SQL






















