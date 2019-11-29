# NF_Analysis_Project
 
# Questions 

#### Given the information you have and any light research you’d like to do on the topic, what insights can you draw?
I am going to start my analysis by looking for any patterns in usage. I am curious if people using this tool might measure low mood for example in the middle of the night if they are having trouble sleeping, or perhaps logging later in the day as this could indicate a poor night's sleep and then sleeping in. Additionally it might be interesting to look at a single user and how they use the tool to rate their experiences over time. It would be the hope that a person's mood improves with therapy over time, or stabilizes over time. So I will look to organize the data to see if these patterns exist. 

 #### What assumptions have you made about the data? 
 I have made the assumption that the user of this tool is using it multiple times a day in addition to the normal 8am prompt. I am also assuming that the number in the value column is the rating the person has given to that particular measure on the described 5 point Likert-scale. However, these seem to not be discrete as expected in the description. 
 
 #### What are 2-3 additional pieces of information that would be important to collect? 
I would like to know when the patient started treatment and if they have every had any gaps in treatment. The user with id of 2012 that I look at in depth on an average by month basis seems to have a drop in ratings from their 8th to 9th month of treatment. Knowing if there is a variable such as a gap in their treatment that could be the cause would be helpful. I do understand that healthcare record laws may prohibit this type of data. 

A point of confusion was the time stamp generated in the data. It seemed that most users were logging their information during the 12pm-3pm time frame. However the application prompts users at 8am. So I am not sure if this is a timezone issue for the user or if it is reported as the timezone of the server. So knowing information like the timezone and timestamp of the user locally could be helpful. 

A problem stated is that there isn't a good way right now to visualize the progress on these 4 measures. I would suggest using each of these independently and then allowing the health provider to show multiple features at the same time over those scaled. 

# Analysis Notes

#### For Replication
Please store the file in folder and put that file path into  the code for cell 2 in the Jupyter notebook. 
Also ensure that pandas, numpy, and matplotlib are installed for your version of python. 

#### Overview 
I started off by gathering some counts of the data to see the number of unique users and then the amount of logs for each of the users in the data set. Additional it is helpful to have the date column recognized as time stamp type. 

My first thought was to look at the hour that the user logged their measures. Then to use this formation to look at the usage based off of the four types of measures they could be logging. The histograms seem to show that all four of these measures follow a similar pattern. The usage spikes for all 4 types of measures between the hours reported here as 12pm - 2 pm. I believe these times could be the times recorded by the server and not the users own times since the users are prompted at 8am. 

Next I thought I could look at a single user and plot the density of their response considering the hour they logged their measure and the value reported. I took the user with user_id = 2012 because they had the most records as an example. I was able to provide a density plot where the lighter the region indicated the more dense grouping. Not only can we see what hour windows are most often used to log their measures but we can also see that during those time the person mostly has logged ratings of between 3.5-4.0 and 2.0-2.5. It might be useful to also facet this by the type of measure being reported and then create some additional density plots. 

Finally I thought about how we might look at their progress overtime. For this I decided to look at a simple line plot. I created a column with the time stamp to give us a categorical variable of YYYY-MM. Using that I performed a group by operation to find the mean and median of each year - month pair. Ensuring they were ordered from least recent to most I plotted them. Again the pattern between the two measures of central tenancy seemed similar. This user's ratings seems to have decreased over time, then rises during the 8th month of treatment only to drop again during the 9th and 10th month. As next steps repeating this process with another user would be helpful. Additionally generating a full set of summary statistics (count, min, max, quartiles, etc) would be helfpul to ensure that this isn't the result of poor reporting during the 9th month. I never checked to see how many times the user logged in that month. All of those pieces of information would be important before attempting to draw any conclusion from this singular graph. 

#### Next Steps
Moving to a more granular time series approach would be my next step. Using the full YYYY-MM-DD level to track at the day level or perhaps by week. I would also like to understand if seasonality could show up in the mood data. For that type of analysis we would need to have users with information for multiple full years, but if possible it could be interesting. 