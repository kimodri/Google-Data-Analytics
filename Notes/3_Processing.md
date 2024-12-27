# Data Analysis: Processing
Kim Audrey Magan | 14/12/2024

# Objectives
**What do you need to know:**

The goal of processing is to ensure the integrity of data. That is being complete and correct. Finishing this, one must be able to:
- Clean data with spreadsheet and SQL
- Report the changes

# Steps
To sum things up, here the steps you can do in the processing phase

**Before Cleaning (Preprocessing)**

| **Step**          | **Description**                                                                                      |
|--------------------|------------------------------------------------------------------------------------------------------|
| 1. **Review data integrity** | Determine data integrity by assessing the overall accuracy, consistency, and completeness of the data. <br> > This will guide you on what to clean to ensure data integrity. |
| 2. **Check for sample size and sampling bias** | > This will guide you by ensuring you have enough volume of data and unbiased data to represent the population. |
| 3. **Evaluate data reliability** | > This will guide you to check if your data is reliable and thus worthy of cleaning/analysis. |
| 4. **Deal with insufficient data** | > This will guide you on what to do if your data is not enough. |
| 5. **Balance business objectives with data integrity** | > This ensures that your data processing does not conflict with the business problem you aim to solve. |

**During Cleaning (Processing)**

| **Step**          | **Description**                                                                                      |
|--------------------|------------------------------------------------------------------------------------------------------|
| 1. **Clean your data with the right tools (Excel or SQL)** | If you concluded that your data lacks integrity, clean common errors (e.g., null values, duplicates). |
| 2. **Report your cleaning results** | Reflect on whether the cleaned data aligns with business objectives. Create change logs for documentation etc. |

# Recall
Google course on data analytics:
There are **6 phases** for data analysis and this 6 phases are the coverage for this program and these are

| **Step**         | **Description**                                                                                                                                                 |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ~~**Asking**~~       | ~~Communicate with stakeholders about the problem to be solved. Ask relevant questions to narrow the focus of analysis. <br><br>~~~~**Example**: What are the possible data? What is the root problem/cause?~~ |
| ~~**Preparation**~~  | ~~Gather the data to analyze. It could be through surveys or past company data.~~                                                                                   |
| **Process**      | Manipulate the gathered data, such as removing outliers or filling nulls.                                                                                       |
| **Analyzing**    | Analyze the cleaned data to find patterns, if any.                                                                                                              |
| **Sharing**      | Share the findings using visualizations.                                                                                                                        |
| **Act**          | Recommend proper steps for the company to solve the problem based on the analysis.                                                                              |
# Steps in Depth
## Preprocessing:

Keep these things in mind, you are not cleaning yet!

### 1. Review Data Integrity
- **Data Integrity** - The accuracy, completeness, consistency, and trustworthiness of data throughtout its lifecycle (YOU WANT TO MAINTAIN THIS)

Data integrity can be compromised if the data is:

- Transferred
- Duplicated
- Manipulated


**To check for your data's integrity you can look at this for a guide (criteria) that makes them valid:**

| Data Constraint         | Definition                                                                                         | Examples                                                                                             |
|--------------------------|---------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| Data type               | Values must be of a certain type: date, number, percentage, Boolean, etc.                         | If the data type is a date, a single number like 30 would fail the constraint and be invalid.        |
| Data range              | Values must fall between predefined maximum and minimum values                                    | If the data range is 10-20, a value of 30 would fail the constraint and be invalid.                 |
| Mandatory               | Values can’t be left blank or empty                                                              | If age is mandatory, that value must be filled in.                                                  |
| Unique                  | Values can’t have a duplicate                                                                    | Two people can’t have the same mobile phone number within the same service area.                    |
| Regular expression (regex) patterns | Values must match a prescribed pattern                                                        | A phone number must match ###-###-#### (no other characters allowed).                               |
| Cross-field validation  | Certain conditions for multiple fields must be satisfied                                         | Values are percentages and values from multiple fields must add up to 100%.                        |
| Primary-key             | (Databases only) value must be unique per column                                                 | A database table can’t have two rows with the same primary key value.                               |
| Set-membership          | (Databases only) values for a column must come from a set of discrete values                     | Value for a column must be set to Yes, No, or Not Applicable.                                       |
| Foreign-key             | (Databases only) values for a column must be unique values coming from a column in another table | The State column must be a valid state or territory with the set of acceptable values in a States table. |
| Accuracy                | The degree to which the data conforms to the actual entity being measured or described           | If values for zip codes are validated by street location, the accuracy of the data goes up.         |
| Completeness            | The degree to which the data contains all desired components or measures                         | If data for personal profiles required hair and eye color, and both are collected, the data is complete. |
| Consistency             | The degree to which the data is repeatable from different points of entry or collection          | If a customer has the same address in the sales and repair databases, the data is consistent.       |

