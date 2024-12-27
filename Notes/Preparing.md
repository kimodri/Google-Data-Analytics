# Data Analysis: Preparing
Kim Audrey Magan | 09/12/2024
# Table of Contents

1. [Objective](#objective)  
2. [Steps](#steps)  
3. [Recall](#recall)  
4. [Steps in Depth](#steps-in-depth)  
    - [Planning your Data](#planning-your-data)  
        - [1. Decide on the data you need](#1-decide-on-the-data-you-need)  
        - [2. Decide on the formats of your data](#2-decide-on-the-formats-of-your-data)  
        - [3. Wide or Long Data](#3-wide-or-long-data)  
    - [Understanding your Data](#understanding-your-data)  
        - [1. Being wary on biases](#1-being-wary-on-biases)  
        - [2. Is my data good?](#2-is-my-data-good)  
        - [3. Create a metadata](#3-create-a-metadata)  
5. [Additional Readings](#additional-readings)  


# Objective
Finishing this course, one must be able to:
- Identify and explore different types of data and data structures that fits your analysis
- Then, you’ll learn to identify any bias in data and to verify its credibility

Basically, this course will teach you how to identify the correct data (data types for your analysis).
# Steps
1. Structuring/Planning your data:
    1. Decide on the data you need (is it age, gender, family number, number of cars?)
    2. Decide on their formats
    3. Decide on the format of your structured data (long or wide?)
2. Understanding your data:
    1. Catch biases
    2. Is my data good?
    3. Create metadata
# Recall
Google course on data analytics:
There are **6 phases** for data analysis and this 6 phases are the coverage for this program and these are

| **Step**         | **Description**                                                                                                                                                 |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ~~**Asking**~~       | ~~Communicate with stakeholders about the problem to be solved. Ask relevant questions to narrow the focus of analysis. <br><br>~~~~**Example**: What are the possible data? What is the root problem/cause?~~ |
| **Preparation**  | Gather the data to analyze. It could be through surveys or past company data.                                                                                   |
| **Process**      | Manipulate the gathered data, such as removing outliers or filling nulls.                                                                                       |
| **Analyzing**    | Analyze the cleaned data to find patterns, if any.                                                                                                              |
| **Sharing**      | Share the findings using visualizations.                                                                                                                        |
| **Act**          | Recommend proper steps for the company to solve the problem based on the analysis.                                                                              |
# Steps in Depth
## Planning your Data
### 1. Decide on the data you need

How will you decide what data to collect (this also means what are the types or the structure)?

You can think of these considerations to achieve your analysis goals.
| **Guidelines**                     | **Description**                                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Purpose of the Data**       | Identify the purpose of the data needed. The data must be relevant and approved for use. For instance, analyzing rush hour traffic requires traffic volume data, not financial data. Selecting appropriate data keeps the analysis focused on solving the problem.                                                                             |
| **Data Types**                | Determine the type of data required. For example, dates in traffic records help identify high-traffic days, revealing patterns like congestion-prone days of the week. Choosing the right data type makes the analysis more effective.                                                                                                        |
| **Volume**                    | Decide between collecting population data or sample data: <br> - *Population Data*: Includes all possible data values (e.g., all cars in a city), but collecting it can be challenging. <br> - *Sample Data*: A representative portion of the population (e.g., traffic at one intersection). Choose based on project scope.                                                |
| **Data Sources**              | Identify where to collect data: <br> - *First-party Data*: Data collected directly, offering high reliability (e.g., observing and counting cars). <br> - *Second-party Data*: Purchased from a trusted source (e.g., traffic analysis firms). <br> - *Third-party Data*: Collected indirectly; must be checked for accuracy, bias, and credibility.                        |
| **Time Frame for Data Collection** | Define the timeframe for data collection. <br> - For quick answers, use historical data that already exists. <br> - For tracking long-term patterns, collect new data over time (e.g., monitoring traffic trends over several months).                                                                                                      |

**Kim,** you might be wondering why this is important. Well, there are times when analysis-ready data isn’t readily available. Often, you’ll need to retrieve data from a database (e.g., using SQL). In such cases, these guidelines can help you choose the right data from the database effectively.

### 2. Decide on the formats of your data

- This is important because once you know what format of data you have, you'd know what to do with them. 
- If it's discrete then you can apply discrete math to it like probability, or one hot encoding for ML.

There are different data formats and each format requires different handling:

| **Category**           | **Description**                                                                                                                                                                |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nominal Data**        | Categorical data without a set order, such as responses to whether someone watched a movie: "Yes," "No," or "Not Sure."                                                     |
| **Ordinal Data**        | Ordered data, like ranking a movie from 1 to 5 based on preference.                                                                                                         |
| **Internal Data**       | Data collected within an organization, often more reliable. For example, a movie studio tracking its own productions uses internal data.                                     |
| **External Data**       | Data gathered from outside the organization. For instance, a studio analyzing industry trends might use external data.                                                      |
| **Structured Data**     | Data organized into rows and columns, such as a spreadsheet or database table. It’s easy to search and analyze, making it a common format for analysts.                     |
| **Unstructured Data**   | Data without a defined format, like video or audio files. While harder to analyze, it can provide unique insights.                                                         |

### 3. Wide or Long Data?

Structured data is still divided into two and each of these require different strategies when handling.

| **Format**        | **Description**                                                                                                                                                                                                                     | **Example**                                                                                                                                                                         |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Wide Format**    | Each data subject has a single row with multiple columns representing different attributes or variables.                                                                                                                          | **Data about students**: <br> - Row: A single student <br> - Columns: Test scores in Math, Science, and English (e.g., Math_Score, Science_Score, English_Score).                   |
| **Long Format**    | Each row represents a single observation for a subject, allowing the same subject to have multiple rows. It is better for organizing data with multiple variables observed over time or at different conditions.                     | **Data about students**: <br> - Multiple rows per student <br> - Columns: Student_ID, Subject (Math, Science, English), and Score. <br> (Allows for easier addition of subjects). |
| **Key Difference** | Wide format uses more columns to represent variables; adding new variables increases the number of columns. Long format uses fewer columns, making it more scalable and easier to analyze with statistical tools.                  | If you add a new variable (e.g., "Attendance"), **wide format** needs one new column per category (e.g., Math_Attendance, Science_Attendance), but **long format** needs only one. |

<table>
  <tr>
    <td>
      <strong>Wide Format Example:</strong>
      <table>
        <tr>
          <th>Student_ID</th>
          <th>Math_Score</th>
          <th>Science_Score</th>
          <th>English_Score</th>
        </tr>
        <tr>
          <td>101</td>
          <td>85</td>
          <td>90</td>
          <td>78</td>
        </tr>
        <tr>
          <td>102</td>
          <td>88</td>
          <td>92</td>
          <td>80</td>
        </tr>
      </table>
    </td>
    <td>
      <strong>Long Format Example:</strong>
      <table>
        <tr>
          <th>Student_ID</th>
          <th>Subject</th>
          <th>Score</th>
        </tr>
        <tr>
          <td>101</td>
          <td>Math</td>
          <td>85</td>
        </tr>
        <tr>
          <td>101</td>
          <td>Science</td>
          <td>90</td>
        </tr>
        <tr>
          <td>101</td>
          <td>English</td>
          <td>78</td>
        </tr>
        <tr>
          <td>102</td>
          <td>Math</td>
          <td>88</td>
        </tr>
        <tr>
          <td>102</td>
          <td>Science</td>
          <td>92</td>
        </tr>
        <tr>
          <td>102</td>
          <td>English</td>
          <td>80</td>
        </tr>
      </table>
    </td>
  </tr>
</table>

**Which One to Use?**
<div style="display: flex; justify-content: space-between;">

<div style="width: 45%; padding: 10px; border: 1px solid #ccc;">

**Wide Data**
- Preferred when:
  - Creating tables and charts with a few variables about each subject.
  - Comparing straightforward line graphs.

</div>

<div style="width: 45%; padding: 10px; border: 1px solid #ccc;">

**Long Data**
- Preferred when:
  - Storing a lot of variables about each subject. For example, 60 years worth of interest rates for each bank.
  - Performing advanced statistical analysis or graphing.

</div>
</div>

## Understanding your Data
- Once you're with a transformed data from the above you must know its characteristics
### 1. Being wary on Biases
There are different types of bias and you may find this in the data you are working on or will collect:
1. Sampling bias
    - You may find this when groups are underrepresented and resolved by doing a random sampling
    - You can identify bias with features of data elements like their gender
    - You can visualize it with bar graphs
    - **How do you know if you have a bias? What should be the difference?** is there a formula?
3. Interpretation bias
4. Confirmation bias
5. Observation bias
### 2. Is my data good?
Aside from being wary of the biases you can just find good data. Good data satisfies _ROCCC_

- Reliable
- Original
- Comprehensive
- Current
- Cited
### 3. Create a metadata
Metdadata about your data provides context and ensures consistency. For example, if you are working on two files, one file's metadata may include the methods for collecting the data thus you can compare the two files and if they differ (based on their metadata then it is perhaps better to not combine them).
- To better make use of metadata you can create a repository of it.
- That is using a spreadsheet as a database for the information of your datasets because context is everything.

# Additional Readings

### Data modeling (Optional)
Data modeling is the process of creating diagrams that visually represent how data is organized and structured.  In your job as an analyst you may do this but not too much. Still it is helpful to learn this.

**Data-modeling techniques:** 
There are a lot of approaches when it comes to developing data models, but two common methods are the Entity Relationship Diagram (ERD) and the Unified Modeling Language (UML) diagram. ERDs are a visual way to understand the relationship between entities in the data model. UML diagrams are very detailed diagrams that describe the structure of a system by showing the system's entities, attributes, operations, and their relationships. As a junior data analyst, you will need to understand that there are different data modeling techniques, but in practice, you will probably be using your organization’s existing technique. 

Data modeling can help you explore the high-level details of your data and how it is related across the organization’s information systems. Data modeling sometimes requires data analysis to understand how the data is put together; that way, you know how to map the data. And finally, data models make it easier for everyone in your organization to understand and collaborate with you on your data. 

### Understanding Relationship in Databases

This is actually just optional, introductory lesson for the following SQL lessons:

Understand Relational Database 
- Primary key
    - Used to ensure that data in a table is unique
- Foreign key
    - Columns in rdbms that provides a link between the data in two tables
    - Refers to the field in a table that's a rpimary key in another table

**Normalization** is a process of organizing data in a relational database. For example, creating tables and establishing relationships between those tables. It is applied to eliminate data redundancy, increase data integrity, and reduce complexity in a database.

END