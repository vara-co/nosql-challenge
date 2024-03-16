<h1>NoSQL Challenge</h1> (Using MongoDB and Jupyter Notebook)<br/>
<h2>DU - DA Module 12 challenge<br/>
Eat Safe, Love (UK Food Standards Agency ratings data, evaluation)<br/>
<br/>
by Laura Vara</h2><br/>
This is a work-in-progress project. If you want to see the finished result, please come back in one week, when this project is due. Thank you!<br/>

((ADD IMAGE HERE))
<br/>
NOTE: 

<h2>INDEX</h2><br/>

1. Content of the repository<br/>
2. Instructions for the NoSQL Challenge<br/>
3. References<br/>

Content of the repository
-----------------------------------------------------------
- Resources directory:
	- establishments.json  <-- JSON file to import via the instructions provided on the Jupyter Notebook NoSQL_setup_LMVS

- NoSQL_analysis_LMVS.ipynb <--
- NoSQL_setup_LMVS.ipynb <-- Jupyter Notebook file, with CRUD operations
    
<h2>Instructions for NoSQL UK Food Ratings</h2><br/>
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.<br/>

<h3>Part 1: Database and Jupyter Notebook Set Up</h3><br/>

Use **NoSQL_setup_starter.ipynb** for this section of the challenge.
1. Import the data provided in the **establishments.json** file from your Terminal. Name the database **uk_food** and the collection **establishments**. Copy the text you used to import your data from your Terminal to a markdown cell in your notebook.
2. Within your notebook, import the libraries you need: PyMongo and Pretty Print **(pprint)**.
3. Create an instance of the Mongo Client.
4. Confirm that you created the database and loaded the data properly:<br/>
	- List the databases you have in MongoDB. Confirm that **uk_food** is listed.
	- List the collection(s) in the database to ensure that **establishments** is there.
	- Find and display one document in the **establishments** collection using **find_one** and display with **pprint**.
5. Assign the **establishments** collection to a variable to prepare the collection for use.

<h3>Part 2: Update the Database</h3><br/>

Use **NoSQL_setup_starter.ipynb** for this section of the challenge.<br/>
The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. Make the following changes to the **establishments** collection:<br/>
1. An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis. Add the following information to the database:<br/>

![Part2Image_ReadMe](https://github.com/vara-co/nosql-challenge/assets/152572519/ddd6275e-1d76-4fba-8913-52db6f0d6cfe)

2. Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the **BusinessTypeID** and **BusinessType** fields.<br/>
3. Update the new restaurant with the **BusinessTypeID** you found.<br/>
4. The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority. Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.<br/>
5. Some of the number values are stored as strings, when they should be stored as numbers.<br/>
	1. Use **update_many** to convert **latitude** and **longitude** to decimal numbers.<br/>
 	2. Use **update_many** to convert **RatingValue** to integer numbers.<br/>

<h3>Part 3: Exploratory Analysis</h3><br/>

Eat Safe, Love has specific questions they want you to answer, which will help them find the locations they wish to visit and avoid.<br/>
Use **NoSQL_analysis_starter.ipynb** for this section of the challenge.<br/>
Some notes to be aware of while you are exploring the dataset:<br/>
* **RatingValue** refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.<br/>
	* **Note:** This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating. We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.<br/>
* The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.<br/>

Use the following questions to explore the database, and find the answers, so you can provide them to the magazine editors.<br/>
Unless otherwise stated, for each question:<br/>
* Use **count_documents** to display the number of documents contained in the result.
* Display the first document in the results using **pprint**.<br/>
* Convert the result to a Pandas DataFrame, print the number of rows in the DataFrame, and display the first 10 rows.<br/>
1. Which establishments have a hygiene score equal to 20?<br/>
2. Which establishments in London have a **RatingValue** greater than or equal to 4?<br/>
**Hint:** The London Local Authority has a longer name than "London" so you will need to use $regex as part of your search.<br/>
3. What are the top 5 establishments with a **RatingValue** of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?<br/>
**Hint:** You will need to compare the geocode to find the nearest locations. Search within 0.01 degree on either side of the latitude and longitude.<br/>
4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.<br/>
**Hint:** You will need to use the aggregation method to answer this.<br/>

![Part3Image_ReadMe](https://github.com/vara-co/nosql-challenge/assets/152572519/f00ff1a1-23a6-4659-ae23-4757fc6822a4)

<h2>References for NoSQL UK Food Ratings</h2><br/>
Most of what's in this challenge, was covered in class.<br/>
The few things that either weren't or I had to reference to, are described
with it's source right below.<br/>

- Bla:   <br/>
    - https:  <br/>
    
----------------------------------------------------------------------------------------------
