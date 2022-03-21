# hamoye-ds-internship


I'll be posting solution to the quizzes and some projects I did for the Hamoye 2022 Data Science Internship

## Project 1:  This is a quiz using dataset from the Food and Agriculture Organization of the United Nations

## Project 2: Appliances Energy Prediction Data

### Description of Dataset:

[Link to Dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00374/)

The dataset for the remainder of this quiz is the Appliances Energy Prediction data. The data set is at 10 min for about 4.5 months. The house temperature and humidity conditions were monitored with a ZigBee wireless sensor network. Each wireless node transmitted the temperature and humidity conditions around 3.3 min. Then, the wireless data was averaged for 10 minutes periods. The energy data was logged every 10 minutes with m-bus energy meters. Weather from the nearest airport weather station (Chievres Airport, Belgium) was downloaded from a public data set from Reliable Prognosis (rp5.ru), and merged together with the experimental data sets using the date and time column. Two random variables have been included in the data set for testing the regression models and to filter out non predictive attributes (parameters). The attribute information can be seen below.

Attribute Information:

Date, time year-month-day hour:minute:second

Appliances, energy use in Wh

lights, energy use of light fixtures in the house in Wh

T1, Temperature in kitchen area, in Celsius

RH_1, Humidity in kitchen area, in %

T2, Temperature in living room area, in Celsius

RH_2, Humidity in living room area, in %

T3, Temperature in laundry room area

RH_3, Humidity in laundry room area, in %

T4, Temperature in office room, in Celsius

RH_4, Humidity in office room, in %

T5, Temperature in bathroom, in Celsius

RH_5, Humidity in bathroom, in %

T6, Temperature outside the building (north side), in Celsius

RH_6, Humidity outside the building (north side), in %

T7, Temperature in ironing room , in Celsius

RH_7, Humidity in ironing room, in %

T8, Temperature in teenager room 2, in Celsius

RH_8, Humidity in teenager room 2, in %

T9, Temperature in parents room, in Celsius

RH_9, Humidity in parents room, in %

To, Temperature outside (from Chievres weather station), in Celsius

Pressure (from Chievres weather station), in mm Hg

RH_out, Humidity outside (from Chievres weather station), in %

Wind speed (from Chievres weather station), in m/s

Visibility (from Chievres weather station), in km

Tdewpoint (from Chievres weather station), Â°C

rv1, Random variable 1, nondimensional

rv2, Random variable 2, nondimensional

## Project 3: Stability of the Grid System

