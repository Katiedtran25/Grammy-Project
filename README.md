# Grammy-Project
Grammys Project


Are you excited to dive into data work for an exciting project at The Recording Academy? You know, the non-profit organization behind the Grammy Awards!

In this project, you'll work on real data from both websites owned by The Recording Academy, the non-profit organization behind the famous Grammy Awards. As you just learned, Ray Starck, the VP of Digital Strategy, decided to split the websites into grammy.com and recordingacademy.com to better serve the Recording Academy's various audience needs.

Now, you are tasked with examining the impact of splitting up the two websites, and analyzing the data for a better understanding of trends and audience behavior on both sites.

Are you ready?!?!

Let's do this!
Data Dictionary
To start, you will be working with two files, grammys_live_web_analytics.csv and ra_live_web_analytics.csv.

These files will contain the following information:

date - The date the data was confirmed. It is in yyyy-mm-dd format.
visitors - The number of users who went on the website on that day.
pageviews - The number of pages that all users viewed on the website.
sessions - The total number of sessions on the website. A session is a group of user interactions with your website that take place within a given time frame. For example a single session can contain multiple page views, events, social interactions.
bounced_sessions - The total number of bounced sessions on the website. A bounced session is when a visitor comes to the website and does not interact with any pages / links and leaves.
avg_session_duration_secs - The average length for all session durations for all users that came to the website that day.
awards_week - A binary flag if the dates align with marketing campaigns before and after the Grammys award ceremony was held. This is the big marketing push to get as many eyeballs watching the event.
awards_night - The actual night that Grammy Awards event was held.
Part I - Exploratory Data Analysis

Task 1
Import the pandas,numpy, and plotly.express libraries.

# Import libraries
import pandas as pd
import plotly.express as px
# RUN THIS CELL - DO NOT MODIFY
# this formats numbers to two decimal places when shown in pandas
pd.set_option('display.float_format', lambda x: '%.2f' % x)
Task 2
Load in the first two files for your analysis. They are the grammy_live_web_analytics.csv and ra_live_web_analytics.csv.

A. For the grammy_live_web_analytics.csv file store that into a dataframe called full_df

B. For the ra_live_web_analytics.csv file store that into a dataframe called rec_academy

C. Preview the dataframes to familiarize yourself with the data.

All files needed can be found in the datasets folder.
# Read in dataframes
full_df = pd.read_csv('datasets/grammy_live_web_analytics.csv')
rec_academy = pd.read_csv('datasets/ra_live_web_analytics.csv')
# preview full_df dataframe
full_df.head()
date	visitors	pageviews	sessions	bounced_sessions	avg_session_duration_secs	awards_week	awards_night
0	2017-01-01	9611	21407	10196	6490	86	0	0
1	2017-01-02	10752	25658	11350	7055	100	0	0
2	2017-01-03	11425	27062	12215	7569	92	0	0
3	2017-01-04	13098	29189	13852	8929	90	0	0
4	2017-01-05	12234	28288	12990	8105	95	0	0
# preview rec_academy dataframe
rec_academy.head()
date	visitors	pageviews	sessions	bounced_sessions	avg_session_duration_secs	awards_week	awards_night
0	2022-02-01	928	2856	1092	591	148	0	0
1	2022-02-02	1329	3233	1490	923	90	0	0
2	2022-02-03	1138	3340	1322	754	127	0	0
3	2022-02-04	811	2552	963	534	142	0	0
4	2022-02-05	541	1530	602	326	111	0	0
Task 3
We all know The Grammy Awards is the biggest music event in the music industry, but how many visitors does that bring to the website?

A. Create a line chart of the number of users on the site for every day in the full_df. See if you can spot the days the Grammys awards are hosted.

# Plot a line chart of the visitors on the site.
px.line(full_df, x ='date', y = 'visitors', title = 'Number of visitors on the days the Grammys awards are hosted by year')
Remark: The smaller spikes, typically around November/December of each year, are when the nominees are announced.

B. What can you say about the visitors to the website by looking at the graph?

Each year, there are two peak data events related to the Grammys: one occurs when the Recording Academy announces the nominees, and the other happens during the main showcase event. Viewership typically spikes on Grammy night when the winners are revealed. In 2021, the event saw high viewership. However, in 2022, traffic was lower due to the ceremony being held virtually. In 2023, data peaks were modest, largely due to a boycott by several artists, a disconnect with broader audiences, and controversies surrounding the voting system.

