# Automated Twitter Responder Using Google Gemini AI

## Overview

This project is an automated system that interacts with Twitter by searching for recent tweets on specified topics, gathering contextual information from various sources, and generating thoughtful responses using Google Gemini AI models. The primary goal is to engage with trending topics and contribute meaningful insights by leveraging AI-generated content.

## Features

- **Trending Topics Fetcher**: Retrieves current trending topics from Google Trends.
- **Topic Filtering**: Utilizes Google Gemini AI to filter and select relevant topics based on a custom system prompt.
- **Contextual Data Gathering**:
    - **Brave Search API**: Fetches additional information and web results related to the topics.
    - **Reddit Discussions**: Retrieves top Reddit discussions and comments on the selected topics.
    - **News Articles**: Gathers recent news articles from specified sources using the NewsAPI.
    - **Wikipedia Summaries**: Obtains concise summaries from Wikipedia for deeper understanding.
- **Twitter Interaction**:
    - Searches for recent tweets matching the keywords.
    - Extracts keywords from tweets using AI.
    - Generates AI-driven responses to tweets.
    - Posts responses to selected tweets.
- **Data Management**:
    - Stores tweets and related data in a Google Sheet for tracking and management.
    - Provides a user interface via the console for selecting tweets and responses.

## Technologies Used

- **Programming Language**: Python
- **Execution Environment**: Google Colab (optional)
- **APIs and SDKs**:
    - Google Gemini AI SDK (`google.generativeai`)
    - Twitter API (`tweepy`)
    - Reddit API (`praw`)
    - Brave Search API
    - Google Trends API (`pytrends`)
    - NewsAPI (`newsapi-python`)
    - Wikipedia API (`wikipedia`)
    - Google Sheets API (`gspread`)
- **Libraries**:
    - Rich (`rich`) for enhanced console output
    - Pandas (`pandas`) for data manipulation

## Setup Instructions

### 1. Environment Setup

- **Python Installation**: Ensure Python 3.7 or higher is installed.
- **Package Installation**: Install required packages using pip:
    
    ```bash
    pip install rich praw tweepy pytrends python-dotenv gspread pandas google-generativeai newsapi-python wikipedia
    
    ```
    

### 2. API Credentials

Obtain API keys and credentials for the following services:

- **Google Gemini AI**
- **Twitter API**
- **Reddit API**
- **Brave Search API**
- **NewsAPI**
- **Google Sheets API**

Store these credentials securely. In the code, credentials are accessed using `userdata.get('KeyName')`, which assumes they are stored in Google Colab's `userdata` or environment variables.

### 3. Google Sheets Setup

- **Service Account**: Create a service account and download the JSON key file.
- **Authorization**: Use the `gspread` library to authorize access to Google Sheets:
    
    ```python
    gc = gspread.service_account(filename='path_to_service_account.json')
    
    ```
    
- **Spreadsheet Creation**: The script will attempt to open a spreadsheet named `Tweet_data_table`. If it doesn't exist, it will create one.

### 4. Running the Script

- **Execution**: Run the script in Google Colab or a local environment.
- **User Interaction**: The script provides console prompts for user input when selecting tweets and responses.
- **Automated Job**: The `job()` function orchestrates the workflow, which can be scheduled or run manually.

## Workflow Overview

1. **Initialize Console and APIs**: Set up the rich console for output and configure API clients.
2. **Fetch Trending Topics**: Retrieve current trending topics from Google Trends.
3. **Filter Topics**: Use Google Gemini AI to select relevant topics based on a system prompt.
4. **Gather Contextual Information**:
    - Fetch additional web information using Brave Search API.
    - Retrieve Reddit discussions and comments.
    - Obtain recent news articles using NewsAPI.
    - Get Wikipedia summaries.
5. **Search Recent Tweets**: Use the Twitter API to find recent tweets related to the selected keywords.
6. **Store Tweets**: Save tweet data in a Google Sheet for tracking.
7. **Generate Responses**:
    - Extract keywords from each tweet using AI.
    - Gather context for the extracted keywords.
    - Generate AI-driven responses to each tweet.
8. **User Selection and Posting**:
    - Display a menu of tweets and generated responses.
    - Allow the user to select which response to post.
    - Post the selected response as a reply to the tweet.
    - Remove the replied tweet from the Google Sheet.

## Important Functions

- **`initialize_sheet()`**: Prepares the Google Sheet by adding headers if it's empty.
- **`get_trending_topics()`**: Fetches trending topics from Google Trends.
- **`filter_trending_topics(trending_topics, system_prompt)`**: Filters topics using AI based on a system prompt.
- **`get_additional_info(query)`**: Retrieves additional information related to a query using the Brave Search API.
- **`get_reddit_discussion(topic)`**: Gets top Reddit discussions and comments on a topic.
- **`get_news_data(keywords)`**: Fetches news articles related to the keywords.
- **`get_wikipedia_data(keywords)`**: Obtains summaries from Wikipedia for the keywords.
- **`search_recent_tweets(keywords, max_results)`**: Searches for recent tweets matching the keywords.
- **`extract_keywords_from_tweet(tweet_text)`**: Extracts significant keywords from a tweet using AI.
- **`generate_responses_to_tweets(tweet_data)`**: Generates thoughtful responses to tweets using AI.
- **`display_menu_and_post_response(responses)`**: Displays options for the user to select and posts the chosen response.
- **`job()`**: Main function that ties together the workflow and can be scheduled to run periodically.

## Usage Notes

- **User Interaction**: The script requires user input to select tweets and responses before posting.
- **Data Management**: Tweets are stored in a Google Sheet, allowing for tracking and avoiding duplicate responses.
- **Error Handling**: The script includes error handling for API rate limits and retries failed requests.
- **Customization**:
    - Modify the `system_prompt` in `filter_trending_topics` to change topic selection criteria.
    - Update the list of `keywords` in the `job()` function to search for different topics.
    - Adjust API configurations and credentials as needed.

## Considerations

- **API Limits**: Be mindful of API rate limits for Twitter, Reddit, Brave Search, and other services.
- **Content Compliance**: Ensure that generated content complies with platform policies and guidelines.
- **Security**: Keep API keys and credentials secure. Do not expose them in code repositories or logs.
- **Ethical Use**: Use the AI capabilities responsibly, avoiding spam and respecting user privacy.

## License

This project is licensed under the GNU License.

## Contributing

Contributions are welcome! Please submit a pull request or open an issue to discuss improvements or additions.

## Acknowledgments

- **Google Gemini AI** for powerful AI content generation free experimental tier.
