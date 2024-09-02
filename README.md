# comment___classifierproject

**YouTube Comments Sentiment Analysis**

VADER (Valence Aware Dictionary and sEntiment Reasoner) is a sentiment analysis tool specifically designed for analyzing social media text and short-form content. It is based on a lexicon and rule-based approach, meaning it uses a predefined list of words that are associated with specific sentiment scores. VADER assigns sentiment scores to text in the following categories:

Positive: Indicates the presence of positive sentiments.
Negative: Indicates the presence of negative sentiments.
Neutral: Indicates the absence of strong positive or negative sentiments.

API Key and Setup:
The script begins by importing necessary libraries, including the googleapiclient.discovery for interacting with the YouTube API and SentimentIntensityAnalyzer from the VADER sentiment library.
An API key (API_KEY) is defined, which allows the script to access the YouTube Data API v3. The video_id is also set to specify which YouTube video's comments will be analyzed.

Connecting to YouTube Data API:
The build function from googleapiclient.discovery is used to create a service object that allows the script to communicate with the YouTube API.
The script then requests the top-level comments from the specified video in batches of up to 100 comments per API call.

Fetching Comments:
The script iterates through the comments, fetching them along with their like counts. If there are more than 100 comments, it continues to fetch additional pages of comments using the nextPageToken provided by the API.

Sentiment Analysis:
For each comment, the script uses VADER's SentimentIntensityAnalyzer to analyze the text and generate a sentiment score.
Based on the compound score provided by VADER, the script classifies each comment into one of three categories:
Positive: If the compound score is greater than or equal to 0.05.
Negative: If the compound score is less than or equal to -0.05.
Neutral: If the compound score is between -0.05 and 0.05.

Results Compilation:
The script counts the number of comments in each sentiment category (Positive, Negative, Neutral) and calculates the percentage of comments in each category.
It also aggregates the total number of likes across all comments.

Displaying Results:
The script prints out each comment with its corresponding sentiment and like count.
Finally, it summarizes the overall sentiment distribution and visualizes these results using a bar chart created with matplotlib.

**The output of the comment_classifier look like the below**
1. Comment: This video is amazing!
   Likes: 123
   Sentiment: Positive

2. Comment: I didn't like the content.
   Likes: 45
   Sentiment: Negative

...

Total Comments: 200
Total Likes: 2345
Positive Comments: 120 (60.0 %)
Negative Comments: 50 (25.0 %)
Neutral Comments: 30 (15.0 %)
