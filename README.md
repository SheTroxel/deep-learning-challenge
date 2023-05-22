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

Using Google Colab, I read in the charity_data.csv to a Pandas DataFrame to view the data. In reviewing the data, I determined that I would use <IS_SUCCESSFUL> for my Target variable andthe other columns for my features variable. Since, I do not need the <EIN> or <NAME> columns for my model, I dropped them. I then sorted through the data to look at number of unique values and for those colums with more than 10 unique values, I choose a cutoff point to bin "rare" categorical variables together in a new value, <Other>.

Once columns were organized, I then used <pd.get_dummies()> to encode categorical variables and split the preprocessed data into a features array, <X>, and a target array,<y>. Using these arrays and the <train_test_split> function, I split the data into training and testing datasets. 



