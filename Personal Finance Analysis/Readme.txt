# Personal Finance Google Looker Studio Dashboard

A project that utilizes Google Looker Studio to analyze personal financial data and visualize expenses through an interactive dashboard.

> _"Data analysis is not just about presenting data, but to build a story and create a meaningful narrative from the raw data. At the end of the day, that's what analytics is all about - not about writing code, not about crunching numbers, not about memorizing formula syntax - it's about deriving meaning and context from the data and, more importantly, using it to make real change."_
> _- Chris Dutton, Maven Analytics_


## Problem Description

As one should, I have been keeping track of all my daily spending using Microsoft Excel. Using basic sorting/filtering in Excel I'm able to see a very high-level overview of my spending. In order to perform data analysis at a more deeper level, we will turn my static Excel data into dynamic Google Looker Studio dashboards.


## Project Goals

Here are the questions I would like the Google Looker Studio dashboards to answer:
- Monthly spending (in a given year).
- How much money spent per item category.
- List all expenses with comments.
- How much money spent per location.
- The number of purchases in various price ranges.
- Quarterly and weekly spending information.
- Various average costs (per week, month, day).
- Comparison of food costs to restaurant costs.
- Spending behavior when I'm sick.
- Comparison of weekday and weekend spending.

In order to answer these questions, I invested time in planning the Google Looker Studio measures I would need to create and also planned a rough outline of the dashboard visuals I wanted. 


## Data Analysis Summary

Here are the dashboards that I created. If you would like to actually play around with these dashboards see the end of this readme for instructions:

![alt text][ExecSumm]

![alt text][Granular]


## Hardware and Software Used

- Google Big Query
- Windows 11 Machine
- Google Looker Studio 
- Microsoft Excel
- Apple iPad (7th Gen) and pencil


## Explanation of Project Files

Here is a brief description of each file/folder found in this GitHub repository.

### **Finance_Data/20xx**
This is the folder that contains each month's Excel data in a separate Excel workbook. The dates (currently) range from Aug 2018 - Dec 2020.

### Table_quey.sql
This sql script import all Excel  sheets to a single table Finance_Data. 

### Finance_Data.xlsx
This is a copy of the original Excel file that I was using to keep track of my spending.

### Personal_Finance_Analysis.pdf
This is the file containing the finance dashboards.
https://lookerstudio.google.com/s/sFc85WSvY-E


## Data Collection Methodology

I collected this data by keeping all purchase receipts and inputting the data manually into Excel. The information I kept track of was: Date, Item Category, Price, Location, Comment.

In order to import this data into Google Looker Studio, it was quite the process. Since the data was contained in *multiple Excel sheets in the same Excel workbook*, I first had to separate the sheets into their own Excel workbook - this turned out to be the easiest avenue to importing the data.


## Data Cleaning

There was quite a bit of data cleaning to do. I had to do some basic editing of the 'Item' category column, in order to have consistent categories. For example, I had 'hair cut', 'Hair cut', 'Hair-Cut' as separate categores, and so had to standardize this into simply a 'Hair Cut' category.

There was a lot of work needed to be done with dates. Some dates were of a 'Text' type, some were a 'General' type, and still others were the 'Date' type. These had to be standardized.

Finally, only a few rows contained null entries, so I simply chose to remove these rows from the overall dataset; This would not drastically affect the variance of the overall data.


## Measure Creation & Visualizations

In order to help answer the questions listed above, I started by making three other tables: (i) Calendar Lookup, (i) Item Lookup, (iii) Location Lookup.

The calendar lookup contains each range of dates from the data. From this I created various other useful calculated columns including month name/number, month-and-year, quarter,  and end of week/month.
  
The item lookup table contained a single column of each distinct Item category. While working through the project, I realized that every month had a rental payment listed. It didn't make sense to me to have this consistently in each month, so I created a filter that can be used to manually include or exclude rental payments. To accomplish this I needed a second column in the Item Lookup table to represent the 'Rent' item as a Boolean.
  
The location table contains a single column of each distinct location of purchase.

Once these lookup tables were ready, I followed my planned layout above and created each visual one at a time. As I created these, I also created the associated measure I would need to portray the data. Some of the measures I made were:
- total cost
- price ranges
- average cost per day, week, year
- Boolean to adress my sick days

The main visuals I used were 'slicers'. I created calendar slicers for overall date, year, quarter, month, and day of week. With these one has a lot of options as to what granularity they wish to visualize their data with respect to dates. I also have two slicers for weekday/weekend and healthy/sick selections. There is also a slicer that acts as a dropdown to select various purchase price ranges.


## Conclusion

Using Google Looker Studio I was able to visualize my purchases data in an interactive way. This allowed me to drill deeper into my spending behaviour and with this information I can now be more conscientious of what I choose to spend my money on.


## How You Can View My Google Looker Studio Dashboards


## Future Steps

For future improvement, we can consider the following ideas:
- Attempt to create more visually appealing dashboards (perhaps you can find a template to use?).
- Perhaps there is a way to generalize this dashboard so anyone can use it? (Launch via Docker container?)
  - Would need to ask users to standardize their Excel sheets a certain way?
- Think of new informative metrics that may be useful.


## Author

- **tariqulismail** (https://github.com/tariqulismail/)


## Acknowledgements

- Creators of Google Looker Studio - It's a pretty amazing tool!
- All the kind and patient cashiers who took the time to print out a receipt for me.
- Viewers of my GitHub page...Thanks for visiting!

