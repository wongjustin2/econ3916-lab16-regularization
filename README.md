# Regularization: Buying Bias to Sell Variance

## Objective
I tested how LASSO and Ridge trade a little bias for a big drop in variance when a dataset has more predictors than training rows.

## Methodology
- I built a simulated design with 200 predictors, only 5 of them real, and 105 training rows, and fitted OLS, LASSO and Ridge to it with LASSO and Ridge each in a pipeline with a scaler.
- I compared the test MSEs of the three models.
- I traced the LASSO path to see when the true predictors and the first noise variable entered.
- I chose the penalty by 5-fold cross-validation with the scaler fitted inside every fold.
- I scored LASSO's selection against the known truth.
- I gave LASSO and Ridge two near-duplicate predictors that both matter and compared their coefficients.
- I wrote my own prompt asking an AI for the cross-validation loop and checked its lambda and CV MSE against mine.

## Key Findings
- OLS had a test MSE of 12.9587, Ridge 10.1128 and LASSO 1.4219.
- All five true predictors were in the LASSO path from step 6 and the first noise variable entered at step 17.
- Cross-validation chose lambda = 0.1995 with a CV MSE of 1.5502.
- LASSO found 5 of 5 true predictors with 11 false positives.
- On the near-duplicates LASSO put 4.462 on one and zero on the other, and Ridge split the weight 1.618 and 1.609.
- I went 2 rounds with the AI and its lambda and CV MSE matched mine in every digit both times.