---
### 2. Check for Sample Size and Sampling Bias 

**Answers the question:** how much?

**Why is this important to learn?**
- This is important because with this knowledge you can know how much data you need to analyze if the entire dataset let's say span upto millions observations.
- And then remember that sometimes your data maybe insufficient, with this you'd know if you still need proxy or in that case how much proxy (will be explained under the "Deal with insufficient data)?

Let's say you were given a dataset, you can solve this problem simply by asking those who collected if they did a random sampling.

**How do I know that my data has a sampling bias?**

This is not answered by the course, but you can ask chatGPT with this one. Simply you can just compare the ratio of the features. If your population represents 50% of customers in the age 18-25 then your sample must reflect this.

When you are checking for the sampling bias on your data, here are the things to consider:
- Don't use sample size less than 30
- The confidence level most commonly used is 95 and 90%
- Sample sizes vary by business problem

#### 2.1. Determine the Best Sample Size:

Remember that samples vary based on problems.

- Know your confidence level
  - The probability that your sample accurately project the population
- Know your margin of error
    - The maximum amount the the sample results are expected to differ from those of the actual population
- Know your population

You can study the deeper statistics in here or just use the calculator:

http://www.raosoft.com/samplesize.html

---

### 3. Evaluate Data Reliability

How do you know that your analysis is reliable (refelcts the entire population)?
> It must have a low margin of error and a high confidence level

If you are the one to collect it is important for you to identify variables such as 
- marigin of error
- CL and what not

but if the data is given to you (you laready know the sample size) **you can just calculate the margin of error or CL*.

Now, this is important to know because you do not want to analyze a dataset with a large margin of error therefore you need to check it before analysis. 

>Maybe your margin of error is 20%, you don't want that so you report to the data engineers or stakeholders that you need more data to reflect the situation to the population.

example here: 
> Data engineers gathered data from a survey with a sample of people who work five-day workweeks (not the entire population).**You concluded that 60% of the sample prefers a four-day workweek.** This result represents only the sample, not the entire population.

> They said that they used a **10%** margin of error and that justifies their sample (at least according to them)

> This indicates the range within which the true population percentage is likely to fall. The range here is 50% to 70% (60% ± 10%).

> Since the lower end of the range is exactly 50%, we cannot conclusively say the majority of the population prefers a four-day workweek. The survey is inconclusive.

**This means that your analysis might not give an actionable result. And let's say you feel that the margin of error to large you can decrease it by adding observations to your current dataset.**

**3.1. Calculate your Margin of Error:**

Google provided a calculator for us:

https://docs.google.com/spreadsheets/d/1gdhfyA3_vMnQ1cDaGSCshXd5ezLtVPfLhxc9STGq6B8/template/preview

---
### 4. Deal with Insufficient Data

What to do if you have insuffienct data?

**Types of Insufficient data:**
- Data from only one source (limited), other source might give other trends
- Keeps updating (it means it is not yet finished)
- Outdated data
- Geographiaclly limited

The following notes will answer how you'll solve it.

#### When starting to analyze you might encounter the following issues (insufficient data)
The possible solution is stated but first, one must know **proxy data** that is a data substitute

Proxy Data:
>If you are analyzing peak travel times for commuters but don’t have the data for a particular city, use the data from another city with a similar size and demographic. 

**4.1. How to Use Proxy Data?**

Here are some more examples of how you use proxy data:
<div style="display: flex; justify-content: space-between;">

<div style="width: 45%; padding: 10px; border: 1px solid #ccc;">

