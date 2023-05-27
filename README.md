Trends in Indian Start-up Fund
## Introduction
Now a day's data analysis becomes highly impacting in every area who are actually running its business with a high flow of data, in this article, I provide some of my investigation into and analysis of funding for Indian start-ups for four years from 2018 to 2021.
India has emerged as one of the fastest-growing startup ecosystems in the world, attracting significant investment in various sectors. The India startup funding dataset typically contains information on startup names, industry sectors, funding rounds, funding amounts, investor names, and funding dates.
The goal was to use the data to explore the ecosystem, uncover insights, and recommend the best course of action to my fictional team attempting to enter the Indian start-up ecosystem.
I used the six stages of data analysis (as learnt from Google's Data Analytics program): Ask, Prepare, Process, Analyze, Share, and Act
1.1 The Data
The data for each year of funding was in a separate CSV file, meaning they had to be put together at a point. The shared columns/attributes in the files were as follows (column name: description):
· Company/Brand: name of the company/start-up
· Founded: the year the start-up was founded
· Sector: sector of operation
· About Company/What it does: description of the company
· Founders: founders of the company
· Investor: investors in the deal
· Amount($): raised funds
· Stage: round of funding
· Headquarters: headquarters of the company
Determine business objective.
The funding given to Indian start-up is to give them entrepreneurial ventures to the capital which will help them think big and be innovative. These start-ups will then grow to the point they will create employment for the youth of India. These start-ups will grow into big companies making huge profits and, in the end, make India rich. These companies now becomes house-hold names in India leaving impact on all.
Objectives of investors is to:
1. Assess situation
2. Determine data mining goals
3. Produce project plan
2. Ask Stage
At this stage, we bring the objective into view and put down the questions that we intend to answer at the end of the analysis process.
Here, with the overarching goal of making a recommendation to the team to assist their goal of entering the Indian ecosystem, the following hypothesis was stated and questions were asked to guide the analyses.
2.1 Hypothesis
Null- Funding to start-ups in India has not changed over time.
Alternate- Funding to start-ups has changed over time
2.2 Questions
For the hypothesis, the following questions were put forward to be answered:
1. How has funding to startups changed over the period?
2. How does location affect funding to startups?
3. Which sectors are most favored by investors?
4. What is the average amount of funding for start-ups in: the sector with the most funding, and the location with the most funding?
5. How does the breakdown by stages of funding look?
6. Which start-ups were most favored by investors?
3. Data Preparation and Processing
At this stage, we organize the data to make it fit for analysis. Cleanliness and consistency of data are the objectives here.
3.1 Loading packages
To start with, the basic packages for the analysis were loaded. These were:
· Pandas: for data cleaning and manipulation
· Numpy: for data cleaning and manipulation
· Matplotlib: for visualisations
· Seaborn: for visualisations
· Re: for regular expressions
· Warnings: to deal with the warnings
3.2 Froom Previewed the DataFrames
The individual datasets were then loaded as Pandas DataFrames. The first note was the differences in the number of columns in the datasets: 2018 (6), 2019 (9), 2020 (10), and 2021 (9). Other observations from looking at the individual datasets are as follows
3.2.1 The 2018 DataFrame
· The DataFrame has 526 rows and 6 columns.
· Dashes were used in the amounts column for deals whose values were not known.
· The amounts in the 2018 DataFrame are a mix of Indian Rupees (INR) and US Dollars (USD), meaning they have to be converted into the same currency.
· The industry and location columns have multiple information. A decision is to be made between selecting the first value before the separator(,) as the main value or representing that column with a word cloud.
3.2.2 The 2019 DataFrame
· The DataFrame has 89 rows and 9 columns.
· The data type of the "Founded" column is set to float64. It should be set to a string for uniformity.
· The headquarter column has multiple information. A decision is to be made between selecting the first value before the separator(,) as the main value or representing that column with a word cloud.
3.2.3 The 2020 DataFrame
· There is an extra column called "Unnamed:9", giving it a total of 10 columns. It should be dropped to ensure complete alignment with the other DataFrames for ease of concatenation.
3.2.4 The 2021 DataFrame
· The data type of the "Founded" column is set to float64. It should be set to a string for uniformity.
3.2.5 General Notes
· The columns in 2018 are different from those of 2019–2021, meaning they have to be renamed before concatenation.
· The currency signs and commas have to be removed from each amount column for each DataFrame.
· All the columns with amounts have to be set to float.
· All the years of funding and the years founded should be converted to strings.
· The respective years of funding have to be attached to each DataFrame before combining.
3.3 Assumptions
1. The average Indian Rupee (INR) to US Dollar (USD) rate for the relevant year will be used for currency conversions.
2. The first values of industry and location in the 2018 data are the primary sector and headquarters respectively.
3. Amounts without currency symbols in the 2018 dataset are in USD.
4. Imputations will not be made for undisclosed and/or unavailable (missing) amounts due to the uncertainties, risks of misstatements and possible misleading effects on the analyses.
3.4 Cleaning the Data
Given that this article is to present a summary, I will focus on the major activities performed on the DataFrames. The detailed functions will be found in the notebook, a link to which will be attached at the end of the article.
1. I applied string formatting to all columns except the amounts columns which were formatted as numerics.
2. I separated the values in the location and industry columns using a comma as the delimiter and selected the first value in the split column as the primary sector.
3. For the 2018 Amount column, I created two new columns to help with the currency conversion and then dropped them after standardising the amounts.
4. I removed all commas and currency signs from the "Amounts" columns.
5. I replaced the "Undisclosed" text in the "Amounts".
6. I replaced the "nan" values in the "Founders" column with nulls.
7. I replaced notable misplaced and/or erroneous values in the respective rows.
8. I dropped the extra unnamed in the 2020 DataFrame.
9. For each DataFrame, I appended a column indicating the year of funding
The columns in the 2018 DataFrame were renamed to match the other DataFrames, after which it was concatenated with the other DataFrames. I then brushed up with the following:
1. Reformatted all amounts as numerics and replaced nulls with zeros.
2. Formatted funding years and years founded as strings.
3. Dropped all duplicates and reset the index.
4. Did more column-specific cleaning (ref. notebook).
4. Answering the Questions
Here, I combine the "Analyze" and "Share" stages of the data analysis process through the code and visualizations.
4.1 How has funding to startups changed over the period?
Looking at the number of deals, funding to startups in the Indian ecosystem has been on an overall increasing trajectory despite a dip in 2019; moving from 525 deals in 2018 to 89 in 2019, then 1,054 in 2020, and 1190 in 2021.
The same trend was maintained when looking at the changes in terms of amounts involved, moving from USD 6.6bn in 2018 to USD 3.3bn in 2019, USD 90bn in 2020, and USD 179.6 bn in 2021.
It is therefore safe to conclude that both the number of deals and funding received by startups in the Indian ecosystem increased over the period.

4.2 How does location affect funding to startups?
In terms of total number of deals for startups headquartered in the various locations, Bangalore (916), Mumbai (471), Gurgaon (317), and New Delhi (230) made up the top 5. A visual representation can be seen below:
By amount of funding received by startups headquartered in the locations, Mumbai came first (USD 230.8bn), followed by Bangalore (USD 24bn), Gurgaon (USD 6.9bn), and New Delhi (USD 3.4bn) in that order. A visual representation of the gap between funding to startups headquartered in the top 10 locations is shown below:
