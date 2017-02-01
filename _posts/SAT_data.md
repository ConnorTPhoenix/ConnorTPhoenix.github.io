#United States SAT Scores (2001)
##Introduction
In this first project for General Assembly's Data Science Immersive program we were tasked with investigating the average SAT scores by US State from 2001 for our client CollegeBoard.com. The goal was to read in a .csv file and explore the dataset using descriptive statistics and data visualizations.

##The Data
The dataset is taken from CollegeBoard.com and provides the average SAT score by state for both the Math and Verbal sections. Also provided are the student participation rates for for each state. View dataset: [sat_scores.csv](https://git.generalassemb.ly/ConnorTPhoenix/project-1-sat-scores/blob/master/assets/sat_scores.csv)

Fig 1. (Summary of Data)

![img](https://cloud.githubusercontent.com/assets/23442782/22491800/ea3b2078-e7f3-11e6-85f7-80cae1a337d4.png)

    enter code here

##Data Cleaning
The csv file provided by CollegeBoard.com was well structured and did not contain any missing or "NaN" values.

I imported the csv module and read the 'sat_data.csv' into a list of lists using the csv.reader() method. After printing the resulting list I noted that the data within each column was of "str" type. I reassigned the data type of the 3 numeric columns (Rate, Math, & Verbal) using the below 'for loop':

    for row in SAT_data:
    row[1] = int(row[1])
    row[2] = int(row[2])
    row[3] = int(row[3])  


##Assumptions  

Two assumptions were made related to the "State" column. The first was to include the row State="DC" in the dataset. Although Washington "DC" is technically not a state, its residents contribute to the total US population and are therefore relevant to the analysis. The row where State = "All" was removed from the dataset. Given that the "All" column is comprised of summary statistics of the rest of the dataset it made sense to exclude it from the analysis. I removed this row as well as the column names using list splicing:

    SAT_data = SAT_file[1:52]

##Computing Summary Statistics

In order to gain a better sense of the data I computed the min, max, and standard deviation of each numeric column.  

min and max were calculated using list comprehension as follows:

    max_verbal = max([row[2]for row in SAT_data])

max_rate: 82
min_rate: 4
max_verbal: 593
min_verbal: 482
max_math: 603
min_math: 439

From these values, it would appear the there is a large degree of variability in State SAT participation rates. These values also suggest that there is more variability in Math scores compared to Verbal.

Taking it a step further, I then calculated the standard deviation (std) for each numeric column. I first created a function to calculated std() using numpy as follows:

    def std_dev(row_index):
	    return np.std([row[row_index] for row in SAT_data])

Passing in the row indices of the numeric columns as arguments yield the following results:

Rate Standard Deviation: 27.0379964945
Verbal Standard Deviation: 32.9150949616
Math Standard Deviation: 35.6669961643

These results support our hunch that there was more variability in the Math scores compared to Verbal.

##Data Visualization

###ScatterPlots

To get a better since of how each column in sat_scores.csv relate to each other I plotted a three scatterplots (Participation Rate v. Verbal Score, Participation Rate v. Math Score,  and Math v. Verbal Score).

![img](https://github.com/ConnorTPhoenix/ConnorTPhoenix.github.io/blob/master/_posts/assets/SAT_Scatter.png)

SAT Score v. Participation Rate

	There appears to be a negative correlation between Participation Rate and Verbal Score.

    Similarly, we observe a negative correlation between Participation Rate and Math Score.

	However there was one significant outlier to this trend within the Math distribution. OH: [26, 534, 439], where the participation was low (26%) and the Math Score was very low (439).

    One possible explanation for this phenomenon is that in states with lower participation only higher achieving students are expected to take the exam.

Math Score v. Verbal Score


	There appears to be a strong positive correlation between Math and Verbal SAT scores.

    This observation feels intuitively accurrate. It seems likely that a student's achievement across subjects would be strongly correlated.

###Heatmap

![img](https://github.com/ConnorTPhoenix/ConnorTPhoenix.github.io/blob/master/_posts/assets/SAT_Math_Heatmap.png)

![img](https://github.com/ConnorTPhoenix/ConnorTPhoenix.github.io/blob/master/_posts/assets/SAT_Particpation_Heatmap.png)

![img](https://github.com/ConnorTPhoenix/ConnorTPhoenix.github.io/blob/master/_posts/assets/SAT_Verbal_Heatmap.png)