### Business Scenario
- A new car model was just launched a few days ago, and the auto dealership can’t wait until the end of the month for sales data to come in. They want sales projections now.
- A brand new plant-based meat product was only recently stocked in grocery stores, and the supplier needs to estimate the demand over the next four years.
- The Chamber of Commerce wants to know how a tourism campaign is going to impact travel to their city, but the results from the campaign aren’t publicly available yet.

</div>

<div style="width: 45%; padding: 10px; border: 1px solid #ccc;">

### How Proxy Data Can Be Used
- The analyst proxies the number of clicks to the car specifications on the dealership’s website as an estimate of potential sales at the dealership.
- The analyst proxies the sales data for a turkey substitute made out of tofu that has been on the market for several years.
- The analyst proxies the historical data for airline bookings to the city one to three months after a similar campaign was run six months earlier.

</div>

</div>

#### Data issue 1: No data
<div style="display: flex; justify-content: space-between;">

<div style="width: 45%; padding: 10px; border: 1px solid #ccc;">

### Possible Solutions
- Gather the data on a small scale to perform a preliminary analysis and then request additional time to complete the analysis after you have collected more data.
- If there isn’t time to collect data, perform the analysis using proxy data from other datasets.  
  *This is the most common workaround.*

</div>

<div style="width: 45%; padding: 10px; border: 1px solid #ccc;">

### Examples of Solutions in Real Life
- If you are surveying employees about what they think about a new performance and bonus plan, use a sample for a preliminary analysis. Then, ask for another 3 weeks to collect the data from all employees.
- If you are analyzing peak travel times for commuters but don’t have the data for a particular city, use the data from another city with a similar size and demographic.

</div>

</div>

#### Data issue 2: Too little data
<div style="display: flex; justify-content: space-between;">

<div style="width: 45%; padding: 10px; border: 1px solid #ccc;">

### Possible Solutions
- Do the analysis using proxy data along with actual data.
- Adjust your analysis to align with the data you already have.

</div>

<div style="width: 45%; padding: 10px; border: 1px solid #ccc;">

### Examples of Solutions in Real Life
- If you are analyzing trends for owners of golden retrievers, make your dataset larger by including the data from owners of labradors.
- If you are missing data for 18- to 24-year-olds, do the analysis but note the following limitation in your report: this conclusion applies to adults 25 years and older only.

</div>

</div>

#### Data Issue 3: Wrong data/including data with errors
* Important note: Sometimes data with errors can be a warning sign that the data isn’t reliable. Use your best judgment.

<div style="display: flex; justify-content: space-between;">

<div style="width: 45%; padding: 10px; border: 1px solid #ccc;">

### Possible Solutions
- If you have the wrong data because requirements were misunderstood, communicate the requirements again.
- Identify errors in the data and, if possible, correct them at the source by looking for a pattern in the errors.
- If you can’t correct data errors yourself, you can ignore the wrong data and go ahead with the analysis if your sample size is still large enough and ignoring the data won’t cause systematic bias.

</div>

<div style="width: 45%; padding: 10px; border: 1px solid #ccc;">

### Examples of Solutions in Real Life
- If you need the data for female voters and received the data for male voters, restate your needs.
- If your data is in a spreadsheet and there is a conditional statement or boolean causing calculations to be wrong, change the conditional statement instead of just fixing the calculated values.
- If your dataset was translated from a different language and some of the translations don’t make sense, ignore the data with bad translation and go ahead with the analysis of the other data.
 

</div>

</div>

<br>

**Sometimes this happens when cleaning your data:**

>Losing track of business objectives: When you are cleaning data, you might make new and interesting discoveries about your dataset-- but you don’t want those discoveries to distract you from the task at hand. For example, if you were working with weather data to find the average number of rainy days in your city, you might notice some interesting patterns about snowfall, too. That is really interesting, but it isn’t related to the question you are trying to answer right now. Being curious is great! But try not to let it distract you from the task at hand.

**The question here arises:** How much proxy do you need? Should you just drop observations from you original dataset and not use proxy data? This is where the knowledge of sampling becomes important.

---
### 5. Balance Business Bbjectives with Data Integrity

**The main insight here is** that even if you're processing your data you still want to make sure that it can solve your business problem. (Aligned to your business problem.)

- **Good alignment** means that the data is relevant and can help you solve a business problem or determine a course of action to achieve a given business objective.
  
- Sometimes your data may have integrity **but** cannot answer your business problem. That's why there maybe times when **you can change your objectives because of your data**. If for instance your data has a duplicate in just one column and you realize that it is not a mistake then maybe you can just adjust your business objectives.

**Lesson,** even if you are doing something to your data (limiting it in a way), make sure to balance what you do to the business objectives.

**Concluion:**
- When there is clean data and good alignment, you can get accurate insights and make conclusions the data supports.
- If there is a good alignment but the data needs to be cleaned, clean the data before you perform analysis.
- If the data partially aligns with an objective, think about how you could modify the objective or use data constraints to make sure that the subset of data better aligns with the objective

## Processing
This is where you clean the data

### 1. Clean Data with the Right Tools

**What to do with NULLS?**: 
- You can rule them out and then communicate that you now have a smaller sample
- Fix it if you know how
- Continue and learn from the fact that the customer skipped it.

**Dirty data**: data that is incomplete, incorrect, or irrelevant to the problem you are trying to solve. And it includes the following and this is what you want to clean. 

The following resonates with the criteria for data integrity, the following could be the reasons why data loses its integrity and therefore must be fixed.

| **Dirty Data**         | **Description**                                                    | **Possible Cause**                                              |
|-------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------|
| **Duplicate**          | Any data record that shows up more than once                     | Manual data entry, batch data imports, or data migration        |
| **Outdated**           | Any data that is old and should be replaced with newer information| People changing roles or companies, or obsolete software/systems|
| **Incomplete**         | Any data missing important fields                                | Improper data collection or incorrect data entry               |
| **Incorrect/Inaccurate** | Any data that is complete but inaccurate                        | Human error, fake information, or mock data                    |
| **Inconsistent**       | Any data using different formats to represent the same thing     | Data stored incorrectly or errors during data transfer     


#### 1.1. Using Spreadsheet:
| **Tool/Function**         | **What it Does**                                                                                   | **Why Use It**                                                                                               | **Syntax/Steps**                                                                                                                                                  |
|----------------------------|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **COUNTIF Function**       | Returns the number of cells that match a specified condition.                                     | Useful for identifying outliers, such as unexpected values or errors.                                        | `=COUNTIF(range, condition)`<br>Example: `=COUNTIF(I2:I72, "<100")` counts values less than 100 in a range.                                                      |
| **LEN Function**           | Counts the number of characters in a text string.                                                 | Helps verify if text values meet a specific length, such as ID codes.                                        | `=LEN(cell)`<br>Example: `=LEN(A2)` returns the length of text in cell A2.                                                                                       |
| **LEFT Function**          | Extracts a specified number of characters from the beginning (left) of a text string.             | Useful for analyzing or isolating data from the start of a text string.                                      | `=LEFT(range, num_characters)`                                                                                                                                   |
| **RIGHT Function**         | Extracts a specified number of characters from the end (right) of a text string.                  | Useful for analyzing or isolating data from the end of a text string.                                        | `=RIGHT(range, num_characters)`                                                                                                                                  |
| **MID Function**           | Extracts a segment from the middle of a text string.                                              | Helps isolate specific substrings when they are not at the start or end of a string.                         | `=MID(range, start_position, num_characters)`                                                                                                                    |
| **CONCATENATE Function**   | Joins two or more text strings into one.                                                          | Useful for rejoining separated data into a single string.                                                    | `=CONCATENATE(text1, text2, ...)`                                                                                                                                |
| **TRIM Function**          | Removes leading, trailing, and repeated spaces in text.                                           | Helps clean up text data for easier analysis and searching.                                                  | `=TRIM(range)`                                                                                                                                                   |
| **Conditional Formatting** | Changes cell appearance based on conditions. Highlights cells meeting or not meeting set criteria.| Useful for visual cues in large datasets, like identifying missing data.                                     | 1. Select range → 2. Go to **Format → Conditional Formatting** → 3. Choose "Format cells if empty" → 4. Select style (e.g., pink) → 5. Click "Done".              |
| **Remove Duplicates**      | Automatically detects and removes duplicate entries.                                              | Ensures data is unique and avoids redundancy in analysis.                                                    | 1. Copy dataset → 2. Go to **Data → Remove Duplicates** → 3. Select **Data has header row** → 4. Choose "All" → 5. Click "Remove Duplicates".                     |
| **Consistent Formatting**  | Standardizes the format of dates or other data types.                                             | Makes data uniform, avoiding confusion and enabling proper analysis.                                         | 1. Select column → 2. Go to **Format → Number → Date**                                                                                                            |
| **Split Text to Columns**  | Divides a text string into separate cells based on a specified delimiter.                         | Useful for separating concatenated data like names, locations, or certifications into individual columns.    | 1. Highlight column → 2. Go to **Data → Split text to columns** → 3. Specify delimiter if not automatically detected.                                             |


