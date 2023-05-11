**Mohan's Review**

data.py

In get_data function extracted the data from the API in json format.

Created a Spark Session and then created a rdd of the data from extracted from API.

In create_and_clean_df function cleaned the data, created a schema and finally created a dataframe from the schema and rdd.

In csv_file function user can download the results of each query in csv file.

For finding most affected state, sorted the Death/Total_cases in descending order and limit the result by 1 and selected the state column from the result.

For finding least affected state, sorted the Death/Total_cases in ascending order and limit the result by 1 and selected the state column from the result.

For finding state with most cases, sorted the total_cases column in descending order and limit the result by 1 and selected the state column from the result.

For finding state with least cases, sorted the total_cases column in ascending order and limit the result by 1 and selected the state column from the result.

For finding the total cases across all states, aggregated the sum of total_cases column.

For finding most cured state, sorted the Cured/Total_Cases in descending order and limit the result by 1 and selected the state column from the result.

For finding least affected state, sorted the Cured/Total_Cases in ascending order and limit the result by 1 and selected the state column from the result.

At last stored the result of each query in a python list.

app.py

In app.py created a Flask app and inside it created the routes for all the queries used in data.py and retured the output in json format.

**Ashwat's Review**


In dataframe.py file he created the following functions:

He created getDataFromUrl() function which uses the requests library to make a GET request to an API endpoint for COVID-19 data in India. The response is returned as a JSON object.

He then created trimCheck() function that takes a state name as a string and removes the "*" character if it is present. This is used to clean up some state names that have an asterisk in them.

He created cleanData() function that takes the JSON object returned by trimCheck() and processes it into a list of lists. Each inner list contains data for a single state: the serial number, state name, number of confirmed cases, number of cured cases, number of deaths, and total number of cases.

Lastly he created getDataFrame() function that takes the list of lists returned by cleanData() and converts it into a PySpark DataFrame. This is done by creating a PySpark RDD from the list of lists, converting each inner list into a Row object, defining a schema for the DataFrame using StructType, and using spark.createDataFrame() to create the DataFrame.

The app.py file was created to display the results

He imported the dataframe created in dataframe.py.

Then he wrote queries to get the required data and created endpoints to display them.
