# Main.ipynb notebook
## Functionality of Data class

Name of file with data is putted in class under self.DataName. Make sure that you have dataset file in the same folder in which you have your working file.

There are 5 optional parameters:
- DropCol (DropCol = None): a list of names of columns to be deleted. Do not put column 'car'. It is drop in NaN preprocessing.
- DropRow (DropRow = None): a list of tupeles: [(column, value), ...] which must be removed from data.
- DropRowEpsilon (DropRowEpsilon = 0): if DropRowEpsilon > 0, then removed all (column, value) rows where the frequency of value in data is less than epsilon.
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
- ImputeMissing (ImputeMissing = False): if ImputeMissing = True, then the rows with NaN values are imputted with modes (for categorical or binay values) or median (for numerical values).

Parameters must be defined at the moment of creating the Data class instance. See example in Data_class.ipynb file.
 
Main function in Data class is fit() fucntion. See example in Data_class.ipynb file.

Remark on types of data: There are 4 list with listed columns of Categorical, Categorical with order, Binary or Numerical type.

Remark on OneHot endcoding: Replace old column with new columns with OneHot encoding vector.
The new columns are now named after their original values, e.g. `destination_Work` instead of `destination_1` 

Remark on 0,1,2... encoding: For columns of Categorical with order, this type encoding is fixed.

Remark on NaN values: 'Car' column is unconditionally removed since it consists primarily of NaNs. Special column (`toCoupon_GEQ5min`) is removed by default since it has only one binary value 1.

Remark on epsilon value: putting DropRowEpsilon = 0.01 you are using 3% of data.


### Other notes
- If the dictionary is specified for "EncConfig", all the categorical columns must be provided as keys, otherwise they are not encoded. 

## Models training
Then, in the subsequent "Decision tree" and "Linear regression, SVM and neural networks" sections of the Main.ipynb notebook, we train and compare different classification models, and also perform hyperparam optimization for Decision Trees and Neural networks.