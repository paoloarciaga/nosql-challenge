# NoSQL Challenge

This repo consists of two jupyter notebooks where I evaluated Eat Safe, Love's ratings data in order to help their journalists and food critics decide where to focus future articles. 

I referenced the exercises from week 12 to complete this challenge. I also utilized an askBCS tutor who helped edit my code for question 3, during my exploratory analysis. 

## Part 1: Database and Jupyter Notebook Set Up
In this section of my Arciaga_NoSQL_Setup notebook, you'll see how I completed the following: 
- Included the mongoimport command text you used to import establishments.json in a markdown cell at the beginning of your Jupyter notebook file 
- The mongoimport command text dropped any existing establishments collection before importing establishments.json into MongoDB 
- The database is named uk_food and the collection is named establishments 
- Imported PyMongo and Pretty Print 
- An instance of the Mongo Client was created 
- Listed the databases you have in Mongo, which includes uk_food 
- Listed the collection(s) in the uk_food database, which includes establishments in the output 
- Used find_one() and pprint to display one document in the establishments collection 
- The establishments collection was assigned to a variable

## Part 2: Updating the Database
In the second section of my Arciaga_NoSQL_Setup notebook, you'll see how I completed the following: 
- The supplied data for the "Penang Flavours" restaurant was inserted into the establishments collection 
- A query was performed to find the BusinessTypeID for "Restaurant/Cafe/Canteen" and returned only the BusinessTypeID and BusinessType fields 
- The "Penang Flavours" document was updated with the correct value for BusinessTypeID 
- A query was performed to delete all the documents in the collection where "Dover Local Authority" is the value for LocalAuthorityName 
- A count_documents() check was performed before and after the removal of the Dover documents to ensure the documents were removed 
- An update_many() query was performed to convert the latitude and longitude fields from strings to decimal numbers and RatingValue to integers

## Part 3: Exploratory Analysis 
In my Arciaga_NoSQL_Analysis notebook, you'll see how I completed the following: 
- Question 1: Which establishments have a hygiene score equal to 20? 
  - A query was performed to find the establishments with a hygiene score of 20 
  - count_documents() was used to list the number of documents (answer: 41) 
  - The first result was printed using pprint 
  - The results were converted to a Pandas DataFrame and displays the first 10 rows 
- Question 2: Which establishments in London have a RatingValue greater than or equal to 4? 
  - A query was performed to find the establishments in London with a RatingValue greater than or equal to 4 
  - The query used the $regex operator to locate the London establishments 
  - count_documents() was used to list the number of documents (answer: 33) 
  - The first result was printed using pprint 
  - The results were converted to a Pandas DataFrame and displays the first 10 rows 
- Question 3: What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"? 
  - A query was performed to find the establishments within 0.01 degree of the "Penang Flavours" restaurant
  - The query also limited the results to establishments with a RatingValue of 5 
  - The query used the sort() method in PyMongo to sort in ascending order on the hygiene score 
  - The query used the limit() method in PyMongo to limit the results to 5 
  - All five results were printed using pprint 
  - The results were converted to a Pandas DataFrame and displayed 
- Question 4: How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas. 
  - An aggregation pipeline was built to include a match query, group, and sort 
  - The match query matched documents with a hygiene score of 0
  - The group step of the pipeline was grouped on LocalAuthorityName and counts the number of documents 
  - The sort step of the pipeline sorted the count of the documents in descending order 
  - The aggregation pipeline was sent to the aggregate() method 
  - The results from the aggregation query was casted as a list and then saved to a variable 
  - The first ten results were printed using pprint 
  - The results were converted to a Pandas DataFrame and displays the first 10 rows 
