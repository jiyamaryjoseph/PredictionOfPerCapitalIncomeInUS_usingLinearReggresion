# linear-regression-single-variable (also using Libraries  of Pickle and joblib)
Here  I am using linear regression for single variable dataset.

## Pickle & sklearn Joblib 


                       Suppose you are working on a practice problem related to house rent given lots of data points and input features. It’s quite common to perform EDA, Preprocessing(may need to    create additional features), and feeding our data to our model. In this scenario even if we use the simplest Linear Regression Model (multiple variables) it may become huge in   size due to all the input_features and all the parameters which will be time-consuming to re-train again and again for use.


### Method 1 – Pickle – 2 Steps
Many of you will be familiar with the pickle module, however, if not it’s good to know that the pickle module allows you to pickle a file using de-serialization which means simply breaking down an object into its constituting components. For e.g, our model files attribute like the one we saw.

To save a file using pickle one needs to open a file, load it under some alias name and dump all the info of the model. This can be achieved using below code:

##### loading library
import pickle
##### create an iterator object with write permission - model.pkl
    with open("D:\\data\\model_pickleonLinearreg", 'wb')as f:
        pickle.dump(reg,f)
    
    
 #### One can load this file back again into a model using the same logic, here we are using the reg variable for referencing the model and then using it to predict the per capital income on the year of 2020

##### load saved model
    with open("D:\\data\\model_pickleonLinearreg", 'rb')as f:
       model=pickle.load(f)

##### check prediction
model.predict([[2020]]) # similar

## Benefits:

- The pickle module keeps track of the objects it has already serialized, so that later references to the same object won’t be serialized again, thus allowing for faster execution time.
- Allows saving model in very little time.
- Good For small models with fewer parameters like the one we used.

### Method 1 – Pickle – 2 Steps

Joblib is an alternative to model saving in a way that it can operate on objects with large NumPy arrays/data as a backend with many parameters. It can be used as an individual module(refer here) or using the Sci-Kit Learn library. For simplicity’s sake, we will be using the second method.

-> First, we will import joblib from sklearn’s external class 
#### loading dependency

##### from sklearn.externals import joblib
##### To save the model we will use its dump functionality to save the model to the model_jlib file.

##### saving our model # model - model , filename-model_jlib
         with open("D:\\data\\model_joblibonLinearreg",'wb')as f2:
              joblib.dump(reg,f2)e created with a filename and contents will be similar to the pickle file.
##### load saved model
After running the above code a file will be created with a filename and contents will be similar to the pickle file.

         with open("D:\\data\\model_joblibonLinearreg", 'rb')as f2:
              model2=joblib.load(f2)
##### check prediction
            model2.predict([[2020]] # similar
