# Breath (Senior Project)

  In the modern era, several types of pollution exist around the globe, one of which is air pollution. The mixture of solid particles and gas in the air slowly deteriorates the city populations' health. There have been countless attempts to substantially reduce this particulate matter in the air, but to no avail. Therefore, to effectively aid in solving this air pollution crisis, our group will implement programming, data science, and machine learning to analyze the data pertaining to the atmospheric content and conditions over time. Insights, warnings, and a data platform are expected at the end of this project.

  Air pollution is the reason for many respiratory diseases. Ischemic heart disease, stroke, chronic obstructive pulmonary disease, and lung cancer are the most common non-communicable diseases linked to air pollution. Moreover, increased fine particulate matter (PM2.5) concentrations have been linked to an increased risk of respiratory diseases such as acute respiratory distress, asthma, chronic obstructive pulmonary disease, and lung cancer in various populations. This is the main reason that inspired us to make this project. We wish to gather insights, predictions, and make visualizations from the collected data in hopes of achieving cleaner air for human health.

## Objective of the project

  To integrate the concepts of cloud computing, data science, air pollution, and sustainability into a project. Using a cloud platform will benefit the data by means such as security, flexibility, mobility, loss prevention, disaster recovery, etc. 

  It will also be a good example to demonstrate the cloud engineering procedures for the upcoming Thailand server of cloud services providers. Data science will help us understand the available data better. 
The short period warning from deep learning methods will aid with the decision of the next course of action to deal with air pollution problems.

## Scope of the work

- This project will gather the dataset from online sources, for example, Thai Pollution Control Department, Thailand Open Data, Longdo Traffic, World Bank's Climate Change Data, etc.

- This project will develop a system using Google Cloud Platform (GCP) to store the raw data and perform the ETL method to transform the data and keep it in the data warehouse. Then we will use Google's API to link the Google Colab and the GCP together for further data science processes.

- This project will perform the aforementioned data science methodology to deeply study the correlation between our datasets.

- This project will develop a short period warning system that will predict the PM value in the next short period. This involves using deep learning techniques, we will compare the traditional ANN method with LSTM method to see which one performs better.

## GCP

- We stored the raw data XLSX files in Google Cloud Storage.
- We tried to transform the raw data to table form in Google BigQuery, but it does not support XLSX files.
- So, we transform XLSX to CSV.
- Again, we stored the raw data (now CSV) in Google Cloud Storage.
- Then, transform the CSVs to table form in Google BigQuery.
- Each CSV file will be dedicated one table.

## GCP to Colab

- We authenticated the admin user (E-mail) in Colab first.
- Specify the project ID and tables, then Get (method) the table.
- Transform each tables into DataFrame.
- Remove the _ in front of the column name.

## BigQuery to Colab data corruption fix

- The first 2, 3 rows are appended with random data, we dropped them out.
- Re-sort the rows by using Date column as reference.
- Use reset_index function to reset the column to Date.
- Drop the newly generated 'index' column as we don't need it.

## PM 2.5 and PM 10 data cleaning

- We dropped the column that every rows are NaN. Dropped the first half of PM 2.5's 2011 data (and reset index), and latter half of PM 2.5's 2022 data (they are empty rows). 
- Change the datatype of columns, [Date] to datetime, [Stations] to numeric using Pandas.
- Use linear interpolate on each columns to clean the NaN values.
- Some year data's first few rows are NaN, only interpolate() itself cannot deal with that. We use bfill (Backward fill) after interpolate().
- Average each column's value to find the year's average.
- Concatenate all the datetime and value column.

## LONGDO Traffic index data cleaning
0. Downsample from 5 mins to daily (to compare with daily PM value later)
1. Editing timestamp format.
2. Use Group by function and then Average values in same date.
3. Set datetime as index.
4. Use Reindex() method on the missing dates (add dates that have missing value with NaN).
5. Use Linear Interpolate method on the NaN (fillna) to fill out the NaN.
6. Use resetindex() to change datetime to column.

Power BI Link https://app.powerbi.com/view?r=eyJrIjoiN2EwOGY2YWQtZmNmYS00NDYyLTg2NzAtNzE4YzdkMmExNGY0IiwidCI6IjZmNDQzMmRjLTIwZDItNDQxZC1iMWRiLWFjMzM4MGJhNjMzZCIsImMiOjEwfQ%3D%3D