Electrical grids require a balance between electricity supply and demand in order to be stable. Conventional systems achieve this balance through demand-driven electricity production. For future grids with a high share of inflexible (i.e., renewable) energy sources, the concept of demand response is a promising solution. This implies changes in electricity consumption in relation to electricity price changes. In this work, we’ll build a binary classification model to predict if a grid is stable or unstable using the [UCI Electrical Grid Stability Simulated dataset](https://archive.ics.uci.edu/ml/datasets/Electrical+Grid+Stability+Simulated+Data+)



It has 12 primary predictive features and two dependent variables.


### Predictive features:

1. ***tau1*** to ***tau4***: the reaction time of each network participant, a real value within the range 0.5 to 10 (***tau1*** corresponds to the supplier node, ***tau2*** to ***tau4*** to the consumer nodes).


2. ***p1*** to ***p4***: nominal power produced (positive) or consumed (negative) by each network participant, a real value within the range -2.0 to -0.5 for consumers (***p2*** to ***p4***). As the total power consumed equals the total power generated, ***p1 (supplier node) = - (p2 + p3 + p4)***.

3. ***g1*** to ***g4***: price elasticity coefficient for each network participant, a real value within the range 0.05 to 1.00 (***g1*** corresponds to the supplier node, ***g2*** to ***g4*** to the consumer nodes; ***g*** stands for 'gamma').


### Dependent variables:


1. ***stab***: the maximum real part of the characteristic differential equation root (if positive, the system is linearly unstable; if negative, linearly stable).

2. **stabf***: a categorical (binary) label ('stable' or 'unstable').
Because of the direct relationship between ***stab*** and ***stabf*** (***stabf*** = 'stable' if ***stab*** <= 0, 'unstable' otherwise), ***stab*** should be dropped and ***stabf*** will remain as the sole dependent variable (binary classification).


### Methodology:

1. I split the data into an 80-20 train-test split with a random state of “1”. The stab column was dropped since it is a binarry clasifier problem.

2. Then I used the standard scaler to transform the train set (***X_train, y_train***) and the test set (***X_test***). 

3. After that I used scikit-learn to train a random forest and extra trees classifier. 

4. Finally I used xgboost and lightgbm to train an extreme boosting model and a light gradient boosting model and also check their various accuracies on the test set. 

5. As an extra step, I tuned the extra trees classifier using a Randomized CV and obtained a better accuracy.

6. The Light Gradient Boosted Machine (LightGBM) produced the best accuracy on the test set (acc = 0.9365 ).


` (Note: I used random_state = 1 for training all models and evaluations on the test set.) `




## Project 4: Understanding the Amazon from Space

I built artificial intelligence algorithms to label satellite image chips with different atmospheric conditions and the different classes of land cover/land use.  For this Multi-class Multi-Label problem, some of the labels are from the following categories: Cloud Cover (clear, partly, cloudy, haze), Primary RainForest, Water (rivers, lakes), Habitation (large city, small homes), Agriculture, Roads etc. The algorithms from this project will enable us to understand where, how and why deforestation happens.

This quiz was obtained from the [Kaggle](https://www.kaggle.com/) Competition platform and would be submitted as a late project. 

### Steps:
1. Sign up for a Kaggle account: https://www.kaggle.com/
2. Open the Kaggle Amazon Deforestation Competition page: [Planet: Understanding the Amazon from Space](https://www.kaggle.com/c/planet-understanding-the-amazon-from-space/overview)
3. Enter the competition, read all the instructions, download the data and start with a baseline.
4. Submit your solution to Kaggle (as late submission)
TIPS: The Kaggle notebook and discussion sections are the best resources you will need for this challenge. Make use of them.

After submission, Kaggle will give you a score (Mean FScore Beta) and where you would have landed on the leadership board. Remember to share the screenshot and your Github solution notebook.

### Description

Every minute, the world loses an area of forest the size of 48 football fields. And deforestation in the Amazon Basin accounts for the largest share, contributing to reduced biodiversity, habitat loss, climate change, and other devastating effects. But better data about the location of deforestation and human encroachment on forests can help governments and local stakeholders respond more quickly and effectively.

Planet, designer and builder of the world’s largest constellation of Earth-imaging satellites, will soon be collecting daily imagery of the entire land surface of the earth at 3-5 meter resolution. While considerable research has been devoted to tracking changes in forests, it typically depends on coarse-resolution imagery from Landsat (30 meter pixels) or MODIS (250 meter pixels). This limits its effectiveness in areas where small-scale deforestation or forest degradation dominate.

Furthermore, these existing methods generally cannot differentiate between human causes of forest loss and natural causes. Higher resolution imagery has already been shown to be exceptionally good at this, but robust methods have not yet been developed for Planet imagery.

In this competition, Planet and its Brazilian partner SCCON are challenging Kagglers to label satellite image chips with atmospheric conditions and various classes of land cover/land use. Resulting algorithms will help the global community better understand where, how, and why deforestation happens all over the world - and ultimately how to respond.

To dig into/explore more Planet data, sign up for a free account.

And if you're interested in building applications on Planet data, check out our Application Developer Program.

### Methodology
1. Review the data page, which includes detailed information about the labels and the labeling process.
2. Download a subsample of the data to get familiar with how it looks.
3. Explore the subsample on Kernels. We’ve created a notebook for you to get started.



### My Score!
