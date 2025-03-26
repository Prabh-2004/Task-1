# Task 1 (Titanic Dataset Classification)
## Description
This Dataset contains information of 891 passengers who Boarded the Titanic ship and predicts if the passenger survived or not. The Dataset contains Missing Values and Outliers in some of its Variables(out of 12) and needs to be Cleaned and Encoded before any kind of Analysis.
<br>

**There are 12 Variables in the Dataset ->**
1) **PassengerId** - Represents every Passenger uniquely with a Number.
    - DataType : int64
    - Null Values: 0
2) **PClass** -  Pclass categorizes the Passengers on the Basis of there Ticket class, i.e, First class, second class and Third class.
    - DataType : int64
    - Null Values: 0
3) **Name** - Name of the Passenger. Unique for every record in the Dataset.
    - DataType : object
    - Null Values : 0
4) **Sex** - Represents the Gender of the Person (Male or Female).
    - Datatype : object
    - Null Values : 0
5) **Age** - Age of the Passenger.
    - Datatype : float64
    - Null Values : 177
6) **SibSp** - SibSp is the Number of Sibling(s) or Spouse(s) of the Passenger Onboard.
    - Datatype : int64
    - Null Values : 0
7) **Parch** - Parch represents the Number of Parent(s) or Children.
    - Datatype : int64
    - Null Values : 0
8) **Ticket** - This variable is the Unique Ticket Number of every passenger.
    - Datatype : object
    - Null Values : o
9) **Fare** - Fare of each Passenger according to their Passenger Class.
    - Datatype : float64
    - Null Values : 0
10) **Cabin** - The Number of cabin of each passenger.
    - Datatype : object
    - Null Values : 687
11) **Embarked** - Port of Embarkation:C = Cherbourg, Q = Queenstown, S = Southampton
    - Datatype : object
    - Null Values : 2
12) **Survived(Target)** - The Target variable with 0(Survived) and 1(Did not survive) values.
    - Datatype : int64
    - Null Values : 0

## Exploratory Data Analysis
**Data Cleaning ->**
- The dataset had no duplicated values but had 177 missing values in the 'Age' attribute which were Imputed using the `SimpleImputer()` class from `sklearn` library. Since the 'Cabin attribute was not significant for the analysis, it was not cleaned.
- The 'Age' and 'Fare' variables had excessive Outliers which were capped using the `IQR` method. This was achieved using a user-defined function called `outliers()` to avoid redundancy in the code. The `boxplot` was used from the seaborn library to effectively Visualize the Outliers before and after dealing with Outliers.
- After that, `LabelEncoding` was used to convert important Categorical Variables to numeric type with the following classification :-
    - `Sex` : 0(female), 1(male)
    - `Embarked` : 0(C), 1(Q), 2(S)

**Data Visualization ->**
Important Inferences were made about the Dataset to help with, if any kind of, Decision Making using visualizations from `matplotlib` and `seaborn` libraries such as, 
- A bar chart with the title *Survival Chances according to the Pclass*, that the 'Pclass' variable influences the survival to a great degree. First(1) class had the highest chance of survival as they were given more importance over the people from other classes.
- A bar chart named "Survival chances according to gender" threw light on the fact that Female Passengers had more chances of Survival than Male Passengers.
- Passengers that did not have Sibling(s) or Spouse(s) were at the Highest risk of not Surviving.
- The "Age" and "Fare" variables are Normally Distributed.
- The Majority Passengers were Embarked from 'S' so had the Highest Chances of not surviving among passengers from 'Q' or 'C'.
- The Chart named "Average Age of Passengers in different Classes" uncovered that Average Age of passengers decreased as the Class of the passengers increased, i.e, a passenger of class 1, on an average, is older than the passengers in class 2 or 3.
- The average Fare decreases as the Class of the Passenger decreases.

## Data Preprocessing
1) **Inputs and Target** : Split the Dataset into Inputs and Targets to train the Classification Models. Several Important Features were chosen as Inputs(X), namely, 'Pclass', 'Sex', 'Age', 'SibSp', 'Parch', 'Embarked' and 'Survived' was chosen as the Target(y).
2) **80/20 Split** : The Dataset was splitted into Training and Testing sets including 80% and 20% of the Values from the Dataset respectively. This was important to test the Model's performance on a Test set it had never seen before so as to ensure that the Model doesn't Overfit. This was achieved using the `Sklearn's`, `train_test_split` class.
3) **Feature Scaling** : The Features were all Standardized so that all the Inputs/Features are in the same range which is between 0 and 1. This was achieved using the `StandardScaler()` class from `Sklearn's` `preprocessing` module.

## Model Training and Evaluation
**Model Training** : Several Machine Learning Models were created to predict the Target(Survived) variable from the Dataset such as, `Logistic Regression`, `K-Nearest Neighbours`, `Suppor Vector Machines`, `Naive Bayes` and `Random forest classifier from the` `Skleran` library.

**Model Evaluation and Conclusion** : The Performance of these Machine learning model are given below -
1) `Logistic Regression` - 
    - Training Accuracy: 79.3%
    - Test Accuracy: 80.44%
2) `K-Nearest Neighbours` -
    - Training Accuracy: 84.83%
    - Test Accuracy: 79.88%
3) `Support Vector Classifier` :
    - Training Accuracy: 84.26% 
    - Test Accuracy: 82.21%
4) `Naive Bayes` :
    - Training Accuracy: 79.07%
    - Test Accuracy: 81.56%
5) `Random Forest Classifier` :
    - Training Accuracy: 92.55%
    - Test Accuracy: 77.65%