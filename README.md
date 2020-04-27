# udacity_data_wrangling
Repository for the Data Wrangling Project on Udacity

During assessing of gathered data, some quality and tidiness issues were found. For this project I
chose 9 quality and 2 tidiness issues that I was solving in the data cleaning process, going every
time through three parts of this process:
• defining,
• coding,
• and testing.
1. Firstly, I was dealing with some unneeded data in twitter table. Some entries in columns
in_reply_to_status_id,in_reply_to_user_id,retweeted_status_user_id,retweeted_status_id
and retweeted_status_timestamp indicate, that is not actually a tweets, but response or
retweets. Firstly I cleaned all the row which contained values in those columns and after it I
removed the columns themself (in Step 6).
2. After this I moved on with erroneous datatypes and change the type of the column ’tweet_id’
in all three tables integer to string.
3. One more issue in the twitter table was, that all the entries, written completly in lower or
upper case were no names. So they were replaced with ’NaN’.
4. Looking at the source column, I decided to extract only relevant information - where the
data coming from - using REGEX
5. Still the account has a unique rating system the numerator values has some outliers. Firstly
here I extracted the real rating from the text. After this I looked trough all the values of the
numerator. I saw that people sometime multiplying there rate with the amount of puppies
on the picture. For the consistency, I changed these values. Entries with too high rating like
1776 and 420 were obviously outliers and I dropped them. Also I recognized that few times
the rating was extracted not correct and also replaced those values with correct ones.
6. I also dropped columns with some information about repies and retweets. For retweet and
favorites information I will merge twitter and tweet_datalater.
7. In the dog stages(doggo, floofer, pupper, puppo columns) there were a lot ’None’ instead of
’NaN’, so non-null values were pictured incorrect. With the function replace I made needed
changes.
8. The last quality issue that I solved was strip ’+0000’ from the timestamp column and then
change the type to datetime.
For the tidiness part, I chose firstly to bring all the information together on one table twitter.
I am interested only in tweets that have pictures of the dogs included,so I merged this table with
images and removed all the rows that didn’t have .jpg-file. All information about retweets and
favourites I got from the tweet_datatable. After this step, I had all the needed data for my analyses
in one table.
Secondly, I made from 4 dog stages column (doggo, floofer, pupper, puppo columns) only one.
I was trying to do so with function melt(), but because the columns not always had some values it
made a lot of duplicates. So solved this issue with the extract function.
After all these steps, my data was ready for analysis and visualisation.