#### More techniques:
- **Sorting** helps to organize data and spot duplicates, making the data easier to work with.
- **Filtering** allows you to zero in on specific values, improving efficiency during the cleaning process.
- **Pivot Tables** allow you to summarize and organize data for quick insights, focusing on key areas.
- **VLOOKUP** is essential when working with multiple datasets, enabling you to find corresponding data in different sheets.
- **Plotting** is a quick way to visualize data distributions and identify anomalies, such as outliers or incorrect values.


| **Function/Feature** | **What it does**                                             | **Why use it**                                                                 |
|-----------------------|------------------------------------------------------------|--------------------------------------------------------------------------------|
| **Sorting**           | Arranges data in a meaningful order (e.g., alphabetical, numerical). | Makes data easier to analyze and visualize; helps quickly identify duplicates. |
| **Filtering**         | Displays only data that meets specific criteria while hiding the rest. | Speeds up data cleaning by focusing on relevant information.                   |
| **Pivot Tables**      | Summarizes data by sorting, reorganizing, grouping, counting, totaling, or averaging. | Provides a clutter-free, focused view of specific aspects of your dataset.     |
| **VLOOKUP**           | Searches for a value in one column and returns information from another column. | Useful for looking up data across multiple sheets or databases.                |
| **Plotting**          | Visualizes data in the form of charts or graphs.          | Helps identify outliers or errors and aids in visual analysis of trends.  orrect values.


#### 1.2. Using SQL

#### 1.2.1. Clean String Variables:

| **Function/Feature** | **What it does**                                                                                       | **Why use it**                                                                                               | **Syntax if Applicable**                                                                         |
|-----------------------|------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| **DISTINCT**          | Removes duplicate rows from the query result.                                                       | Ensures unique values are returned, avoiding redundancy in the data.                                         | `SELECT DISTINCT column_name FROM table_name;`                                                  |
| **LENGTH (or LEN)**   | Checks the number of characters in a string.                                                        | Verifies data consistency, such as ensuring all country codes are the correct length.                        | `SELECT LENGTH(column_name) FROM table_name;`                                                   |
| **SUBSTRING**         | Extracts a specific portion of a string, starting from a defined position for a defined length.      | Standardizes text values, such as extracting consistent portions of string variables.                        | `SELECT SUBSTRING(column_name, start, length) FROM table_name;`                                 |
| **TRIM**              | Removes leading, trailing, or both types of spaces from a string.                                   | Ensures no unintended spaces exist, avoiding data mismatches and inconsistencies.                            | `SELECT TRIM(column_name) FROM table_name;`                                                     |
| **CONCAT**            | Combines two or more strings into a single string.                                                 | Creates unique identifiers by combining text columns or formats text for easier analysis.                    | `SELECT CONCAT(column1, column2) FROM table_name;`                                              |


1. **DISTINCT** can be added to the `SELECT` statement to filter out duplicates.  
   For example, `SELECT DISTINCT customer_id FROM customer_data.customer_address` ensures unique customer IDs in the result set.

2. **LENGTH** is useful for identifying inconsistencies in text length, such as country codes or state abbreviations.  
   A condition like `WHERE LENGTH(country) > 2` highlights irregularities.

