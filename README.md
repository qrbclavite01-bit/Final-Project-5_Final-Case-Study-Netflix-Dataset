# Final-Project-5_Final-Case-Study-Netflix-Dataset

Name: Hyrum Bordeos, Renz B. Clavite, Justine Cris B. Demeterio, James Allen E. Lozano, & Adrian Lyle M. Tapel

Course & Section: CPE 310 - IE22S1

Course Name: Fundamentals of Data Science

Date: April 19, 2026 

Guide Questions

Here is a guide that you may use to bring structure to your analysis:

 
    Data Loading & Overview. Load the CSV into a DataFrame. What are its dimensions (.shape)? Display the first and last five rows. What insights do you immediately notice about the columns?

   
    Data Cleaning. Which columns contain missing values? How might you handle missing entries? Drop them or fill with a placeholder?

 
    Data Types & Conversion. Check each column’s data type. Are there any that you need to convert (like date to datetime type)?


    Univariate Analysis. How many Movies vs. TV Shows are there? What are the top five most common ratings? Which release year appears most frequently?


    Duration & Seasons. Parse duration into numeric minutes (for movies) and number of seasons (for shows). What is the average movie length? The average number of seasons per TV show?


 
    Genre Analysis. Which genre has the highest average release year? What might that indicate?


    Temporal Trends. Are there spikes or drops? Compare release_year vs. year_added: how long after release does Netflix typically acquire content?

 
    Rating vs. Type. Create a cross-tab or pivot table of type vs. rating. Which rating dominates movies compared to TV shows?

 
    Filtering & Querying. Extract all titles with rating “R” added after 2020. How many?


    Aggregations & GroupBy. For each country, compute the average release year of its titles. Group by year_added and compute the proportion of Movies vs. TV Shows added each year.


    Applying Functions. Write a function that, given a director’s name, returns their titles sorted by release_year. Create a reusable function to plot the top N categories for any categorical column.




**--------------------------------------------------------------------------------------------------------------------------------**


**Data Loading & Overview. Load the CSV into a DataFrame. What are its dimensions (.shape)? Display the first and last five rows. What insights do you immediately notice about the columns?**

from google.colab import drive
drive.mount('/content/drive')


import pandas as pd

df = pd.read_csv('/content/netflix_titles.csv')


df.shape

df


Data Cleaning. Which columns contain missing values? How might you handle missing entries? Drop them or fill with a placeholder?


df.isnull().sum()


df['director'] = df['director'].fillna('Unknown')
df['cast'] = df['cast'].fillna('Unknown')
df['country'] = df['country'].fillna('Unknown')


df = df.dropna(subset=['date_added', 'rating', 'duration'])




