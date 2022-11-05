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

![Image of original column with too much data](

The dataset included Kickstarter projects for everything from opening restaurants to producing television shows. In order to bring this dataset down to a more manageable subset, I created a new sheet with a pivot table Analysis conducted on almost 1400 theater funding projects include 1066 plays, but also 140 musicals and 187 spaces.   

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?
Louise indicated at the start of this project that she has a goal 

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create?