3. **SUBSTRING** is powerful for handling text anomalies.  
   For example, `SUBSTRING(country, 1, 2) = 'US'` extracts the first two characters from the `country` column to standardize entries.  
   *(Assuming that some countries in the `country` column have "USA")*.

4. **TRIM** cleans data by removing extra spaces, such as resolving entries like "OH " (with a trailing space) to "OH."  
   A query like `WHERE TRIM(state) = 'OH'` accounts for such errors.

5. **CONCAT** allows you to combine two or more strings into a single value, which can create unique keys or formatted outputs.  
   For example, `SELECT CONCAT(product_code, product_color) AS unique_key FROM customer_purchase` creates a unique key combining product codes and colors to differentiate items.

#### 1.2.2. Fixing the Format:
| **Functions/Queries**              | **What it Does**                                                      | **Why Use It**                                                                | **Syntax if Applicable**                                                                                      |
|------------------------------------|----------------------------------------------------------------------|------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| `CAST`                            | Converts data from one data type to another.                          | Used for fixing improperly formatted data types, such as turning strings into numbers or dates. | `CAST(expression AS data_type);`                                                                               |



Use the CAST function to convert data to the appropriate data type when the imported data is not formatted correctly. This is essential when sorting or performing calculations, especially if the database misinterprets numeric values as text (e.g., sorting prices in descending order).

#### 1.2.3. Updating and Inserting:

| **Functions/Queries**              | **What it Does**                                                      | **Why Use It**                                                                | **Syntax if Applicable**                                                                                      |
|------------------------------------|----------------------------------------------------------------------|------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| `INSERT INTO`                      | Inserts new rows of data into a table.                               | Adds new records to a database table.                                        | `INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);`                               |
| `UPDATE ... SET ... WHERE`         | Updates specific rows of data in a table.                            | Corrects or modifies data anomalies such as errors or outdated information.   | `UPDATE table_name SET column_name = new_value WHERE condition;`                                             |
| `CREATE TABLE IF NOT EXISTS`       | Creates a new table only if it does not already exist.                | Avoids duplication of tables while adding new structures to the database.    | `CREATE TABLE IF NOT EXISTS table_name (column1 datatype, column2 datatype, ...);`                           |
| `DROP TABLE IF EXISTS`             | Deletes a table if it exists.                                        | Cleans up unused or redundant tables to maintain a tidy database.            | `DROP TABLE IF EXISTS table_name;`                                                                           |
- Use `UPDATE ... SET ... WHERE` to fix data anomalies like incorrect addresses, values, or errors found in the table.
- Use `INSERT INTO` to add missing or new records after validating the data.
- Use `DROP TABLE IF EXISTS` to clean up tables created for temporary testing or redundant data.
- Combine `CREATE TABLE IF NOT EXISTS` with other queries to ensure smooth data management without errors caused by duplicate tables.

#### 1.2.4. Handle Nulls:

| **Function/Feature** | **What it does**                                                                                   | **Why use it**                                                                                               | **Syntax if Applicable**                                                    |
|-----------------------|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| **COALESCE**          | Returns the first non-NULL value from a list of columns or expressions.                          | Replaces missing values (NULL) with alternative data to ensure completeness and readability.                 | `SELECT COALESCE(column1, column2, 'default_value') AS alias_name FROM table_name;` |

- **COALESCE** is used to replace NULL values with the first non-NULL value in a specified list.  
   For example, `SELECT COALESCE(product_name, product_code) AS product_info FROM customer_purchase` ensures that if `product_name` is NULL, the `product_code` will be displayed instead.

- **COALESCE** is especially useful when handling optional fields that might not always have values.  
   For instance, when analyzing sales data, displaying a fallback value prevents gaps in reports.

- You can provide a default fallback value as well.  
   For example, `SELECT COALESCE(customer_name, 'Unknown') AS customer_info FROM sales_data` replaces NULL `customer_name` entries with the word "Unknown."

