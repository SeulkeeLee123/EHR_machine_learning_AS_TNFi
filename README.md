# Machine learning to predict early TNF inhibitor users in patients with ankylosing spondylitis

This is the repository for the article submitted to Scientific Reports. The title is 'Machine learning to predict early TNF inhibitor users in patients with ankylosing spondylitis'. We compared various machine learning methods to predict the target population for the early use of TNF inhibitors in AS using baseline characteristics. 


## Environment setting

### Installing miniconda:

We recommend using miniconda as a package manager when executing these codes. Miniconda can be installed from the following link: https://docs.conda.io/en/latest/miniconda.html

### Environment setting:

All software tests were done under the following environment setting, and we highly recommend making the miniconda environment to test codes.

```
python 3.7.5
numpy 1.18.0
keras 2.3.1
tensorflow 2.0.0
sklearn 0.22
xgboost 1.1.0
```

## Input file preparation

* Input file **should** be located in the same folder with codes, and the name has to be 'data_file.txt'.
* Input file **must** be a tab delimited text file.
* Input file **should** include a header row.
* The first column **should** be a ID of each patient, and the last column **should** be a group of each patient (early TNF users or not).
* We recommend the same variables we used, or you have to change the number of index in each code according to the number of variables in your own dataset.
* Our original input data includes WBC count, hemoglobin, platelet count, AST, ALT, BUN, creatinine, ESR, CRP, age, sex, HLA-B27 positivity, weight, and height.

Example (All values in this example are virtual.):
```
ID  WBC	Hb	Plt	AST	ALT	BUN	Cr	ESR	CRP	age	sex	HLA	Wt	Ht	group
AS001	3.44	15.5	186	28	30	12.2	0.85	7	0.11	19.90	0	1	65	173.5	0
AS002	10.52	13.4	237	27	12	9.8	0.85	88	3.99	41.95	0	1	69	164	1
AS003	2.58	14.8	461	19	19	10.1	0.95	19	0.25	25.13	0	1	75	185	0
AS004	15.28	15.1	207	37	22	10.7	0.85	17	0.19	22.87	0	1	89	172	0
AS005	7.73	12.9	176	24	11	15.9	0.76	33	0.22	28.14	1	1	45.4	165.6	1
AS006	9.82	11.3	264	11	11	28.8	1.24	72	1.88	38.63	1	1	50.15	160.6	1
AS007	5.65	13.1	156	29	28	16.3	0.47	3	0.42	37.51	0	1	90.95	168.4	0
```

## (Optional) Input file modification
If you want to change the input variables, be aware that part of code has to be changed according the form of the data (categorical: integer, continuous: float). 
```
# The number of index has to be changed according to the number of features in your data.
for line in whole_data:
    featDic[line[0]] = list(map(float,line[1:11])) + list(map(int,line[11:13])) + list(map(float,line[13:15])) + list(map(int,line[15]))
```
* line[x]: x means the index number of each column.

* If you want to change the name of input file or directory, you may change this part of code to your own input file.
```
path_to_data_file = 'PATH/TO/DATA/FILE'
```

## Comparing analysis & hyperparameter tuning
### ANN, RF, XGBoost
The three codes below were used for the hyperparameter tuning and comparing analysis.
```
001-2_run_ANN_hyperparameter_tuning.ipynb
002-2_run_RF_hyperparameter_tuning.ipynb
003-2_run_XGBoost_hyperparameter_tuning.ipynb
```

Those codes actually execute the codes below.
```
001_ANN_hyperparameter_tuning.ipynb
002_RF_hyperparameter_tuning.ipynb
003_XGBoost_hyperparameter_tuning.ipynb
```

The performance of each execution will be saved the files below.
```
'ANN_hyperparameter_tuning.txt'
'RF_hyperparameter_tuning.txt'
'XGBoost_hyperparameter_tuning.txt'
```

Performances from each iteration will be saved independently. You have to compare the performances of each hyperparameter after combining all three iterations.

### Logistic regression, SVM
The two codes below were used for the comparing analysis only. 
```
004-2_run_logistic_performance.ipynb
005-2_run_SVM_performance.ipynb
```

Those codes actually execute the codes below.
```
004_logistic_regression_performance.ipynb
005_SVM_performance.ipynb
```

The performance of each execution will be saved the files below.
```
'logistic_hyperparameter_tuning.txt'
'SVM_hyperparameter_tuning.txt'
```
Unlike ANN, RF, and XGBoost, the two files only include performances of each iteration. 

## Finding best model



## Change the path of input and output files of the codes.

* The path of input and output files **must** be changed according to the individual environment.

The six codes below has the same categories to be changed.
```
001_ANN_hyperparameter_tuning.ipynb
002_RF_hyperparameter_tuning.ipynb
003_XGBoost_hyperparameter_tuning.ipynb
004_random_performance.ipynb
005_logistic_regression_performance.ipynb
006_SVM_performance.ipynb
```

You have to change the 
```
path_to_data_file = 'PATH/TO/DATA/FILE'
performance_file = 'PATH/TO/PERFORMANCE/FILE'
```

