# is6812

## Home Credit Default Risk

**Business Problem**

Home Credit aims to predict their applicants repayment abilities on loans awarded to the
applicant. They service applicants that struggle to get loans due to the applicants lack of or
nonexistent credit history. Home Credit specialists help these applicants receive loans and
financial services by using a variety of data from the applicants transactional history. Home
Credit needs to accurately monitor and predict applicants repayment capability to ensure
profitability and client acquisition and retention. Home Credit must be able to successfully
approve applicants that are more capable of loan repayment who otherwise would be rejected.
And secondly, avoid awarding loans to applicants who have a higher risk of default to ensure no
loss of profit.

**Benefit of a solution**

Home Credit will benefit from a solution by increasing client retention and acquisition. Their
revenue will also increase due to increased business partnerships with loan providers and
increased client retention and acquisition. This project will also help identify applicants who are
at risk of default to ensure no loss in profits.
Success Metrics:
The project will be a success if the probability of default increases of Home Credit baseline
metrics and use those metrics to determine the return on investment and identify increases in
profitability. Achieving this will be an indicator of model success in determining applicants default
risk.

**Analytics Approach**

The proposed approach will predict which applicants are most likely and least likely to default on
their loan. We will use a supervised analytic approach, specifically a classification model that
utilizes the clients historical data of previous transactional history and credit history. The data
will include but not limited to: previous credits provided by other financial institutions, monthly
balances of previous credits, monthly balance of previous point of sales and cash loans the
applicant had with Home Credit, monthly balance of previous credit cards, repayment history for
previous loans disbursed, and previous applicants for Home Credit loans. The model will then
be implemented into Home Credit’s application system and used on future applicants.

**Findings**

-- Random Forest:
Conducting a random forest showed a good performance in predicting
applicants who default versus those that won't default. The model
achieved accuracy of .72 and a approximately a \~.85 PR-AUC, indicating
strong ability to identify applicants that are at risk of default. It
had a ROC-AUC of \~.75. Other performance metrics to note: The recall is
\~.93, this model catches 93% of the defaulters. Specificity is .322,
indicating many good applicants were flagged as potential defaulters.
The chosen hyperparameters were manually set as baseline parameters.
Conducting a grid search tuning caused major delays in computational
time. To speed up the process manual selection was done. With manual
adjustments, there were marginal differences in performance metrics and
still yielded good performance metrics.

-- Gradiant Boosted Model:
The gradient boosted model yielded better performance. Hyperparameter
changes yielded marginal if any differences in performance metrics. We
decided to mirror the hyperparameters as random forest and
found performance metrics were comparable and reasonable. Tuning
hyperparameters across all parameters yielded marginal changes as
previously stated. Therefore, the chosen hyperparmeters were in
comparison to the random forest model. The accuracy had a minor increase
in accuracy \~.74, PR-AUC of \~.86 and ROC-AUC of \~.76. There was a
decrease in recall, recall dropped from .93 to .87. Specificity
increased to \~.47.

-- Ablation Table:
The ablation table provides insight into the contribution of the
transaction data to predictive performance. When our best model was
trained using only the application data, its performance declined, as
reflected by a lower ROC-AUC and a higher Brier score. In contrast, the
model that included both application and transaction data achieved a
higher ROC-AUC and a lower Brier score. This demonstrates that the
transaction data adds meaningful predictive signal and improves overall
model performance.

![ablationtable_features](https://github.com/user-attachments/assets/71562841-c4a3-4cbd-b6a4-545403e119a2)

-- Feature Importance:
Gain: How much the feature improves model accuracy (i.e., average
reduction in loss when it’s used in a split)
Cover: The fraction of samples affected by splits involving that feature
(how frequently it impacts examples)
Frequency: The fraction of all splits that used the feature (how often
the model used it structurally)
5 Highest Gain Features:
-   ext_source_2: Accounts for 7.7% of the total improvement in loss
    across all splits. The strongest predictor.
-   ext_source_3: Accounts for 6.4%, similar predictive strength.
-   days_birth: Accounts for 2.5% , smaller predictive contribution.
-   days_employed: Accounts for 2.3%, similar predictive contribution as
    days_birth.
-   bur_max_days_credit: Accounts for 2.2%, similar predictive
    contributions as days_birth and days_employed.
The top two, ext_source_2/3 are the most powerful predictors of default risk.
To recall, these variables are the normalized creditworthiness scores
from external data sources. The transaction data provides complementary
insights that further enhance model accuracy.

<img src="https://github.com/user-attachments/assets/f5c81613-39ab-4da9-9a21-a5f755a24341" width="450">


-- Hypothetical Scenario:
Creating a hypothetical scenerio gives us insight on the models capability 
to predict new value inputs. Using a randomly selected data observation in 
the training data, we plugged in our hypothetical applicant Derek's 
demographics into the sampled row. The only information we had on Derek were:
- 45-year-old
- male
- he has one child
- earns $90K per year
- owns his home
- does not own a car
- and has 20 years of employment history
- requesting a $300K loan
  
The other variables remained the same assuming the other 167 variables apply to 
Derek. We had to standardize the values of Derek's attributes to match the down
sampled data the model was trained on. Then found the prediction of default. 
Using the Platt scale calibration, we got a prediction of default of .1 and no 
default of .89. Derek is a safe applicant and is not considered high risk. 

<img width="225" height="73" alt="Derek Predictions" src="https://github.com/user-attachments/assets/95956031-9155-43c0-ad82-3cd0e14f644b" />


# Data Source

The dataset used in this project is from Kaggle:

**Home Credit Default Risk**  
https://www.kaggle.com/competitions/home-credit-default-risk/data

Due to file size and Kaggle licensing, the raw CSV files are not included in this repository.  
Place the downloaded files in this directory before running the scripts.

**Group Project Repo**
https://github.com/mcal8055/is_6812_gp
