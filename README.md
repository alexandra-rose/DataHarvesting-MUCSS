# DataHarvesting-MUCSS


--Preparing for the Reddit API--

In order to be able to execute the code, especially the Reddit API, some prior steps are needed. In order to access the Reddit API you need to get a client-id and a client-secret from the Reddit website. In order to do this we need to use OAuth2 to get our ID and tokens. To use the OAuth2, you need to have a pre-existing account with Reddit, so if you don't have one, make one as the first step!

In case needed OAuth2 support documentation can be found here: https://github.com/reddit-archive/reddit/wiki/OAuth2

Next you need to go to this website https://www.reddit.com/prefs/apps and click "are you a developer? create an app...", and create an application with your account. The details of the application don't matter, you can put whatever reasonable information there that you like. Once this is made, you should get a 'personal use script' code and a 'secret' code. This information you need to save. 

Next you can move to the Reddit API code, make sure you have all the packages installed and in use. Then you need to input your own API credentials into the code so you can get the temporary token to be able to scrape the data. The tokens expire, so every now and then you need to get a new token. This was put into a function request_token. 

