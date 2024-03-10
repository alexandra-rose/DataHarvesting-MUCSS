# DataHarvesting-MUCSS

--Preparing for the Reddit API--

In order to be able to execute the code, especially the Reddit API, some prior steps are needed. In order to access the Reddit API you need to get a client-id and a client-secret from the Reddit website. In order to do this we need to use OAuth2 to get our ID and tokens. To use the OAuth2, you need to have a pre-existing account with Reddit, so if you don't have one, make one as the first step!

In case needed OAuth2 support documentation can be found here: https://github.com/reddit-archive/reddit/wiki/OAuth2

Next you need to go to this website https://www.reddit.com/prefs/apps and click "are you a developer? create an app...", and create an application with your account. The details of the application don't matter, you can put whatever reasonable information there that you like. Once this is made, you should get a 'personal use script' code and a 'secret' code. This information you need to save. 

Next you can move to the Reddit API code, make sure you have all the packages installed and in use. Then you need to input your own API credentials into the code so you can get the temporary token to be able to scrape the data. The tokens expire, so every now and then you need to get a new token. This was put into a function request_token. 

## ***IMDb Top 250 Web Scraper***

This R script scrapes details about movies listed in IMDb's Top 250 chart. The list can be found in <https://www.imdb.com/chart/top/?ref_=tt_awd>.

### Variables

The Movie Attributes included in the data set are the following:

-   Title.

-   Year.

-   MPAA rating: this is the Motion Picture Association film rating system. The complete guide for what each number or letter means can be found in <https://www.filmratings.com/>. However, variations are found for certain movies not completely supervised by the Motion Picture Association.

-   Duration of the film.

-   IMDB score.

-   Director.

-   Main actor.

-   Supporting Actor.

-   Main writer.

-   Second writer.

-   Release date.

-   Genre.

-   Budget: the estimated total used in the creation of the movie. The currency is generally in dollars, however there are some exceptions for the movies that have no relation to the US movie market.

-   Gross Worldwide Revenue: the estimated total revenue attained for each movie in dollars.

-   Title of featured review: main title of the review featured in the IMDB page at the time of the scraping.

-   Text of the featured review: complete text of the featured review found in the IMDB page.

-   Awards and nominations: number of awards and nominations given to the movie at the time of the scraping.

-   Oscar information: number of Academy Award wins and nominations.

### **Prerequisites**

Before running this script, install the following R packages:

-   **rvest**: For web scraping

-   **httr**: For handling HTTP requests

-   **dplyr**: For data manipulation

-   **tidytext**: For text mining and sentiment analysis.

-   **purrr**: For functional programming tools.

-   **ggplot2**: For creating plots.

-   **scales**: For formatting scales in plots.

### **Running the Scraper**

1.  Open the R script called “**Markdown For IMDB web scraping.Rmd”** in RStudio.

2.  Run the entire script to scrape data from the IMDb Top 250 chart.

3.  The script will create two data frames: **movies_df**, which contains details from a test sample of 5 movie URLs, and **movies_df_final**, which contains details from all movie URLs in the Top 250 chart. The first data frame was created to show a preview of how the data is being collected and not having to wait for an extended period in order to get the full data set.

### **Sentiment Analysis of the Feature Reviews**

A sentiment analysis is performed on the text of the featured reviews collected for each movie. It uses the tidy text package to classify each review as positive, negative, or neutral based on the sum of the sentiment scores of the words contained in the review. This is a crucial step for understanding the general sentiment of the audience towards the movie.

### **Plots**

Three descriptive plots were created to visualize the data set:

1.  Top Genres by Review Classification: This plot displays the count of positive, negative, and neutral review classifications for the top genres in the data set. It helps in understanding which genres are most favored according to the sentiment analysis of the feature reviews.
2.  Number of Movies from the Top 250 per Decade: A bar chart that shows the distribution of the movies in the IMDb Top 250 list across different decades. This plot provides insights into which decades are most represented in the list.
3.  Bubble Chart of Movie Budgets vs. IMDB Score: This scatter plot visualizes the relationship between the budgets of the movies and their IMDb scores, with the size of each point representing the budget of the movie. The color gradient from blue to red indicates the range of IMDb scores. This plot helps in exploring whether there's a correlation between the movie's budget and its success on IMDb.

**Notes**

-   The scraper includes a user agent string within the set_config() function to simulate a real browser session. The user agent string is specified as **"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/121.0.0.0 Safari/537.36; Sofia Villamil / [sofia.v1999\@gmail.com](mailto:sofia.v1999@gmail.com)"** in the script. Replace "Sofia Villamil / sofia.v1999\@gmail.com" with your actual user agent details if needed.

-   The scraper is designed to be polite to the server by including a delay between requests. This is controlled by the **Sys.sleep(runif(1, 1, 3))** function call, which sleeps for a random duration between 1 to 3 seconds between each request.

-   The script includes error handling to skip any URLs that might cause an error during the scraping process.

-   The structure of web pages can change over time. If IMDb updates the structure of its pages, the scraper may need to be updated as well.

