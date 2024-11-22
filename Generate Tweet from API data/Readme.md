# Automated Tweet Generation Bot

## Overview

This bot is designed to automatically generate and post tweets based on trending topics. It leverages various APIs and AI models to gather data, filter topics, generate content, and interact with the user before posting tweets to Twitter.

## Features

- **Fetch Trending Topics**: Retrieves the latest trending topics from Google Trends.
- **Filter Topics**: Uses an AI model to filter and select relevant topics based on specified criteria.
- **Data Gathering**: Collects additional information from multiple sources:
    - Brave Search API
    - Reddit API
    - News API
    - Wikipedia API
- **Keyword Generation**: Generates keywords from the collected data to refine the content.
- **Content Generation**: Utilizes an AI model to generate the final tweet content based on the gathered information.
- **User Interaction**: Prompts the user to approve or reject the generated tweet before posting.
- **Tweet Posting**: Posts approved tweets to Twitter using the Twitter API.

## Setup and Installation

### 1. Clone the Repository

Clone the repository or copy the bot script to your local environment or Google Colab workspace.

### 2. Install Dependencies

Install the required Python libraries:

```bash
pip install rich praw tweepy pytrends python-dotenv google-colab newsapi-python wikipedia google-generativeai

```

### 3. API Credentials

Obtain API credentials for the following services:

- **Google Gemini AI**
- **Reddit API**
- **Brave Search API**
- **Twitter API**
- **News API**

Store your API credentials securely. If using Google Colab, you can store them in `google.colab.userdata`:

```python
from google.colab import userdata
userdata['API_KEY_NAME'] = 'your_api_key'

```

### 4. Mount Google Drive (if using Google Colab)

Mount your Google Drive to access external files:

```python
from google.colab import drive
drive.mount('/content/drive')

```

### 5. Prepare Additional Files

Ensure the following files are placed in your Google Drive or accessible directory:

- **Training Data**: `/content/drive/MyDrive/Google_bounty/When_AIs_Play_God.txt`
- **Final Prompt**: `/content/drive/MyDrive/Google_bounty/Prompt_final.txt`
- **Additional Prompt**: `/content/drive/MyDrive/Google_bounty/COT_sociology_prompt.txt`
- **News Sources**: `/content/drive/MyDrive/Google_bounty/source_ids.txt`

## How to Use

### 1. Initialize the Bot

Import the necessary modules and initialize the AI model:

```python
from rich.console import Console
from rich import print
import google.generativeai as genai

console = Console()
genai.configure(api_key=userdata.get('Google'))
model = genai.GenerativeModel("gemini-1.5-pro")

```

### 2. Set Up API Clients

Configure the Reddit, Brave Search, Twitter, and News API clients using your API credentials.

### 3. Run the Main Job Function

Execute the `job()` function to start the bot:

```python
job()

```

### 4. Workflow Steps

The bot will perform the following steps:

1. **Fetch Trending Topics**: Retrieves trending topics from Google Trends.
2. **Filter Topics**: Uses the AI model to select relevant topics.
3. **Gather Additional Information**: Collects data from Brave Search, Reddit, News API, and Wikipedia based on the selected topics.
4. **Generate Keywords**: Creates a list of keywords from the collected data.
5. **Collect Further Data**: Gathers more information using the generated keywords.
6. **Generate Tweet Content**: Uses the AI model to generate the final tweet content.
7. **User Approval**: Prompts you to approve or reject the generated tweet.
    - **Approve**: The tweet is posted to Twitter.
    - **Reject**: The bot generates a new tweet.

## Functions Breakdown

### `get_trending_topics()`

Fetches trending topics from Google Trends for the United States.

### `filter_trending_topics(trending_topics, system_prompt)`

Filters the list of trending topics based on criteria specified in the system prompt using the AI model.

### `get_additional_info(query, num_results=7)`

Retrieves additional information for a given query using the Brave Search API.

### `get_reddit_discussion(topic, limit=1)`

Fetches top Reddit discussions related to the specified topic.

### `get_news_data(keywords)`

Retrieves news articles related to the generated keywords using the News API.

### `get_wikipedia_data(keywords)`

Obtains summaries from Wikipedia for each keyword.

### `generate_keywords(trends_data, search_data, reddit_data, additional_prompt)`

Generates a list of keywords from the collected data using the AI model.

### `generate_content(final_context, news_data, wikipedia_data, brave_data, reddit_data, additional_instructions)`

Generates the final tweet content by processing all the collected data with the AI model.

### `job()`

The main function that orchestrates the entire workflow.

## Dependencies

- Python 3.x
- Libraries:
    - `rich`
    - `praw`
    - `tweepy`
    - `pytrends`
    - `python-dotenv`
    - `google-colab`
    - `newsapi-python`
    - `wikipedia`
    - `google-generativeai`

## Important Notes

- **Ethical Use**: Ensure that the content generated and posted adheres to ethical guidelines and platform policies.
- **API Limits**: Be mindful of API rate limits for the services used.
- **User Interaction**: The bot requires user input to approve tweets, providing control over the content being posted.

## License

This project is licensed under the GNU License.

## Contact

For questions or support, please contact the project maintainer.
