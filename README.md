# OSDA Big Homework
## Option - Lazy FCA
[Lazy FCA library](https://github.com/AndrewDiv/FCALC)

### Datasets:
1. [Israel's Covid-19 Dataset for Year 2020 & 2021](https://www.kaggle.com/datasets/mykeysid10/covid19-dataset-for-year-2020) (isr)
2. [COVID, FLU, COLD Symptoms](https://www.kaggle.com/datasets/walterconway/covid-flu-cold-symptoms) (cfc)
3. [Symptoms and COVID Presence (May 2020 data)](https://www.kaggle.com/datasets/hemanthhari/symptoms-and-covid-presence) (cov)

### Datasets preparation
1. In isr dataset columns with test date and patients gender were deleted. Test indication column was transformed into two binary columns: 'Abroad' and 'Contact with confirmed'.
2. The initial cfc dataset had four target classes: 'ALLERGY', 'FLU', 'COLD' and 'COVID'. Among those only objects with 'COLD' and 'COVID' were picked, 'COVID' was assigned to be the positive class, 'FLU' was assigned to be the negative. As the resulting dataset had 3k rows, stratified data sample of 500 objects was taken.
3. In cov dataset all values 'No' were changed to False and all values 'Yes' were changed to True.

Duplicates (repeated rows) were removed from all datasets. 

Dataset sizes after preparation:
1. isr: 366 rows x 9 columns
2. cfc: 500 rows × 21 columns (sample)
3. cov: 466 rows × 21 columns

All features in all datasets are categorical; they correspond to presence (True) or absence (False) of medical symptoms and risk factors. 

Note that isr dataset in 'Datasets' folder has no duplicates and has two columns removed already (GitHub did not allow to push the full vesion due to its' large size).

### Standard Models
In this HW assignemnt the following standard models were used:
- Logistic regression
- K-Nearest Neighbours
- Naive Bayes
    * Multinomial NB
    * Gaussian NB
    * Complement NB
- Decision Tree
- Random Forest

### Validation

To calculate accuracy and f1-score for each dataset and to tune the parameters, stratified 10-fold cross
validation was used.

### Hyperparameter tuning

Hyperparameter tuning of standard models was done with **GridSearchCV** from **scikit**. FCALC classifiers do not support it, so the optimal parameters for Binarized and Pattern Binary Classifiers were found through simple **for** loops. 

The following hyperparameters were tuned:

- LogisticRegression: **'C'**

- KNeighborsClassifier: **'n_neighbors'**

- MultinomialNB: **'alpha'**

- GaussianNB: **'var_smoothing'**

- ComplementNB: **'alpha'**

- DecisionTreeClassifier: **'criterion'**, **'max_depth'** and **'min_samples_split'**

- RandomForestClassifier: **'criterion'**, **'max_depth'**, **'min_samples_split'** and **'n_estimators'**

- BinarizedBinaryClassifier: **'method'** and **'alpha'**

- PatternBinaryClassifier: **'method'** and **'alpha'**

In case of Binary Classifiers alpha was searched in the interval from 0 to 1 (including edges) for all methods, and additionally in the interval from 1 to 10 (including edges) for the ratio-support method.

### Optimal parameters

Optimal parameters for each method and dataset are presented in a table below.

<table>
    <colgroup>
        <col style="border: 1px solid #ddd" span="13" />
    </colgroup>
    <tr>
        <th style="text-align: center" rowspan="2"><u>Dataset</u> Method</th>
        <th style="text-align: center" colspan="4">isr</th>
        <th style="text-align: center" colspan="4">cfc</th>
        <th style="text-align: center" colspan="4">cov</th>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
    </tr>
    <tr>
        <th rowspan="2">Logistic regression</th>
        <td>C</td>
        <td colspan="3"> </td>
        <td>C</td>
        <td colspan="3"> </td>
        <td>C</td>
        <td colspan="3"> </td>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
        <td>1.88</td>
        <td colspan="3"> </td>
        <td>1</td>
        <td colspan="3"> </td>
        <td>1</td>
        <td colspan="3"> </td>
    </tr>
    <tr>
        <th rowspan="2">K-NN</th>
        <td>n_neighbors</td>
        <td colspan="3"> </td>
        <td>n_neighbors</td>
        <td colspan="3"> </td>
        <td>n_neighbors</td>
        <td colspan="3"> </td>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
        <td>45</td>
        <td colspan="3"> </td>
        <td>61</td>
        <td colspan="3"> </td>
        <td>12</td>
        <td colspan="3"> </td>
    </tr>
    <tr>
        <th rowspan="2">Multinomial Naive Bayes</th>
        <td>alpha</td>
        <td colspan="3"> </td>
        <td>alpha</td>
        <td colspan="3"> </td>
        <td>alpha</td>
        <td colspan="3"> </td>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
        <td>26.901</td>
        <td colspan="3"> </td>
        <td>0.001</td>
        <td colspan="3"> </td>
        <td>0.501</td>
        <td colspan="3"> </td>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
        <th rowspan="2">Gaussian Naive Bayes</th>
        <td>var_smoothing</td>
        <td colspan="3"> </td>
        <td>var_smoothing</td>
        <td colspan="3"> </td>
        <td>var_smoothing</td>
        <td colspan="3"> </td>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
        <td>1</td>
        <td colspan="3"> </td>
        <td>1</td>
        <td colspan="3"> </td>
        <td>0.1874</td>
        <td colspan="3"> </td>
    </tr>
    <tr>
        <th rowspan="2">Complement Naive Bayes</th>
        <td>alpha</td>
        <td colspan="3"> </td>
        <td>alpha</td>
        <td colspan="3"> </td>
        <td>alpha</td>
        <td colspan="3"> </td>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
        <td>91.001</td>
        <td colspan="3"> </td>
        <td>25.301</td>
        <td colspan="3"> </td>
        <td>60.801</td>
        <td colspan="3"> </td>
    </tr>
    <tr>
        <th rowspan="2">Decision Tree</th>
        <td>min_samples_split</td>
        <td>max_depth</td>
        <td>criterion</td>
        <td> </td>
        <td>min_samples_split</td>
        <td>max_depth</td>
        <td>criterion</td>
        <td> </td>
        <td>min_samples_split</td>
        <td>max_depth</td>
        <td>criterion</td>
        <td> </td>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
        <td>2</td>
        <td>2</td>
        <td>gini</td>
        <td> </td>
        <td>10</td>
        <td>10</td>
        <td>gini</td>
        <td> </td>
        <td>10</td>
        <td>6</td>
        <td>gini</td>
        <td> </td>
    </tr>
    <tr>
        <th rowspan="2">Random Forest</th>
        <td>min_samples_split</td>
        <td>max_depth</td>
        <td>criterion</td>
        <td>n_estimators</td>
        <td>min_samples_split</td>
        <td>max_depth</td>
        <td>criterion</td>
        <td>n_estimators</td>
        <td>min_samples_split</td>
        <td>max_depth</td>
        <td>criterion</td>
        <td>n_estimators</td>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
        <td>2</td>        
        <td>2</td>        
        <td>gini</td>        
        <td>70</td>
        <td>12</td>
        <td>10</td>
        <td>gini</td>
        <td>90</td>
        <td>4</td>        
        <td>6</td>        
        <td>entropy</td>        
        <td>70</td>
    </tr>
    <tr style ="border-top: 1px solid #ddd">
        <th rowspan="2">Binarized Binary Classifier</th>
        <td>method</td>
        <td>alpha</td>
        <td colspan="2"> </td>
        <td>method</td>
        <td>alpha</td>
        <td colspan="2"> </td>
        <td>method</td>
        <td>alpha</td>
        <td colspan="2"> </td>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
        <td>standard-support</td>
        <td>1</td>
        <td colspan="2"> </td>
        <td>ratio-support</td>
        <td>0.00</td>
        <td colspan="2"> </td>
        <td>standard</td>
        <td>0.15</td>
        <td colspan="2"> </td>
    </tr>
    <tr>
        <th rowspan="2">Pattern Binary Classifier</th>
        <td>method</td>
        <td>alpha</td>
        <td colspan="2"> </td>
        <td>method</td>
        <td>alpha</td>
        <td colspan="2"> </td>
        <td>method</td>
        <td>alpha</td>
        <td colspan="2"> </td>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
        <td>standard</td>
        <td>0.1</td>
        <td colspan="2"> </td>
        <td>ratio-support</td>
        <td>3.00</td>
        <td colspan="2"> </td>
        <td>standard</td>
        <td>0.00</td>
        <td colspan="2"> </td>
    </tr>

</table>

### Results
Performance of models is presented in the table below. 

<table>
    <colgroup>
        <col style="border: 1px solid #ddd" span="10" />
    </colgroup>
    <tr style ="border-bottom: 1px solid #ddd; margin-left: 0">
        <th style="text-align: center">Dataset</th>
        <th style="text-align: center" colspan="3">isr</th>
        <th style="text-align: center" colspan="3">cfc</th>
        <th style="text-align: center" colspan="3">cov</th>
    </tr>
    <tr style ="border-bottom: 1px solid #ddd">
        <th style="text-align: center">Method\ Metric</th>
        <td style="text-align: center">Accuracy</td>
        <td style="text-align: center">F1 binary</td>
        <td style="text-align: center">F1 macro</td>
        <td style="text-align: center">Accuracy</td>
        <td style="text-align: center">F1 binary</td>
        <td style="text-align: center">F1 macro</td>
        <td style="text-align: center">Accuracy</td>
        <td style="text-align: center">F1 binary</td>
        <td style="text-align: center">F1 macro</td>
    </tr>
    <tr>
        <th>Logistic regression</th>
        <td>0.3629</td>
        <td>0.3485</td>
        <td>0.3595</td>
        <td>0.9800</td>
        <td>0.9852</td>
        <td>0.9771</td>
        <td>0.9633</td>
        <td>0.9784</td>
        <td>0.9281</td>
    </tr>
    <tr>
        <th>K-NN</th>
        <td>0.4751</td>
        <td>0.5811</td>
        <td>0.4367</td>
        <td>0.9860</td>
        <td>0.9898</td>
        <td>0.9838</td>
        <td>0.9376</td>
        <td>0.9637</td>
        <td>0.8679</td>
    </tr>
    <tr>
        <th>Multinomial Naive Bayes</th>
        <td>0.3631</td>
        <td>0.3545</td>
        <td>0.3564</td>
        <td>0.9800</td>
        <td>0.9854</td>
        <td>0.9769</td>
        <td>0.8668</td>
        <td>0.9255</td>
        <td>0.6488</td>
    </tr>
    <tr>
        <th>Gaussian Naive Bayes</th>
        <td>0.3770</td>
        <td>0.3785</td>
        <td>0.3738</td>
        <td>0.9840</td>
        <td>0.9882</td>
        <td>0.9816</td>
        <td>0.9634</td>
        <td>0.9782</td>
        <td>0.9313</td>
    </tr>
    <tr>
        <th>Complement Naive Bayes</th>
        <td>0.3577</td>
        <td>0.3562</td>
        <td>0.3542</td>
        <td>0.9880</td>
        <td>0.9913</td>
        <td>0.9861</td>
        <td>0.9269</td>
        <td>0.9576</td>
        <td>0.8430</td>
    </tr>
    <tr>
        <th>Decision Tree</th>
        <td>0.3493</td>
        <td>0.2666</td>
        <td>0.3343</td>
        <td>0.9860</td>
        <td>0.9894</td>
        <td>0.9843</td>
        <td>0.9505</td>
        <td>0.9706</td>
        <td>0.9048</td>
    </tr>
    <tr>
        <th>Random Forest</th>
        <td>0.3633</td>
        <td>0.3834</td>
        <td>0.3533</td>
        <td>0.9820</td>
        <td>0.9869</td>
        <td>0.9791</td>
        <td>0.9548</td>
        <td>0.9736</td>
        <td>0.9070</td>
    </tr>
    <tr style ="border-top: 1px solid #ddd">
        <th>Binarized Binary Classifier</th>
        <td>0.4372</td>
        <td>0.4949</td>
        <td>0.3823</td>
        <td>0.9840</td>
        <td>0.9882</td>
        <td>0.9816</td>
        <td>0.8432</td>
        <td>0.9134</td>
        <td>0.5422</td>
    </tr>
    <tr>
        <th>Pattern Binary Classifier</th>
        <td>0.4367</td>
        <td>0.4363</td>
        <td>0.3875</td>
        <td>0.9820</td>
        <td>0.9864</td>
        <td>0.9799</td>
        <td>0.9354</td>
        <td>0.9612</td>
        <td>0.8811</td>
    </tr>

</table>

Note that for lazy classifiers it was impossible to use **f1_score** from **scikit** with **average = "binary"**, as the output consisted of three classes (**1** for positive class, **0** for negative class and **-1** for undefined). Therefore **average = "macro"** for **f1_score** from **scikit** was used.

Despite that, it is still possible to compute binary F1 if we interpret undefined class as missclassification; this is how the values presented in the table were obtained.

Macro F1 was also calculated for all standard models so as to enable comparison with lazy classifiers.

### Low metrics in isr dataset

Accuracy and F1-scores are relatively low in the isr dataset. This is explained by the fact that the obtained dataset contains duplicates over features but not over target, which lowers the possible upper bound for scores.  

### Binarized Binary Classifier	and Pattern Binary Classifier performance

Although all data was categorical and pattern classifier could not form numerical intervals, Binarized Binary Classifier had worse performance than Pattern Binary Classifier in case of cov dataset. It is due to the lack of columns corresponding to absense of symptoms. Suppose that, for example, patients with positive class mostly do not get headaches. This regularity would not be noticed by the Binarized Binary Classifier, whereas Pattern Binary Classifier would consider that. This assumption is confirmed if we add columns corresponding to absense of symptoms (no symptom -> True) and run Binarized Binary Classifier. The results turn out to be exactly the same as in Pattern Binary Classifier.

Judging by the metrics, the performance of Pattern Binary Classifier is comparable to the performance of the other models. And, therefore, this model could be used for non-educational purpuses. Binarized Binary Classifier could be used for non-educational purposes as well, provided that the categorical features have negative counterparts when required.
