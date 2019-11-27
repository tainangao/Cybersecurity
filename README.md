# Cybersecurity

If the Jupyter Notebook doesn't load properly, please **[click here](https://nbviewer.jupyter.org/github/tainangao/Cybersecurity/blob/master/Copy_of_WEEK_3_FRAUD.ipynb) to view the notebook.**


In this project I'll be working on the Kaggle competition [IEEE-CIS Fraud Detection](https://www.kaggle.com/c/ieee-fraud-detection). I'll predict the probability that an online transaction is fraudulent, as denoted by the binary target `isFraud`, using **XGBoost**.

The analysis is brokendown into two parts EDA and Machine Learning. 
1. In the EDA part, I'll explore the distribution of target and its relationship with transaction amount and categorical variables. In addition, I'll also examine the distribution of fraud transactions by datetime. 
2. In the machine learning part, I'll first use **PCA** to fit-transform the 339 V columns into 50 components and then employ **XGBoost** to predict the probability that an online transaction is fraudulent. As required by the competition, ROC AUC score will be used to examine the accuracy. As the class is highly imbalanced, I'll also provide a Percision-recall curve. 





## Data
The data is broken into two files identity and transaction, which are joined by TransactionID. Not all transactions have corresponding identity information.

### Transaction Table
- TransactionDT: timedelta from a given reference datetime (not an actual timestamp)
- TransactionAMT: transaction payment amount in USD
- ProductCD: product code, the product for each transaction
- card1 - card6: payment card information, such as card type, card category, issue bank, country, etc.
- addr: address
- dist: distance
- P_ and (R__) emaildomain: purchaser and recipient email domain
- C1-C14: counting, such as how many addresses are found to be associated with the payment card, etc. The actual meaning is masked.
- D1-D15: timedelta, such as days between previous transaction, etc.
- M1-M9: match, such as names on card and address, etc.
- Vxxx: Vesta engineered rich features, including ranking, counting, and other entity relations.

**Categorical Features:**
- ProductCD
- card1 - card6
- addr1, addr2
- Pemaildomain Remaildomain
- M1 - M9

### Identity Table
Variables in this table are identity information – network connection information (IP, ISP, Proxy, etc) and digital signature (UA/browser/os/version, etc) associated with transactions. 
They're collected by Vesta’s fraud protection system and digital security partners.
(The field names are masked and pairwise dictionary will not be provided for privacy protection and contract agreement)

**Categorical Features:**
- DeviceType
- DeviceInfo
- id12 - id38

