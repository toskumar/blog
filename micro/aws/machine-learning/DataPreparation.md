# Data Preparation

Data preparation is the process of transforming a data set using different techniques to prepare it for model training and testing. Changing our dataset so it is ready for Machine Learning.

### Categorical Encoding

Categorical Encoding is a process of manipulating categorical variables when ML algorithm expect numerical values as inputs. Changing category values in our dataset to numbers. Example of Categorical encoding 
  * Color {green, purple, blue} - Nominal means order does not matter
  * Evil {true, false} - Nominal means order does not matter
  * Size {L > M > S} - - Ordinal means order does matter

* Encoding Categorical Features to predict a loan will be approved or not
  | ID | Type | Bedrooms | Area | Pool Size | Price | Loan Approved |
  | --- | --- |  --- | --- | --- | --- | --- | 
  | 1 | condo    | 2 | 2345 | S | 250230 | N |
  | 2 | house    | 4 | 3100 | L | 243679 | Y |
  | 3 | apartment| 2 | 1250 | M | 120300 | Y |
  | 4 | house    | 4 | 2250 | N | 220300 | N |
  * No need to encode Bedrooms, Area and Price as they are numerical values
  * Loan Approved (Categorical Nominal) is our target attributes and encode as N -> 0 and Y -> 1
  * Pool size (Categorical Ordinal) is an Ordinal values N -> 0, S-> 5, L -> 10, M -> 7
  * House type(Categorical Nominal) is a nominal value and need to use some encoding technique like one-hot encoding condo -> 1-0-0 (CondoType, HouseType, ApartmentType)
  * One hot encoding - Transforms nominal categorical features and creates new binary column  for each observation. Adding a column to your dataset of 1 or 0