- **COALESCE** is efficient in calculations because it skips NULL values, ensuring operations like addition, concatenation, or formatting are not disrupted.  
   For example:  
   ```sql
   SELECT order_id, price + COALESCE(discount, 0) AS final_price 
   FROM orders;

---
### 2. Report and Verify Cleaning Results
- Reporting and verifying your cleaning process is essential so others can keep track or see the steps you took and therefore verify it.
- Reporting reports can simply be done with the version history of your spreadsheet or your RDBMS
- You can also do a document for the documentation

To verify your data after the process, you can go the following steps:

1. Compare your cleaned data to the raw data
    - Check the problems of your raw data and then check if you have solved it.
    - You can use tools such as pivot table
    - or the `CASE` from SQL to make sure that you succesfully cleaned the data

Ex (using the pivot table):

    You notice that your raw data has duplicates so you can verify your cleaned data to know if you have solved it using pivot table:

| Name    | Count |
|---------|-------|
| Alice   | 1     |
| Bob     | 1     |
| Charlie | 1     |
| Diana   | 1     |
| Emma    | 2     |


Ex (using `CASE`):

    You notice that your raw data contains mispellings and you wanna make sure so you use the CASE:

| nameID | name   |
|--------|--------|
| 1      | TNOY   |
| 2      | Alice  |
| 3      | Bob    |

```SQL
SELECT nameID, 
       CASE WHEN name = 'TNOY' THEN 'Tony' 
        ELSE name END AS name
FROM my_table;
```

Result:

| nameID | name   |
|--------|--------|
| 1      | Tony   |
| 2      | Alice  |
| 3      | Bob    |

You should know that you are not limited to these tools.

2. Reflect if the cleaned data is still aligned to the business problem you want to solve (Remember your scope. Maybe you're cleaning something not important because it does not align.)
    - Consider your goal
    - Make sure your data can solve it

# Additional Readings

## Data cleaning with the merger:

### Merging
Merging of data is when you have two datasets and you want to join them **BUT** this is not easy because you cant be sure that these two datasets are compatible thus you have to make them compatible first by cleaning them.

**For instance** if the first dataset uses two columns for names and last names and the other dataset just one then make them the same first before merging.

To guide yourself in the merging ask yourself:
1. Do I have all the data I need (age, gender)
2. Do these datasets have the data I need?
3. Do these datasets need to be cleaned or are they ready to use?
4. Are these datasets compatible (can be joined)

### Data mapping (Don't worry about this much, we have tools for this)
Data mapping is the process of matching fields from one database to another. It ensures compatibility between different data systems by identifying and aligning fields that might be represented differently in each system (e.g., state names written as "Maryland" vs. "MD"). Proper data mapping helps in tasks such as data migration, data integration, and general data management.

Data Mapping Steps:

1. Identify Data to Move: Determine which tables and fields need to be transferred and define the desired format for the destination.
2. Mapping Fields: Map data field by field between sources, ensuring consistency.
3. Schema Understanding:
    >Primary Key: Ensures uniqueness of data.
    
    >Foreign Key: Refers to keys in related tables.
5. Data Transformation: Use functions like concatenate to transform and combine data fields into a consistent format.

---
### Automating tasks
Not a step but as an analyst it is helpful to know how to automate your tasks:

Some resources:
Towards Data Science's Automating Scientific Data Analysis:

https://towardsdatascience.com/automating-scientific-data-analysis-part-1-c9979cd0817e

MIT News' Automating Big-Data Analysis:

https://news.mit.edu/2016/automating-big-data-analysis-1021

Technology Advices' 10 of the Best Options for Workflow Automation:

https://technologyadvice.com/blog/project-management/best-workflow-automation-software/

---
### Advanced Functions:
| Function     | Syntax (Google Sheets)                              | Menu Options (Microsoft Excel)                      | Primary Use                                                                 |
|--------------|-----------------------------------------------------|----------------------------------------------------|-----------------------------------------------------------------------------|
| IMPORTRANGE  | =IMPORTRANGE(spreadsheet_url, range_string)         | Paste Link (copy the data first)                   | Imports (pastes) data from one sheet to another and keeps it automatically updated. |
| QUERY        | =QUERY(Sheet and Range, "Select *")                 | Data > From Other Sources > From Microsoft Query   | Enables pseudo SQL (SQL-like) statements or a wizard to import the data.    |
| FILTER       | =FILTER(range, condition1, [condition2, ...])       | Filter (conditions per column)                     | Displays only the data that meets the specified conditions.                 |

END