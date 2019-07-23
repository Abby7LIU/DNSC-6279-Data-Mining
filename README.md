![GWU cover](https://github.com/Abby7LIU/DNSC-6211-Programming-for-Business-Analytics/blob/master/GWU.png)
# DNSC-6279-Data-Mining                            
#### Course Description(From Sllybus)
The focus of the course is to provide  exposure to various data preprocessing, statistics, and machine learning techniques that can be used both to discover relationships in large data sets and to build predictive models. Techniques covered will include basic and analytical data preprocessing, regression models, decision trees, neural networks, clustering, association analysis, and basic text mining. Techniques will be presented in the context of data driven organizational decision making using statistical and machine learning approaches.

#### All Projects in the repository are due to group contribution.  
__Group Members:__ 
- Qianying Diao 
- Qiang Wang
- Xinrong Chen
- Jingyi Liu

### Project 1: Acquire Valued Shoppers Challenge
- [Basic Data Prepararion](https://github.com/Abby7LIU/DNSC-6279-Data-Mining/blob/master/A01.ipynb)
- [Classification with logistic regression](https://github.com/Abby7LIU/DNSC-6279-Data-Mining/blob/master/A02.ipynb)
- [Classification with GBM and ANN](https://github.com/Abby7LIU/DNSC-6279-Data-Mining/blob/master/A03.ipynb)
- [Clustering and PCA](https://github.com/Abby7LIU/DNSC-6279-Data-Mining/blob/master/A04.ipynb)

##### [Data Source and Project Overview](https://www.kaggle.com/c/acquire-valued-shoppers-challenge/data)
![PUBG](https://github.com/Abby7LIU/DNSC-6279-Data-Mining/blob/master/PUBG.png)
### [Project 2: PUBG Match Death and Statitics](https://github.com/Abby7LIU/DNSC-6279-Data-Mining/edit/master/README.md)
#### 1. Dataset Introduction
PlayerUnknown's BattleGrounds (PUBG) has enjoyed massive popularity. In the dataset, we are given over 65,000 games' worth of anonymized player data, split into training and testing sets, and asked to predict final placement from final in-game stats and initial player ratings. A detailed description of variables can be found [HERE](https://www.kaggle.com/skihikingkevin/pubg-match-deaths).
#### 2. EDA
1. Plot the histogram, get familiar with the property of each variable
2. Match type matters: The game has 4 modes: solo, double and square. The relationship of independent variables and win percent differs in different match types. 
3. Using heat map, we identify 4 the most correlated variables as 'totaldistance', 'boots', 'weaponAcquired' and 'damageDealt'
#### 3. Data preparation
- __Dimension Reduction:__  The original dataset has 27 independent variables which should be reduced. We identify 3 similar variables 'rideDistance', 'walkdistance' and 'swimdistance'. We merged them into one variable 'totaldistance'
- __Removing outliers:__  Remove the records showing the player kill others without moving as it is unreasonable.
- __Binning the levels of the categorical variable:__  For variable ”matchType”, some records contain unwanted information such as ‘solo-fpp‘ since there are only three types of match, convert records to only 3 levels: ‘solo’, ‘duo’ and ‘squd’.
- __Multicollinearity:__  Multicollinearity is not allowed for  generalized Linear Model. , We generate a heap map.  The coefficients of rankpoints, kill points and winpoints, kills and damagedealt, kills and killplace, number of groups and maxplaces are high, so we delete the kill points, kills and rankpoints, maxplaces as well as damagedealt.
#### 4. Modeling
First, we identify whether the dependent variable should be treated as categorical or numerical by comparing model performances of the linear model and logistic model. Generalized linear model turned out to be better so we further our analysis expecting a numeric output in GBM and MLP model.
Overall, we used 4 different models to do the prediction. Generalized Linear Model, Logistic Regression, Multilayer perceptron Model and  Gradient boosting machine. Gradient boosting machine is the best performing model with an MAE(kaggle score criterion) of 0.05671.
GBM model tuning: run the origin model, check the parameter of top 10 models and modify the parameters, repeat this process until the MSE narrow down to a steady level.
#### 5. Model Comparison (Kaggle scores):
The score of the kaggle is MAE of the models. 
- Generalized Linear Model: 0.9983
- Logistic Regression 0.16248
- Gradient boosting machine: 0.05671
- Multilayer perceptron Model: 0.08020
#### 6. Recommendation
Our best model GBM shows the 5 best variables are totalDistance, killPlace(the rank of player kills), weaponAcquired, Boosts(number of boost item used) and heals.
So our suggestion for this game’s player is: being active on moving and killing.
