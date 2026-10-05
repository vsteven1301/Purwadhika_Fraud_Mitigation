# Study Case: Fraud Mitigation

### Notice: 
The dataset used in this analysis is a dummy dataset. This dataset only mimics real business scenario. It doesn't contain actual, sensitive, and real business data. 

### About Dataset:
3 tables (User, Merchant, Transactions)

#### Fields/Variables explanation:
##### Table User:
user_id : Unique user account ID\
join_date : User account creation/joining date\
kyc_status : OVO Club (Unregistered; Not Verified with Official ID) & OVO Premier (Registered; Verified with Official ID)\
kyc_date : Verification Date (Null if not verified)\
wallet_balance: Balance as of 21 Aug 2024 (maximum balance per user is regulated by Indonesian Central Bank, for unregistered and registered user)
##### Table Merchant:
merchant_id : Unique merchant account ID\
merchant_name : Merchant name \
category : Merchant business category | Retail, Digital, F&B, Transport, None
##### Table Transactions
trx_id : Unique transaction number ID\
user_id : User ID (Foreign Key)\
merchant_id : Merchant ID (Foreign Key) | None (if P2P and transaction done through internal application)\
trx_date : Transaction date\
trx_type : Transaction type | Bill Payment, QRIS, VA Bill, Top Up, P2P (P2P can’t be used by OVO Club; unverified user)\
amount : Transaction amount

### Data Analysis Process:
This analysis is conducted to understand our data and identify if there are specific patterns that may lead to suspicious transactions which have financial impact on business. The analysis is done thoroughly for users, merchants, and transactions data. The analysis is also to answer several business questions related to regulations compliance.\
In this dataset, transaction records are captured from 20 Dec 2022 to 21 Aug 2024.

#### Data cleaning process including: 
Filling missing values\
Correcting misspelled data (inconsistencies)\
Handling outliers

#### Data validation process including:
Comparing transaction date to users joining date & KYC date (for P2P transaction type)\
Validating users’ wallet balance with regulations (fulfilled or not fulfilled)\
Validating users’ KYC status with transaction type (especially P2P transfer)\
Validating users’ monthly transaction limit (as regulated from Indonesian Central Bank)\
Validating transactions amount (transaction amount threshold is also regulated)

#### Suspicious transaction checking process:
Based on domain knowledge, certain users have tendencies to make repetitive transaction in specific merchant. After conducting analysis thoroughly; in this captured dataset, there is no enough evidence that may lead to suspicious transactions. With only low frequencies per month, this can be considered as normal transactions.\
Further analysis is needed with more records to analyze this pattern.

### Conclusion/Final Insights:
Even though there is no evidence in suspicious transaction patterns, there are several findings that can be used to enhance current system’s security and database. It has to be done to ensure good data quality in the future, thus database can be used for machine learning with minimum data cleaning process.

