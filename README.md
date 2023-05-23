# deep-learning-challenge
### Challenge Summary:

For this challenge, the nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. Using machine learning and neural networks, create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.

From the Alphabet Soup's business team, I received a CSV file containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization. These include: 


EIN and Name - identification columns

APPLICATION_TYPE - Alphabet Soup application type

AFFILIATION - Affiliated sector of industry

CLASSIFICAITON - Government organization classification

USE_CASE - Use case for funding

ORGANIZATION - Organization type

STATUS - Active status

INCOME_AMT - Funding amount requested

IS_SUCCESSFUL - Was the money used effectively

### Preprocess the Data

Using Google Colab, I read in the charity_data.csv to a Pandas DataFrame to view the data. In reviewing the data, I determined that I would use 'IS_SUCCESSFUL' for my Target variable andthe other columns for my features variable. Since, I do not need the 'EIN'or 'NAME' columns for my model, I dropped them. I then sorted through the data to look at number of unique values and for those colums with more than 10 unique values, I choose a cutoff point to bin "rare" categorical variables together in a new value, <Other>.

Once columns were organized, I then used 'pd.get_dummies()'to encode categorical variables and split the preprocessed data into a features array, 'X', and a target array,'y'. Using these arrays and the 'train_test_split' function, I split the data into training and testing datasets. To ensure that data is not heavily weighted in any one area, I scaled the training and testing feature datasets by creating a 'StandardScaler' instance, fitting it to the training data, then used the 'transform' function.
  
### Compile, Train and Evaluate the Model
Now that the data has been preprocessed, I can create a neural network model by assigning the number of input features and nodes for each layer using TensorFlow and Keras. 
To begin, I created the first hidden layer, added a second hidden layer and an output layer. 

![image](https://github.com/SheTroxel/deep-learning-challenge/assets/117420486/c8b72935-5240-4ea7-8cfb-624f7e0b3c9a)

I then checked the structure of the model, created a callback that saves the model's weights every five epochs.

Using the test data, I evaluated the model to determine the loss and accuracy. Then I exported the results to an HDF5 file.

### Optimizing the Model
For this challenge, we were asked to optimize the model to achieve a target predictive accuracy higher than 75%. I copied over the details from the original colab notebook file to a new file to begin my optimization process. This file can be found here.
![AlphabetSoupCharityOptimized.ipynb](https://github.com/SheTroxel/deep-learning-challenge/blob/main/AlphabetSoupCharityOptimized.ipynb) 

To begin, I looked at the initial data brought into the pandas DataFrame from the csv file to determine if any additional data could be dropped or further binned. 

  *The STATUS column determines if the project is active or not. Since activation doesn’t directly determine if a past or current project is      successful,  I dropped this column along with the EIN and NAME columns.

  *I also increased the ‘app_count’ to < 1000   to increase the number of applications to be included in the OTHER category. 


Next, I continued through the code to determine if I wanted to make any further adjustments before moving on to the Optimizing the model section of the notebook. I did not change anything further.

### The Optimized Model 
To find the best model parameters for this data set, I used a Sequential model with hyperparameter options to help determine what would be the ideal model for our target and features data. Using hyperparameter options allows Kerastuner to decide which activation function to use in hidden layers, how many neurons to include in the first layer, the number of hidden layers and neurons in the hidden layers. 

 

                                             
                                             
                                             
I then compiled the model, used a kerastuner library, and ran kerastuner to search for best hyperparameters.

 

 

Determined the best hyperparameters:
 
  
The optimized model did not achieve an accuracy of 75% or higher. This challenged me to explore a couple other options. Using the initial colab notebook, I created several notebooks to see if other options could bring our accuracy to 75% or higher. 


I did not achieve a target predictive accuracy score of 75% or higher on any of the additional model optimizations. 

### More Optimizations
 
Determined to see if I could reach a target predictive accuracy score above 75%, I created three additional colab notebooks based on the initial colab notebook: AlphabetSoupCharity.ipynb

AlphabetSoupCharityOptiizedV1 
As in my first optimization, I dropped the STATUS column, and I increased the ‘app_count’ to < 1000   to increase the number of applications to be included in the OTHER category. 

For my model, I added 3 hidden layers each using 5 neurons and a Relu activation. I then complied and fit my model increasing epochs from 50 to 100. I then evaluated the model using the test data and received an accuracy sore of 73.06%

 


AlphabetSoupCharityOptiizedV2

This model is like the AlphabetSoupCharityOptimizedV1, with the only change being to the hidden layers. I increased the number of hidden layers to 5 using 5 neurons for each layer.  This actually reduced our accuracy score to 72.97 %

 
  
OneHotEncoder optimization model:

After adding layers, I looked at using 'OneHotEncoder' mostly out of curiosity. However, in seeing that it derives the categories based on the unique values in each feature and creates a binary column - I thought it might be helpful especially with the many categories that are present in our features array. Sadly, it did not do anything that improved accuracy of our model but it was fun to try.

 

