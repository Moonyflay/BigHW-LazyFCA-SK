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
        <td>0.3522</td>
        <td>0.3490</td>
        <td>0.3467</td>
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
        <td>0.6029</td>
        <td>0.6815</td>
        <td>0.5751</td>
    </tr>
    <tr>
        <th>Complement Naive Bayes</th>
        <td>0.3577</td>
        <td>0.3495</td>
        <td>0.3546</td>
        <td>0.9360</td>
        <td>0.8651</td>
        <td>0.9115</td>
        <td>0.8947</td>
        <td>0.9348</td>
        <td>0.8261</td>
    </tr>
    <tr>
        <th>Decision Tree</th>
        <td>0.3493</td>
        <td>0.2666</td>
        <td>0.3343</td>
        <td>0.9520</td>
        <td>0.8958</td>
        <td>0.9323</td>
        <td>0.9484</td>
        <td>0.9695</td>
        <td>0.8989</td>
    </tr>
    <tr>
        <th>Random Forest</th>
        <td>0.3335</td>
        <td>0.2816</td>
        <td>0.3099</td>
        <td>0.9540</td>
        <td>0.8997</td>
        <td>0.9349</td>
        <td>0.9440</td>
        <td>0.9674</td>
        <td>0.8840</td>
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
