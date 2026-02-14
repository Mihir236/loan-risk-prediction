loan-risk-prediction
a predictive model for assessing loan risk using machine learning techniques and data analysis. By analyzing historical loan data, we can identify patterns and factors that contribute to loan defaults, enabling financial institutions to make informed lending decisions.

Basel III Compliance implementation
In simple terms, banks nowadays need to have enough reserves to survive economic and financial shocks. It requires banks to calculate expected loss which is defined as:

E
L
=
P
D
×
L
G
D
×
E
A
D

where:
P
D
 - probablility of default; Chance that a borrower won't pay back,

L
G
D
 - Loss given default; How much money will the bank lose if they default

E
A
D
 - Exposure at default; Total loan amount at risk

For each of those components I've built a seprate model, combined them together and then calculate the expected loss (
E
L
) for each of those loans (check notebook). That way we build a system which automatically checks each loan and calculates it's 
E
L
. Each of those models we're built on German credit dataset.

Probability of default
A gradient boosted tree model learner takes in the dataset and it is trained by setting a target column (in this case, column Risk).

Loss given default
LGD valuse is based on collateral and financial situation of every borrower. If the financial situation is more stable, the lower the LGD. But because on bigger datasets there is much more data (much more elements to add to LGD) I had to add some noise to the data so that it would look more realistic:

 lgd_val = base_lgd + np.random.normal( 0, 0.05 )
Exposure at default
Will be always 0 as the data is from when the loans were accepted or not
