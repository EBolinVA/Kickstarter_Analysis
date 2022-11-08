# Kickstarting with Excel

## Determining factors of successful Kickstarter campaigns

### Overview of Project
Louise, a US playwright, wants to start a crowdfunding campaign to fund her play ***Fever***. Her estimated budget is over $10,000. I'll be analysing several thousand crowdfunding projects to uncover trends which will help Louise determine both the ideal time to launch her campaign and a reasonable goal for funding her project. This analysis will evaluate the success of theater Kickstarter campaigns based on launch date and initial funding goals.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
Starting with a dataset of over 4000 Kickstarter campaigns in a variety of industries around the world from 2009-2017, I filtered the data to view only theater Kickstarter campaigns within these years. The result is an analysis of 1393 theater crowdfunding projects.

As we can see in the chart below, the good news is that overall there are more *successful* theater funding campaigns than *failed* campaigns each month. A closer look at the data indicates that success rates are highest in May and reach a low point in December, suggesting that people are less likely to pledge during the end of year holidays. 

![Image of Theater Outcomes Based on Launch Date](https://github.com/EBolinVA/kickstarter-analysis/blob/main/Theater_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals
Next I looked at the data for only *plays* within the theater Kickstarter projects. Of the 1393 theater kickstarter projects, 1066 are for funding plays. 

Since Louise has a proposed budget of $12,000 for her play, ***Fever***, let's look at the percentage of successful and failed projects by funding goal. 54% of campaigns with funding goals similar to Louise's are successful. 

![Image of Outcomes Based on Goals](https://github.com/EBolinVA/kickstarter-analysis/blob/main/Outcomes_vs_Goals.png)

At first glance, we see that success rates vary depending on the range of funding goals. The blue line shows percentage of successful play funding campaigns, and the highest percentage of successful campaigns have a funding goal of less than $1000. The least successful campaigns have a funding goal over $45000. However, Louise's funding goal is $12,000, and the data shows that campaigns with a funding goals range from $10,000 to $14,999 are 54% successful. The proportion of successful campaigns by funding goals does not change significantly between $5000 and $15000. What this means for Louise is that her campaign is not more likely to be successful if she adjusts her funding goals to an amount between $5000 and $15000. 

### Challenges and Difficulties Encountered
The first challenge for this project was in working with a very large dataset containing data for project categories that could not easily be filtered. As seen below, the original Kickstarter dataset contains only one column for category and subcategory information. 

![Image of original column with too much data](https://github.com/EBolinVA/kickstarter-analysis/blob/main/Category%20and%20Subcategory%20column.png)

In order to parse out the information for theater projects that are plays (and not musicals, or spaces), it was necessary to create two new columns which would contain data for the Parent category and the Subcategory separately. In order to do this, I used the Text to Columns button in the Data menu, which allowed me to separate the Parent category and Subcategory into two columns based on the delimiter value "/". 

![Image of selecting Text to Column tool](https://github.com/EBolinVA/kickstarter-analysis/blob/main/Create%20Subcategory.png)

Another obstacle in presenting the data was that the original dataset contained total pledged toward the project and number of donors, but not individual donations. In order to provide Louise with information about average pledges, I cleaned up some of the data. Dividing total pledge amount by number of donors resulted in some errors. This is because not every project was able to collect donations. Some projects had 0 donors. In order to return a value that was not an error, I had to use an IFERROR formula: =IFERROR(ROUND(E2/L2,2),0). This formula tells Excel that if the result of dividing the total pledges by number of donors is an error, then return the value "0". An average donation of "0" is easier to read than #DIV/0! 

Another complication found in the original data is that time was represented by Unix timestamp, which I learned is a numeric code representing the number of seconds elapsed since midnight January 1, 1970. In order to convert a timestamp that looks like this: 

> ![image](https://user-images.githubusercontent.com/116853681/200135814-1303fe6c-ed94-4158-96bd-0c78945666ef.png)

to a date that looks like this:

> ![image](https://user-images.githubusercontent.com/116853681/200135860-947eac07-b4c2-4122-be00-1cd326362082.png)

I used a formula in Excel to convert the Unix timestamp to a day-month-year format. I created a new column "Date Created Conversion" and used the formula:
```
=(((J2/60)/60)/24)+DATE(1970,1,1)
```
- ```=``` tells Excel that we're using a formula.
- ```(((J2/60)/60)/24)``` divides J2 (the first cell in the Launched_at column) by 60 (seconds), then divide that by 60 (minutes), then divide that by 24 (hours).
- ```+DATE``` tells Excel we're using the DATE formula.
- ```(1970,1,1)``` is the date that the Unix timestamps began counting from, also known as the **epoch**. [^1]

I was able to confirm that this formula works by checking the original unix timestamps with this [Unix Timestamp converter tool](https://www.unixtimestamp.com/). Fun!   

[^1] The explanation for converting Unix Timestamp to MM/DD/YYYY was found in section **1.3.3 Timing Success** of the Data Analytics Bootcamp modules.

## Results

1. Conclusions about the Outcomes based on Launch Date

   -Every month, there are more successful theater campaigns than failed theater campaigns. This means that Louise is likely to encounter success no matter which month she chooses to launch her campaign for funding **Fever**.
   
   -The month with the most successful campaigns vs failed campaigns is May. June and July also have higher than average successful Kickstarter campaigns for funding theater projects. Louise would be smart to launch her Kickstarter campaign during the summer months of May, June or July. Louise should not plan a Kickstarter launch for December as the least amount of successful projects were launched near the end-of-year holidays.

2. Conclusion about Outcomes based on Goals

   -Louise indicated at the start of this project that she has a goal of $12,000 for her campaign to fund her play. It appears that she is only slightly more likely to have a successful campaign than not in this range of $10,000 to $14,999. 

3. Limitations of this dataset

   -Age of the data: The years represented by these Kickstarter projects are as old as 13 years (from 2009) and only as recent as 2017. We have no data from the past five years. Given the advent of the recent pandemic, we might find different outcomes based on goals, as the entertainment industry and global economy have changed during this time. 
   
   -Readability of the data: Some of the data needs to be converted, for example the Unix timestamp to date conversion explained above. Further, after creating the new date column, I pulled Year out and to populate a new column which only listed year.
   
   -Errors in the data: Because I used a formula to calculate average donations which used the Kickstarter column for amount Pledged and number of Backers, I got a #DIV/0 error because some campaigns had no backers. In order to debug this error, I used an IFERROR formula in excel to clean up the data in this column. 
   
   -Limited sample size of data: The original Kickstarter dataset has over 4000 records of Kickstarter projects. By the time I filtered these down to the number of plays to those which were successful, failed or canceled, I was looking at 1046 records. If I were to pare this number down further to include only Kickstarter projects for plays within the US, I would be looking at 671 records.

4. What are some other possible tables and/or graphs that we could create?
   -Box and Whisper Plot: Analysis using a box plot on US plays to compare the distribution of campaign goals and distribution of total amounts pledged. Outliers skewing the data might be found.
   
   -Average Donation by Length of Campaign
   
   -US Play Outcomes by Launch Date 
   
   -US Play Outcomes Based on Goals
   
   -A table to analyze success rate as a function of number of backers for crowdfunding play projects in the US
