# customer-churn-prediction

The data used was highly imbalance , the feature to be predicted has 4000 no and 521
yes.
## Features overview:-
1. age (numeric)
2. job : type of job (categorical:
&quot;admin.&quot;,&quot;unknown&quot;,&quot;unemployed&quot;,&quot;management&quot;,&quot;housemaid&quot;,&quot;entrepreneur&quot;,&quot;s
tudent&quot;, &quot;blue-collar&quot;, &quot;self-employed&quot;,&quot;retired&quot;,&quot;technician&quot;,&quot;services&quot;)
3. marital : marital status (categorical: &quot;married&quot;,&quot;divorced&quot;,&quot;single&quot;; note:
&quot;divorced&quot; means divorced or widowed)
4. education (categorical: &quot;unknown&quot;,&quot;secondary&quot;,&quot;primary&quot;,&quot;tertiary&quot;)
5. default: has credit in default? (binary: &quot;yes&quot;,&quot;no&quot;)
6. balance: average yearly balance, in euros (numeric)
7. housing: has housing loan? (binary: &quot;yes&quot;,&quot;no&quot;)
8. loan: has personal loan? (binary: &quot;yes&quot;,&quot;no&quot;)
9. related with the last contact of the current campaign:
10. contact: contact communication type (categorical: &quot;unknown&quot;,&quot;telephone&quot;,
&quot;cellular&quot;)
11. day: last contact day of the month (numeric)
12. month: last contact month of year (categorical: &quot;jan&quot;, &quot;feb&quot;, &quot;mar&quot;, ..., &quot;nov&quot;,
&quot;dec&quot;)
13. duration: last contact duration, in seconds (numeric)
14. other attributes:
15. campaign: number of contacts performed during this campaign and for this
client (numeric, includes last contact)
16. pdays: number of days that passed by after the client was last contacted from a
previous campaign (numeric, -1 means client was not previously contacted)

17. previous: number of contacts performed before this campaign and for this
client (numeric)
18. poutcome: outcome of the previous marketing campaign (categorical:
&quot;unknown&quot;,&quot;other&quot;,&quot;failure&quot;,&quot;success&quot;)
19. Output variable (desired target):
20. y - has the client subscribed a term deposit? (binary: &quot;yes&quot;,&quot;no&quot;)
## Approach:-
1. Collected the data from kaggle
2. Initial Observations:-
● The difference between 75% and max of balance is very
huge,so there are very few clients whose balance is above
1480 (no. of clients:-1129)
● Duration gap between average ,75% and Max is also two high.
(no. of clients:-1130)
● On average a client is contacted 2-3 times during the campaign
but there are 965 clients contacted more than that.
● Only 816 clients were contacted before campaign(previous)
● Only 771 were contacted after previous campaign(pdays)
● There are 521 (yes) who subscribed and 4000 (no&#39;s) who didn&#39;t
subscribe/churn in &quot;y”

3. Performed an exploratory data analysis and below are few finding from
it (More in deep findings are in notebook attached).

<img width="324" alt="image" src="https://github.com/Kunnalpatil/customer-churn-prediction/assets/88432965/87aa210f-937f-42d5-a455-016a9e55dcb4">

**If we keep the range upto 60 years than there are 127 people above it and out of
them only 48 have subscribed**

<img width="498" alt="image" src="https://github.com/Kunnalpatil/customer-churn-prediction/assets/88432965/5b2cb418-0190-477b-a28f-bf1db565962b">

**The above figure shows subscription among the job titles lookinng at it we can say job will be one of deciding feature**
<img width="243" alt="image" src="https://github.com/Kunnalpatil/customer-churn-prediction/assets/88432965/d7c8d66d-5148-4972-b087-4c48fe990481">

**There are only 17% defaulters in data and most non-defaulters amongst subscribed one's**

<img width="478" alt="image" src="https://github.com/Kunnalpatil/customer-churn-prediction/assets/88432965/d40d49e7-8876-4c54-a22d-1f0b72eefa4c">

**There are few high balance accounts with more balance then the 75th percentile and this is hiding the negative balance, but if we plot distribution up 75th we catch them. shown in above figure**

<img width="335" alt="image" src="https://github.com/Kunnalpatil/customer-churn-prediction/assets/88432965/36237967-8c65-4d9c-869d-da6df6aed9fa">

4. Data preprocessing:-
● Converted Yes/No features to binary (1 and 0)
● Divided the data into train and test
● Used column transformer and converted categorical features to
numeric using OneHotEncoder and scaled the numeric columns
using standard scaler.

5. Model building:-
● Tried with different models and choose to finalise
GradientBoostingClassifier
● Used two approaches first train the model on imbalance data and
second train model on balanced data using
BalancedBaggingClassifier

6. Results:-

(The dependent variable had two options like the client subscribed a
term deposit (yes/No) assuming that the ones who have not subscribed are
the churn ones. )

1. First model:-
   
<img width="275" alt="image" src="https://github.com/Kunnalpatil/customer-churn-prediction/assets/88432965/7bb32bf2-ff0f-44a6-9364-919f72c2db5c">
   
**Here we are able to capture the clients who have churn with good accuracy**

2. Second model:-
   
<img width="267" alt="image" src="https://github.com/Kunnalpatil/customer-churn-prediction/assets/88432965/4db57fda-1363-45c2-a64b-a35e51eac7a3">

**This model is able to capture the clients who have subscribed even though they are very less in the dataset (because of balancing the dataset)**

7. Conclusion:-
The business can decide which model to use as pre the
business requirements



