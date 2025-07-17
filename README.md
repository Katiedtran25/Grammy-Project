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
