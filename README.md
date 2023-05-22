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
For this challenge, we were asked to optimize the model to achieve a target predictive accuracy higher than 75%. To begin, I started by adding additional layers to see if that might provide a higher predictive accracy score. I then looked at the initial data to determine if any additional data could be binned or removed. 

First optimization model:
  
I removed the STATUS column, adding layers for a second model. Each layer had 5 nodes. 

  
Second optimization model: 
  
I added two more hidden layers to the second model, to see if that might help to improve target predictive accuracy score 

  
OneHotEncoder optimization model:
After adding layers, I looked at using 'OneHotEncoder' mostly out of curiousity. However, in seeing that it derives the categories based on the unique values in each feature and creates a binary column - I thought it might be helpful with the many categories that are present in our features array. Sadly, it did not do anything that provide improvement to our model but it was fun to try it out.

Optimized Model:
In a classroom activity, we created a method that created a new Sequential model with hyperparameter options, allowed kerastuner to decide which activation function to use in hidden layers, and allowed Kerastuner to decide number of hidden layers and neurons in hidden layers. I wanted to use this approach on this model to determine if hyperparameter options and kerastuner could provide a model that would improve the target predictive accuracy score. 
  

 After trying several attempts to improve target predictive accuracy, I was not able to achieve a 75% target predictive accuracy.
