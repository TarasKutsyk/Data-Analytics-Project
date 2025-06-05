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

Remark on OneHot endcoding: Since the list od Series type cannot be the element of DataFrame, I had put the result of OneHot as string. If you want it can be changed e.g. on more colums of numerical type i.e. column 'weather' which has 3 features can be transform into 3 columns accordingly to OneHot encoding. Or I can do diffrently.

Remark on types of data: there are 3 list with listed columns of Cotegorical, Binary or Numerical type.
