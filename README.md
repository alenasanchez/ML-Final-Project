# ML-Final-Project

Individual Report: Decision Tree Model

Utilizing Machine Learning Models to Predict the Effects of Food Accessibility in California on Cardiovascular Disease (CVD) 

BSAN 6070: Introduction to Machine Learning
Dr. Arin Brahma

By: Alena Sanchez

Decision Tree - Alena
Model Justification
As we aim to use this data to predict CVD risk based on food accessibility and other determinant factors in a census tract, it was found that decision trees are often a common method utilized in healthcare analytics. According to, A comparative study of classification and prediction of Cardio-Vascular Diseases (CVD) using Machine Learning and Deep Learning techniques, “Decision tree(s) gives a procedural approach for classification of categorical data based on the features or attributes. Hence, it stands the most widely used method for classification in DMT (Data Mining Techniques) for processing large amount(s) of data.” With this, I found that a decision tree algorithm would be a justified choice. Additionally, through further research it was found that this type of model has the ability to handle complex data, this struck my interest in pursuing a decision tree algorithm even further as the data we prepared contains both ordinal and nominal data. Furthermore, as we are aiming to predict CVD risk, it is critical that we construct a model that can be trusted with high accuracy. With this, decision trees also have the ability to develop into ensemble algorithms that take into account multiple trees’ predictions that are weighted to come up with a final decision.
Preparing Data for Model
With the decision to proceed with a decision tree model, it was necessary to run additional data cleaning and preparation. First, I decided to drop attributes that I immediately knew would not contribute to the model either because the attribute was meaningless or there were too many nulls that could not be filled. These attributes include Census Tract, lapop1share, lalowi1share, California County, ZIP, Approximate Location, Low Birth Weight, CES 4.0 Score, Unemployment, Housing Burden, and Pop. Char. Score. Next, with the remaining data, I had to ensure that there were no nulls, so I dropped all records that contained any missing values. 969 total records were dropped, leaving the final dataset with 7054 total records and 25 features. 

Furthermore, with the intent to create a decision tree utilizing scikit-learn’s DecisionTreeClassifier, it was necessary to transform our response variable, Cardiovascular Disease, into a classifier. With the idea to run multiple models, I decided to create two different variables, one a binary classifier and the other being multi-class. The first classifier I created was binary which labeled all records that contained CVD rates equal or greater than 12.5% as 1 and anything below 12.5% was classified as a 0. The second classification variable was a multi-class classifier, all records with CVD rates less than or equal to 10% were labeled as 0, 10-15% were labeled as 1, and any record greater than 15% were labeled as 2. Below, we see the balance of the various classifications that will be used in the model.

Feature Selection
To go into further detail regarding feature selection for the model, I utilized a correlation heatmap that we saw earlier in this report, along with VIF, also known as Variance Inflation Factor. These two visualizations allow me to understand which variables have the potential to affect the performance of the models. With the use of the heatmap, I dropped LATracts_Vehicle_20 as it has a correlation of .99 with HUNVFlag. I also dropped the original Cardiovascular Disease attribute as it can not be run since it is the attribute that created the classifiers.


Model
This paper will now discuss the implementation of the Decision Tree Algorithm I began by first splitting the data into training and test datasets, the training set was 75% of the original data and the test set was the remaining 25%. I then developed 2 binary decision trees. Below you can see the decision tree with the highest performance. This tree utilizes entropy as the split criterion, with a maximum tree depth of 5 and minimum samples split of 15. When running the decision trees I ran various hyper-parameters through the algorithm and these are the values that returned the highest performing model. f



With this tree we can now utilize various performance measures to analyze the reliability of the model. First accuracy, this model returned 81% accuracy, predicting 1,420 classifications correctly out of 1,764. Next I measured F-1 score as it takes into account both precision and recall, here we again see about a 0.81 F-1 score. Lastly, the area under the curve (AUC) as we can see in the figure below is approximately 81% as well. These performance metrics all returned acceptable numbers that indicate the model is reliable.



Next, I will discuss the multi classifier trees developed also using scikit-learn’s algorithm. Below is a figure of the best performing tree. It takes in the same features as model 1,  but now uses the multi-classifier variable as well as has a maximum depth of 15 and minimum sample split of 30. Again I ran various models with this classifier, but this was the best performing model. I want to note that the entropy criterion was used because although gini may be quicker it has been found that entropy may lead to more accurate results, and with this scope of project we want to prioritize accuracy over efficiency.




Performance Analysis

With this tree we can now discuss performance with multi classifiers. Performance is measured a little differently as there is not simply a correct and incorrect. With this, I wanted to simplify it and emphasize maximizing the diagonal. As you can see in the confusion matrix below, this model is the one that maximized the diagonal. Additionally, I looked at accuracy and at weighted F-1 scores which were both around 62%.

Prediction
I initially wanted to use solely model 1 to predict CVD risk, but I figured I could potentially use the multi-class model for further insight. When inputting the features below into the binary model, it is predicting that a tract with these characteristics is at a risk of 12.5% or above as it returns 1. Additionally, when running these metrics into the multi-class model, it is predicted that the tract is at a risk greater than 15% as it returns 2.


Conclusion
The decision tree method has proven to show potential as it has an acceptable accuracy and performance, is reliable and known to be used in healthcare, and also has the capabilities to expand and develop into a more complex ensemble algorithm.

Prediction Insights and Recommendations

With the prediction earlier, the numbers used in the model came from a census tract in Miami, Florida. With this, we wanted to show the capabilities of how this model can expand across the country as well as help areas in need. Florida is known to have a higher CVD risk than many other states. In 2019, the Department of Health in Miami-Dade announced to Floridians the five steps they can take to improve their heart health: Quit Smoking, Increase your physical activity, Control your blood pressure, Know your cholesterol, And emphasize Eating heart healthy foods! With this the model can apply to Florida's census tracts so they can provide the healthy food options to the tracts that are in most need.

For use of this model in the future, it is advised that it be expanded and analyzed tracts not only in California,  but across the nation. Additionally, it is suggested  that a more ensemble method be utilized for better predictions. Finally, iterate and continue to tune the model for the best performance possible.
