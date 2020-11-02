# Fraud-Transaction-Exploratory-Data-Analysis-and-Machine-Learning-Modeling-To-Predict-Fraud-Transaction:
Exploratory data analysis on fraud transaction and machine learning modeling
dataset could be found right  [here](
https://www.kaggle.com/ntnu-testimon/paysim1) : 


## Background information 

banking has been around since long time according to World banks the oldest bank started around before 8000 BC, as of today more and more people use the banking system to do transaction, save money, and etc. However as more people use the banking system there are more fraud cases in the banking system, according to https://www.statista.com/statistics/872716/uk-issued-credit-and-debit-cards-number-of-fraud-cases/, the number of fraud cases goes up year by year.

In this notebook, we're doing an exploratory data analysis on fraud bank cases, and trying to predict fraud bank cases using machine learning based on the dataset that's available in kaggle, link coudld be found above

## Problem Statement 

millions of bank transaction happened everyday, especially as digital banking getting more and more popular  since around 2010, having an access to banking never been closer, however as the access to banking getting closer to the customers, access to banking also been closer to the criminals (people who commited fraud in this case). As the banking is getting more and more accessible the number of fraud cases also getting higher and higher in each year. Fraud cases is not just hurting customers it also hurt the bank in general as the trust inflicted financial loss to the bank, the fraud cases also inflicted a trust loss to the bank.


## Goals 


The goals of this notebook is to findout what are the pattern of fraudulent transaction our dataset by doing an exploratory data analysis, and after we done with exploratory data analysis we're going to create machine learning modeling that will be able to predict fraud transaction


## Business Question: 

- What are the type of fraud transaction in the dataset ?
- how we differentiate a regular transaction from fraud transaction ? 
- when does fraud transaction usually happened ? 
- what is the best machine learning modeling for handling this fraud case ? 


## Workflow : 

- data cleaning : 
  - Binning data (turning step column from monthly hour into daily hour)
  
  
- Exploratory data analysis to answer business question 

- Feature engineering & feature selection for machine learning process 
  - Encoding all the object column into int value using one hot encoding
  - Checking correlation between dependent and independent variable, and dependent variable with another dependent variable
  - Feature Selection based on correlation and EDA findings 
  
- Model building 
  - Train test split
  - Using smote technique to hande imbalance data on the target column
  - Creating base model wit few machine learning algortihm ( Logistic Regression, KNeighbors Classifier, and Decision Tree)
  - Check evaluation matrix 
  - Scalling for Llogistic Regression and KNeighbors classifier
  - comparing evaluation matrix before and after scalling
  - Hyperparameter tuning on best performing model
  - checking evaluation matrix on tuned model 
  
  
  
<details>
  <summary><h2> Tl;dr (Summary)</h2></summary>
  
  <details>
    <summary><h2> Exploratory Data Analysis (Summary)</h2></summary>
  
 ## EDA Conclusion, Recommendation, and Future Improvement


### Conclusion

- There are **5 types** of transaction for non fraud transaction **(Debit, Payment, Cashout, Cashin, Transfer)**
- For fraud transaction there are only **2 types** of transaction  (**Cashout, Transfer)**
- Fraud transaction has a higher median amount compared to non fraud transaction, High amount **cashout / transfer** are types that should be watched of fraud activity
- is flagged fraud method seems doesn't work to handle fraud cases since it only can predict **16 out of 8213 fraud cases (0.02%)** of fraud cases

- **8034 out of 8213 fraud (98%) cases** emptied their bank account 


- Some fraud transaction are able to do cashout / transfer **more than their original balance**

- Some fraud transaction are able to do cashout / transfer **When the original balance is 0**


- there's no fraud transaction from **merchant to customer or customer to merchant only customer to customer**

- there are destination account that has been in **multiple fraud cases**

- the median value of fraud transaction doesn' have any correlation with the number of transaction of fraud transaction 

- or non fraud the median amount of transaction is somehow correlated with the number of transaction



### Recommendation


- Watch out for user that has a **high amount of transfer / cashout**. since fraud transaction has a higher median value compared to the non fraud transaction, all high amount transfer / cashout should be watched closely


- Watch out for customer **who empltied their bank account** 98% of user who's involed in fraud transaction emptied their bank account in a single transaction, bank should be aware watch stop user / have an automated system to stop from someone drawing / transfering an entire bank account in a single transfer



- Use **Machine Learning to predict Fraud**, the bank already implemented a system isflaggedfraud to flagging a fraud activity, however the system failed miserablely and it only able to predict **(0.02%)** out of the entire of fraud transaction, hence using a machine learning that's focus on the recall score could help the bank to predict a fraud activity



### Future Improvement for the notebook


- **there're 2% of fraud activity that did not empty their bank account**, findout the pattern of the fraud transaction that did not emptied their bank account



- **Try Using Sampling** as the data get bigger and bigger EDA could be done using a sampling method since it's resourcefully expensive to explore millions of data as the data transaction get bigger 




- **Getting date from step** our analysis we turn the step from monthly hour into daily hour, in the future step could be turned into date and daily our and from that would could understand better how a fraud transaction affected by date
  </details>
  

  <details>
    <summary><h2> Machine Learning (Summary)</h2></summary>
    
## Machine Learning Conclusion, & Future Improvement


### Conclusion

- **Logistic Regression has the best recall score among all algorithm that we tried in this notebook**
    - Among all the algorithm in this notebook that we tried (Logistic Regression, KNN, and Decision Tree) Logistic regression has the best recall score **(98.7%)**
    

- **Scalling doesn't effect much on Logistic Regression for this case**
    - This dataset has a big range, for certain coulumns, like step compared to all the balance columns, and usually how we tackle this is using scalling, however after scalling process our evaluation matrix did not get any better **(For Logistic Regression Case)**, for KNN it seems to improve the evaluation matrix of the algorithm
    

### Future Improvement

- **Use The Entire Population for machine learning process** 

For this machine learning process this notebook used a stratifed sampled data from the fraud and non fraud group, this notebook only contain 10% of data out of the entire population, for future improvement, for machine learning process we could use an entire dataset for machine learning process, as we know the more the data the better the model is


- **Tryout Different Algorithm**


for this machine learning process this notebook use 3 different kind of algorithm (*Logistic Regression*, *KNeighborClassifier*, and *DecisionTreeClassifier*), in the future we could use different kind of classification and compared with the 3 algorithm that we use


- **Hyperparameter Tuning For all algorithm**


due to the computational power of local laptop, this notebook only have 1 hyperparameter tuning which is *Logistic Regression*, for future imporovement we could do hyperparameter tuning in all algortihm
 </details> 
</details>



<details>
  <summary><h2> Notebook Highlight </h2></summary>
 
 ## Finding Pattern in Fraud Transaction
 
 
 ### 1. Types of Transaction 
 
 
  ![image](https://user-images.githubusercontent.com/57277832/97878556-5cb73880-1d51-11eb-8516-f05ec13859f2.png)

  
the graph above is comparison of fraud transaction and non fraud transaction, we can see clearly that in the **fraud transaction there're only 2 types of transaction** while in the *non-fraud transaction* there're 5 types of transaction, this is one of the way way diffrentiating a fraud transaction and non fraud transaction pattern 
  

### 2. Median Amount of Transaction


![image](https://user-images.githubusercontent.com/57277832/97879526-ac4a3400-1d52-11eb-898d-3796049df446.png)


we can already see a difference of fraud transaction and non fraud transaction by looking at the median amount, we use median amount here because of there are many outliers in the amount column. 


**The median amount of transfer and cashout fraud transaction are similar around 400.000**, and for non fraud transaction the median amount for **cash out transaction is lower than 200.000, (somewhere around 140.000 - 150.000)**, we can clearly see here that a cashout transaction above **200.000 needs to be watched**.


For transfer type transaction it's somewhat harder to differentiate fraud transaction and non fraud transaction since the median amount of non fraud transaction is higher compared to fraud


### 3. Number of Transaction and Median Amount


![image](https://user-images.githubusercontent.com/57277832/97881322-d56bc400-1d54-11eb-92eb-c880981ab02f.png)


we see that fraud transaction is counstant throughout the day **it ranges around 250 to 370 fraud transaction each hour in one month**, for the non fraud transaction there are **rarely any transaction before 9am**. 


However it's kind of hard to compare it side by side with pure number since the difference in numbers of transaction is large, in graph below we will compare it side by side using percentage of total transaction

### 3.1 Percentage of Fraud and Non Fraud Transaction


![image](https://user-images.githubusercontent.com/57277832/97883197-2086d680-1d57-11eb-8831-1c7866291a94.png)


now the barchart is in percentage we can clearly see both of the transaction, don't get mislead by this bar, because this is a percentage of transaction not the total number of transaction.


### 3.2 Median Transaction Amount per Hour for Fraud and Non Fraud Transaction


#### 3.2.1 median Transaction Amount per Hour for Fraud Transaction
![image](https://user-images.githubusercontent.com/57277832/97885245-b1f74800-1d59-11eb-85cf-8636a9b1abd1.png)


The chart above is the percentage of total fraud transaction per hour and the median amount of transaction, on **y axis on the left side (bar chart)** that's the percentage number of transaction while the **y axis on the right side (line Graph)** is the median amount of transaction.


The highest median amount for the fraud transaction happened at around **3 am** with the median value of more than **700.000**, and the median amount of fraud transaction is very fluctuative, and it seems like it doesn't have any correlation by the percentage of transaction


#### 3.2.2 Median Transaction Amount for Non Fraud Transaction


![image](https://user-images.githubusercontent.com/57277832/97886069-bbcd7b00-1d5a-11eb-9049-342ea785e589.png)


the chart above is similar like the fraud transaction the difference is just that this is the char of percentage of non fraud transaction and it's median amount of transaction per hour 


For non fraud transaction the highest median amount happened **during 13.00 at around 90.000**, and for non fraud transaction the **median amount of transaction is somehow correlated with the number of transaction**, as we can see that the median amount start to goes up as the number transaction goes up and it start to goes down as the number of transaction went down 


**The pattern that we can learn from here is a transaction of transfer and cashout and with high amount that's happening before 9am should be watched** since we see it from the chart that the median amount of non fraud transaction that happened before 9am is around 10.000 - 20.000, **any transaction transfer or cashout transaction that has an abnormal amount during that hour should be watched**


### 4. What is The Best Machine Learning Model for Predicting Fraud Transaction


![image](https://user-images.githubusercontent.com/57277832/97887882-0ea83200-1d5d-11eb-861a-b2389da4d81a.png)


The table above is evaluation matrix of Base model machine learning and the scaled version of Logistic Regression and KNeighbor Classifier, we are going to focus on the **recall score** here because of we want to minimize the number of **False Negative (Actually Fraud but the model predict not a fraud)**.


Not scaled logistic regression has the best recall score among all model, it actually correctly predict **162 out of 164 Fraud Transaction**, however after a hyperparameter tuning the recall score stays the same for logistic regression, so in conclusion logistic regression perform the best when it comes to predict a fraud transaction from learning from this dataset



</details>
