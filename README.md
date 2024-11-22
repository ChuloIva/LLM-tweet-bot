# Automated Twitter Bots Repository

## Overview

This repository contains two Python scripts designed to automate interactions on Twitter by leveraging trending topics and AI-generated content. The bots aim to enhance engagement by providing timely, relevant, and insightful tweets or replies based on current trends and gathered information from various sources.

Both bots share common functionalities:

- **Trending Topics Retrieval**: Fetch the latest trending topics from Google Trends to ensure content is current and relevant.
- **Topic Filtering**: Utilize AI models to select and focus on topics of interest, such as world events, politics, science, and psychology.
- **Information Gathering**: Collect additional context from multiple sources including Brave Search, Reddit, NewsAPI, and Wikipedia to enrich content.
- **AI Content Generation**: Use AI models to generate tweets or responses that are contextually aware and engaging.
- **User Interaction**: Provide mechanisms for user approval or selection before posting to Twitter, ensuring control over the content.
- **Twitter Integration**: Interact with the Twitter API to post tweets or reply to existing tweets seamlessly.

By combining data gathering and AI-driven content creation, these bots facilitate meaningful Twitter interactions with minimal manual effort.

---

## Projects Included

### 1. Automated Tweet Generation Bot

- **Purpose**: Automatically generates and posts tweets based on trending topics.
- **Unique Features**:
    - Prompts the user to approve or reject the generated tweet before posting.
    - Focuses on creating original tweets to share with followers.

### 2. Automated Twitter Interaction Bot

- **Purpose**: Searches for recent tweets related to trending topics and generates insightful responses.
- **Unique Features**:
    - Provides a menu-driven interface for users to select and post responses.
    - Interacts with existing tweets to engage with the Twitter community.
    - Stores tweet data in a Google Sheet for tracking and management.

---

## Setup

### Set Up API Keys and Credentials

- Obtain API keys and credentials for all the required services:
    - Google Trends API
    - Brave Search API
    - Reddit API
    - NewsAPI
    - Wikipedia API
    - Twitter API
    - Google Gemini AI API (for content generation)
    - Google Sheets API (for the interaction bot)
- Store them securely using environment variables or a `.env` file.
- If using a `.env` file, ensure it is in the same directory as the scripts.

### 4. Configure User Data

- Replace placeholder code where user data is retrieved with your actual methods of accessing credentials.

### 5. Google Sheets Setup (for the Interaction Bot)

- Share your Google Sheet (named `Tweet_data_table`) with the service account email provided by `gspread`.
- Ensure the Google Sheets API is enabled in your Google Cloud Console.
