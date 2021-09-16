# beer-consumption-mlr
## Using R to solve multiple linear regression in Beer consumption data

- Write a code for doing k-fold cross validation. Refer back to the class notes for details on k-fold cross validation. Let k=10 and use average RMSE as the metric for quantifying predictive error. What is the average RMSE for your regression model?

If you were able to complete this question last time, just write your answer down again.

#### Suppose your data is stored in the object "Data"
#### First set a seed to ensure your results are reproducible
set.seed(...) # use whatever number you want
#### Now randomly re-shuffle the data
Data <- Data[sample(nrow(Data)),]
#### Define the number of folds you want
K <- ...
#### Define a matrix to save your results into
RSME <- matrix(0,nrow=K,ncol=1)
#### Split the row indexes into k equal parts
kth_fold <- cut(seq(1,nrow(Data)),breaks=K,labels=FALSE)
#### Now write the for loop for the k-fold cross validation
for(k in 1:K){
#### Split your data into the training and test datasets
test_index <- which(kth_fold==k)
train <- Data[-test_index,]
test <- Data[test_index,]
#### Now that you've split the data, 
RSME[k,] <- ... # write your code for computing RMSE for each k here
#### You should consider using your code for question 7 above
}
... 
- Calculate the average of all values in the RSME matrix here.
- Now, do EDA to explore interaction effects between all your predictors. Summarize your findings in a few sentences.
- Extend your linear model to include interaction terms between weekend and the other two predictors. Are the interaction terms significant? What are the implications of these findings in the context of the data?

To include an interaction term between two variables x1 and x2 in your linear model, use

"model object here" <- lm(y ~ x1 + x2 + x1:x2)
OR

"model object here" <- lm(y ~ x1*x2)
- Do stepwise model selection using AIC and BIC with the “full model” set to the model from question 3. Summarize your findings in a few sentences.

- Use your code for the k-fold cross validation from question 1 to compute the average RMSE for the new model in question 3. Is the new RMSE model lower or higher than your result from question 1? What can you infer from that?