Task 4
Let's investigate what an "average" day looks like when the awards show is being hosted versus the other 364 days out of the year.

A. Use the pandas .groupby() to calculate the number of visitors on the site based on the values in the column awards_night.
Task 3
We all know The Grammy Awards is the biggest music event in the music industry, but how many visitors does that bring to the website?

A. Create a line chart of the number of users on the site for every day in the full_df. See if you can spot the days the Grammys awards are hosted.

# Plot a line chart of the visitors on the site.
px.line(full_df, x ='date', y = 'visitors', title = 'Number of visitors on the days the Grammys awards are hosted by year')
Remark: The smaller spikes, typically around November/December of each year, are when the nominees are announced.

B. What can you say about the visitors to the website by looking at the graph?

Each year, there are two peak data events related to the Grammys: one occurs when the Recording Academy announces the nominees, and the other happens during the main showcase event. Viewership typically spikes on Grammy night when the winners are revealed. In 2021, the event saw high viewership. However, in 2022, traffic was lower due to the ceremony being held virtually. In 2023, data peaks were modest, largely due to a boycott by several artists, a disconnect with broader audiences, and controversies surrounding the voting system.

Task 4
Let's investigate what an "average" day looks like when the awards show is being hosted versus the other 364 days out of the year.

A. Use the pandas .groupby() to calculate the number of visitors on the site based on the values in the column awards_night.
Task 5
When The Recording Academy decided to split their website into two domains, grammy.com and recordingacademy.com, the data capture for grammy.com was not affected. So the full_df variable needs to be split separately into two dataframes. The day the domains were switched is on 2022-02-01.

Create two new dataframes:

combined_site for all dates before 2022-02-01
grammys for all dates after (and including) 2022-02-01
# Split the data to separate the full_df into two new dataframes.
# One for before the switch of the websites and one for after
combined_site = full_df[full_df['date'] < '2022-02-01']
print(combined_site)
grammys = full_df[full_df['date'] >= '2022-02-01']
print(grammys)
            date  visitors  pageviews  sessions  bounced_sessions  \
0     2017-01-01      9611      21407     10196              6490   
1     2017-01-02     10752      25658     11350              7055   
2     2017-01-03     11425      27062     12215              7569   
3     2017-01-04     13098      29189     13852              8929   
4     2017-01-05     12234      28288     12990              8105   
...          ...       ...        ...       ...               ...   
1852  2022-01-27         2          2         2                 2   
1853  2022-01-28     32986      79160     36571             20268   
1854  2022-01-29     37899      79095     41920             25316   
1855  2022-01-30     39931      81186     43743             26636   
1856  2022-01-31     38221      92863     42291             21747   

      avg_session_duration_secs  awards_week  awards_night  
0                            86            0             0  
1                           100            0             0  
2                            92            0             0  
3                            90            0             0  
4                            95            0             0  
...                         ...          ...           ...  
1852                          0            0             0  
1853                         83            0             0  
1854                         63            0             0  
1855                         61            0             0  
1856                         67            0             0  

[1857 rows x 8 columns]
            date  visitors  pageviews  sessions  bounced_sessions  \
1857  2022-02-01     33209      74033     30472             13070   
1858  2022-02-02     30511      43642     20761             11814   
1859  2022-02-03     31502      44147     20830             12015   
1860  2022-02-04     26863      39483     18700             10731   
1861  2022-02-05     18014      35046     16860              9604   
...          ...       ...        ...       ...               ...   
2337  2023-05-27     14332      34178     15430              5424   
2338  2023-05-28     13798      31708     14662              5509   
2339  2023-05-29     20563      53396     22244              7005   
2340  2023-05-30     16105      37950     17264              6452  
2341  2023-05-31     31253      85686     33237              8200   

      avg_session_duration_secs  awards_week  awards_night  
1857                         69            0             0  
1858                         85            0             0  
1859                         90            0             0  
1860                         85            0             0  
1861                         75            0             0  
...                         ...          ...           ...  
2337                         75            0             0  
2338                         73            0             0  
2339                         92            0             0  
2340                         87            0             0  
2341                        106            0             0  

[485 rows x 8 columns]
# Run the following cell - DO NOT MODIFY
# .copy() prevents pandas from printing a scary-looking warning message
combined_site = combined_site.copy()
grammys = grammys.copy()
# print the shape of the combined_site dataframe
combined_site.shape
(1857, 8)
If done correctly, the combined_site dataframe should have a total of 1857 rows and 8 columns

Part II - It's all about KPIs
