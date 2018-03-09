
Build a binary logistic regression model to predict store type given certain transaction characteristics.
Specifically predict the probability of storetype is ‘C’ or not given certain characteristics

Level 1
●	Build a binary logistic regression model to predict probability of storetype being C given number of customers,
open, promo, state holiday, school holiday, day of week, week of month and month of year
●	Train the model on 2013,2014
●	Test the model on 2015 (use predict function to predict on 2015 data)
●	Using the default probability cutoffs of the model above, what is the accuracy, precision and recall of the model you built above ?
●	What are the variables that are statistically significant in the model ?

Level 2
●	What is probability of storetype==C when 1000 customers visit when store is open, when there is promotion, when it is a state holiday and school holiday on Aug5,2015. Use the model constructed above.

Level 3
●	
●	Change the cutoff probability of the model to 0.6. What is the accuracy, precision, recall, and auc of the model you built above ?
●	Generate the confusion matrix on 2015 data. Explain what this confusion matrix suggests ?
●	What is the best F1 score of the model ? What would be the optimal probability cutoff you would pick that maximizes this metric ?
●	Do feature selection/ variable selection using stepwise selection algorithm. Does it improve accuracy of the model ?


Goal
●	By the end of this assignment you should be familiar in and out with logistic regression and glm function in R. You should understand and apply below concepts in logistic regression
●	Classification models
●	Probability predictions
●	Accuracy metrics in logistic regression
●	Probability cutoffs and its impact on precision/recall
●	Area under curve metric (aka AUC)
●	Confusion matrix
●	Converting features to factors wherever appropriate
●	One hot encoding
