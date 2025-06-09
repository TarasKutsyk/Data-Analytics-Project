Functionality of Data class:

Name of file with data is putted in class under self.DataName. Make sure that you have dataset file in the same folder in which you have your working file.

There are 5 optional parameters:
- DropCol (DropCol = None): a list of names of columns to be deleted. Do not put column 'car'. It is drop in NaN preprocessing.
- EncConfig (EncConfig = None): encoding conficuration. The are some possible input:
    - If not defined: there is no endcoding included.
    - If EncConfig = 'OneHot': all categorical features are encoded using OneHot encoding.
    - If EncConfig = 'Num': all categorical features are encoded in 0,1,2... way.
    - If e.g. EncConfig = {'Name of Atr1': 'OneHot', 'Name of Atr2': 'Num'}: Atr1 is encoded in OneHot, Atr2 in encoded in 0,1,2... way and the rest of columns are not encoded.
- TempType (TempType = 'Cat'): 'temperature' column type. Since it only has 3 values: 30, 55, 80 we can treat it as categorical type. There are 2 options:
    - If TempType = 'Cat': this column is treated as categorical type.
    - If TempType = 'Num': this column is treated as numerical type.
- TempScal (TempScal = 'Robust'): define the way of standardization of 'temperature' column if it is numerical type. There 2 option of standardization:
    - If TempScal = 'Robust': standardization via quartiles.
    - If TempScal = 'Standard': standardization via mean value and standrad deviation.
  - DropSpCol (DropSpCol = True): there is one column, that is 'toCoupon_GEQ5min' column that have only one binary value 1. Default value is True -> it is automically removed.

Parameters must be defined at the moment of creating the Data class instance. See example in Data_class.ipynb file.
 
Main function in Data class is fit() fucntion. See example in Data_class.ipynb file.

Remark on types of data: There are 4 list with listed columns of Categorical, Categorical with order, Binary or Numerical type.

Remark on OneHot endcoding: Replace old column with new columns with OneHot encoding vector.
The new columns are now named after their original values, e.g. `destination_Work` instead of `destination_1` 

Remark on 0,1,2... encoding: For columns of Categorical with order, this type encoding is fixed.

Remark on NaN values: 'Car' column is unconditionally removed since it consists primarily of NaNs. Special column (`toCoupon_GEQ5min`) is removed by default since it has only one binary value 1.
New change: if ImputeMissing=True is specified (default False), the remaining NaNs **are imputted instead of being dropped**. This might be beneficial since the remaining NaNs are not many and we don't have a lot of data to begin with.

### [Marcin] 
I will check how removing some rows with low frequency in columns will implied on dataset, and write which rows with which feature in which column could be removed.



### [Taras] My suggestions for improvement
[I can do some of this later if needed]
- It looks that currently the 'occupation' column is missing. I can understand if we decide to remove it because of how many unique values with low frequency it has:
```
--- occupation ---
                                           count  proportion
                                                  
Unemployed                                  1870    0.147430
Student                                     1584    0.124882
Computer & Mathematical                     1408    0.111006
Sales & Related                             1093    0.086172
Education&Training&Library                   943    0.074346
Management                                   838    0.066067
Office & Administrative Support              639    0.050378
Arts Design Entertainment Sports & Media     629    0.049590
Business & Financial                         544    0.042889
Retired                                      495    0.039026
Food Preparation & Serving Related           298    0.023494
Healthcare Practitioners & Technical         244    0.019237
Healthcare Support                           242    0.019079
Community & Social Services                  241    0.019000
Legal                                        219    0.017266
Transportation & Material Moving             218    0.017187
Architecture & Engineering                   175    0.013797
Personal Care & Service                      175    0.013797
Protective Service                           175    0.013797
Life Physical Social Science                 170    0.013403
Construction & Extraction                    154    0.012141
Installation Maintenance & Repair            133    0.010486
Production Occupations                       110    0.008672
Building & Grounds Cleaning & Maintenance     44    0.003469
Farming Fishing & Forestry                    43    0.003390
```
But I'd like to experiment with adding at least most frequent occupations here (Unemployed, Student etc.) We can do this by discarding the occupations that are less than specified frequency (e.g. 0.01, discarding the last 3 rows above) and applying one-hot encoding to the remaining ones.

### Other notes
[Not necessarily need fixing, just so that we remember]
- If the dictionary is specified for "EncConfig", all the categorical columns must be provided as keys, otherwise they are not encoded. 
