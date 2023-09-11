# Crowdfunding_ETL
#### Project 2: Crowdfunding_ETL
#### Collaborators: Nathan-Andrew Tompkins and Luis Norda

## Create the Category and Subcategory DataFrames
- These dataframes were created using the Numpy library. Using the str.split() function we split the category/subcategory series into two separate series called Category and Subcategory. Using the Numpy library we added a signifying number to make sure that each category had an assigned value. Example: "cat5", or "subcat8".
- We exported these as two separate CSV files.
## Create the Campaign DataFrame
 - The campaign dataframe was created by reading in the crowdfunding.xlsx file and setting it to a dataframe. We then joined the category and subcategory dataframes we created above to this dataframe and dropped the unneeded columns, renamed others, and changed the datatypes of some.
 - We exported this as a CSV file.
## Create the Contacts DataFrame
#### We read in the contacts.xlsx file so that the values were inserted into a dataframe. We used both options below.
 - #### Option 1: Use Python dictionary methods.
   - Imported the JSON library and used the .iterrows(), json.loads(), and .extend() functions within a for-loop to create a dictionary of values.
   - We used list-comprehensions to set the values of the dictionary to lists, then built a dataframe called contact_info that included the information from these lists. Further cleaning included splitting the first and last names into their own columns.
   - We exported the dataframe to a CSV.
 - #### Option 2: Use regular expressions.
   - We set the values to a list using the .tolist() function, then created a column of contact_id's by pulling the 4-digit string of numbers from each row using 'd\{4}' as the regex expression. We then changed that data type to an integer.
   - We subsequently created a column of names by pulling the string of characters from each row using '[A-Z][a-z]+\s[A-Z][a-z]+' OR '\w+\s\w+'  as the regex expression.
   - We lastly created a column of emails by pulling the string of characters from each row using '[\w+\$+-^]+\.[\w+\$+-^]+\@[\w+\$+-^]+\.\w+' as the regex expression. We then looped through the name column and split the names into First and Last, like we did in option 1.
   - We exported the dataframe to a CSV.

### Create the Crowdfunding Database
 - We used the QuickDBD webapp to build an ERD based on the CSVs we exported in the previous steps, identifying primary and foreign keys. We used the export of this ERD to create the tables within a new SQLDatabase called crowdfunding_db, then imported each CSV into each newly created table, using the SELECT * query to verify that each table was properly populated.
 - An erd.png of the ERD is included in this repo.
 - A schema.sql file is included in this repo.
