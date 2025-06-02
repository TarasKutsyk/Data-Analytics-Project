Functionality of Data class:
Name of file with data is putted in class under self.DataName. Make sure that you have dataset file in the same folder in which you have your working file.

There are 2 optional parameters:
- DropCol: a list of names of atrributes to be deleted. Do not put atrribute 'car'. It is drop in NaN preprocessing.
- EncConfig: encoding coficuration. The are some possible unput:
    - If not defined: there is no endcoding included.
    - If EncConfig = 'OneHot': all categorical features are encoded using OneHot encoding.
    - If EncConfig = 'Num': all categorical features are encoded in 0,1,2... way.
    - If e.g. EncConfig = {'Name of Atr1': 'OneHot', 'Name of Atr2': 'Num'}: Atr1 is encoded in OneHot, Atr2 in encoded in 0,1,2... way and the rest of atributes are not encoded.

Parameters must be defined at the moment of creating the Data class instance. See example in Data_class.ipynb file.
 
Mail function in Data class is fit() fucntion. See example in Data_class.ipynb file.

Remark on OneHot endcoding: Since the list od Series type cannot be the element of DataFrame, I had put the result of OneHot as string. If you want it can be changed e.g. on more colums of numerical type i.e. column 'weather' which has 3 features can be transform into 3 columns accordingly to OneHot encoding. Or I can do diffrently.

Remark on Categorical features: At this moment the Catergorical features are the Dtype: object type values. I will check it with description of data and if needed I will cahnge this.
