# DataHarvesting-MUCSS

## ***IMDb Top 250 Web Scraper***

This R script scrapes details about movies listed in IMDb's Top 250 chart. The list can be found in <https://www.imdb.com/chart/top/?ref_=tt_awd>.

### **Running the Scraper**

1.  Open the R script called “**Markdown For IMDB web scraping.Rmd”** in RStudio.
2.  Set your user agent in the beginning. 
3.  Follow the instructions below regarding the Reddit API, and then you can run the whole script. 

## *Preparing for the Reddit API*

In order to be able to execute the code, especially the Reddit API, some prior steps are needed. In order to access the Reddit API you need to get a client-id and a client-secret from the Reddit website. In order to do this we need to use OAuth2 to get our ID and tokens. To use the OAuth2, you need to have a pre-existing account with Reddit, so if you don't have one, make one as the first step!

In case needed OAuth2 support documentation can be found here: <https://github.com/reddit-archive/reddit/wiki/OAuth2>

Next you need to go to this website <https://www.reddit.com/prefs/apps> and click "are you a developer? create an app...", and create an application with your account. The details of the application don't matter, you can put whatever reasonable information there that you like. In the URI part we should fill it out with any link (ex.[**https://www.reddit.com/r/subredditname.json**](https://www.reddit.com/r/subredditname.json)). Once this is made, you should get a 'personal use script' code and a 'secret' code. This information you need to save.

Next you can move to the Reddit API code, make sure you have all the packages installed and in use. Then you need to input your own API credentials into the code so you can get the temporary token to be able to scrape the data. The tokens expire, so every now and then you need to get a new token. This was put into a function request_token.

### **Sentiment Analysis of the Feature Reviews**

A sentiment analysis is performed on the text of the featured reviews collected for each movie. It uses the tidy text package to classify each review as positive, negative, or neutral based on the sum of the sentiment scores of the words contained in the review. This is a crucial step for understanding the general sentiment of the audience towards the movie.

### **Sentiment Analysis of Reddit Comments**

A sentiment analysis is performed on the comments attained from the Reddit API collected for each movie. It uses the tidy text package to classify each review as positive, negative, or neutral based on the sum of the sentiment scores of the words contained in the comment. This is a crucial step for understanding the general sentiment of the audience towards the movie in a social media platform.

### **Plots**

Three descriptive plots were created to visualize the data set:

1.  Sentiment Count for the First Three Movies: This plot displays the count of positive, negative, and neutral review classifications for the top three movies in the data set. It helps to understand which is the general sentiment towards this top three movies according to Reddit.
2.  Top Genres by Review Classification: This plot displays the count of positive, negative, and neutral review classifications for the top genres in the data set. It helps in understanding which genres are most favored according to the sentiment analysis of the feature reviews.
3.  Number of Movies from the Top 250 per Decade: A bar chart that shows the distribution of the movies in the IMDb Top 250 list across different decades. This plot provides insights into which decades are most represented in the list.

**Notes**

-   The scraper is designed to be polite to the server by including a delay between requests. This is controlled by the **Sys.sleep(runif(1, 1, 3))** function call, which sleeps for a random duration between 1 to 3 seconds between each request.

-   The script includes error handling to skip any URLs that might cause an error during the scraping process.

-   The structure of web pages can change over time. If IMDb updates the structure of its pages, the scraper may need to be updated as well.
