# OSDA Big Homework
## Option - Lazy FCA
[Lazy FCA library](https://github.com/AndrewDiv/FCALC)

### Datasets:
1. [Israel's Covid-19 Dataset for Year 2020 & 2021](https://www.kaggle.com/datasets/mykeysid10/covid19-dataset-for-year-2020) (isr)
2. [COVID, FLU, COLD Symptoms](https://www.kaggle.com/datasets/walterconway/covid-flu-cold-symptoms) (cfc)
3. [Symptoms and COVID Presence (May 2020 data)](https://www.kaggle.com/datasets/hemanthhari/symptoms-and-covid-presence) (cov)

### Standard Mosels
In this HW assignemnt the following standard models are used:
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
        <td>37</td>
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
        <td>2.301</td>
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
        <td>0.2310</td>
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
        <td>0.001</td>
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
        <td>8</td>
        <td>8</td>
        <td>gini</td>
        <td> </td>
        <td>6</td>
        <td>2</td>
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
        <td>10</td>        
        <td>2</td>        
        <td>gini</td>        
        <td>40</td>
        <td>2</td>
        <td>6</td>
        <td>gini</td>
        <td>40</td>
        <td>6</td>        
        <td>6</td>        
        <td>gini</td>        
        <td>140</td>
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
        <td>standard</td>
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
        <td>standard</td>
        <td>0.00</td>
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
        <td>0.9520</td>
        <td>0.8945</td>
        <td>0.9317</td>
        <td>0.9633</td>
        <td>0.9784</td>
        <td>0.9281</td>
    </tr>
    <tr>
        <th>K-NN</th>
        <td>0.4751</td>
        <td>0.5811</td>
        <td>0.4367</td>
        <td>0.9320</td>
        <td>0.8462</td>
        <td>0.9012</td>
        <td>0.9376</td>
        <td>0.9637</td>
        <td>0.8679</td>
    </tr>
    <tr>
        <th>Multinomial Naive Bayes</th>
        <td>0.3631</td>
        <td>0.3545</td>
        <td>0.3564</td>
        <td>0.9340</td>
        <td>0.8423</td>
        <td>0.9003</td>
        <td>0.8668</td>
        <td>0.9255</td>
        <td>0.6488</td>
    </tr>
    <tr>
        <th>Gaussian Naive Bayes</th>
        <td>0.3633</td>
        <td>0.3643</td>
        <td>0.3609</td>
        <td>0.9540</td>
        <td>0.8997</td>
        <td>0.9349</td>
        <td>0.9634</td>
        <td>0.9782</td>
        <td>0.9313</td>
    </tr>
    <tr>
        <th>Complement Naive Bayes</th>
        <td>0.3577</td>
        <td>0.3562</td>
        <td>0.3542</td>
        <td>0.9540</td>
        <td>0.8997</td>
        <td>0.9349</td>
        <td>0.9269</td>
        <td>0.9576</td>
        <td>0.8430</td>
    </tr>
    <tr>
        <th>Decision Tree</th>
        <td>0.3493</td>
        <td>0.2666</td>
        <td>0.3343</td>
        <td>0.9540</td>
        <td>0.8997</td>
        <td>0.9349</td>
        <td>0.9506</td>
        <td>0.9045</td>
        <td>0.9708</td>
    </tr>
    <tr>
        <th>Random Forest</th>
        <td>0.3851</td>
        <td>0.3390</td>
        <td>0.3724</td>
        <td>0.9540</td>
        <td>0.8997</td>
        <td>0.9349</td>
        <td>0.9420</td>
        <td>0.9659</td>
        <td>0.8829</td>
    </tr>
    <tr style ="border-top: 1px solid #ddd">
        <th>Binarized Binary Classifier</th>
        <td>0.4372</td>
        <td>0.4949</td>
        <td>0.3823</td>
        <td>0.7300</td>
        <td>0.5469</td>
        <td>0.5297</td>
        <td>0.8432</td>
        <td>0.9134</td>
        <td>0.5422</td>
    </tr>
    <tr>
        <th>Pattern Binary Classifier</th>
        <td>0.4367</td>
        <td>0.4363</td>
        <td>0.3875</td>
        <td>0.9200</td>
        <td>0.8338</td>
        <td>0.8905</td>
        <td>0.9354</td>
        <td>0.9612</td>
        <td>0.8811</td>
    </tr>

</table>

Note that for lazy classifiers it was impossible to use **f1_score** from **scikit** with **average = "binary"**, as the output consisted of three classes (**1** for positive class, **0** for negative class and **-1** for undefined). Therefore **average = "macro"** for **f1_score** from **scikit** was used.

Despite that, it is still possible to compute binary F1 if we interpret undefined class as missclassification.

Macro F1 was also calculated for all standard models so as to enable comparizon with lazy classifiers.
