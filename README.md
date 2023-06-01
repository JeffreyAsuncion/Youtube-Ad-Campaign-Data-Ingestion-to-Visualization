# Data-Engineering-Project-001-Youtube-Ad-Campaign-End-to-End-Project

## Project Name - Youtube Ad Campaign End-to-End Project

## Project Requirements

We have a client that wants to run new ad campaigns online and they have selected their main advertising channel as youtube. They want to understand some of the initial questions that they have, such as: how to categorize videos based on comments and stylistics and what factors affect how popular a youtube video will be. These are the things they want to understand before actually investing money in the youtube campaign. 


## Project Goals

We have data ingestion so we will have data coming from multiple sources then we will design an ETL pipeline to extract transform and load our data easily. We will also build a data lake so that we can easily organize our data and build a data pipeline around it. It should be scalable. So, we will be using AWS Cloud. In the end, we will build a dashboard to easily visualize and understand what is happening in the data. 

![ProjectArchitecture](img/youtubeAdCampaignArchitecture.jpg)


### Step 1: Datasets

For Youtube-Ad-Campaign End-to-End Project, the Kaggle - Trending YouTube Video Statistics dataset can be found at https://www.kaggle.com/datasets/datasnaek/youtube-new. 

This dataset includes several months (and counting) of data on daily trending YouTube videos. Data is included for the US, GB, DE, CA, FR, RU, MX, KR, JP, and IN regions (USA, Great Britain, Germany, Canada, France, Russia, Mexico, South Korea, Japan, and India respectively), with up to 200 listed trending videos per day.
Each region’s data is in a separate file. Data includes the video title, channel title, publish time, tags, views, likes and dislikes, description, and comment count.
The data also includes a `category_id` field, which varies between `region`. To retrieve the categories for a specific video, find it in the associated JSON. One such file is included for each of the five regions in the dataset.
Download the dataset with consists of `JSON` files and `CSV` files to your local machine.



### Step 2: Data Lake - Raw Bucket

Write scripts to load datasets from the local environment to S3 raw bucket. Using the AWS CLI and S3 API run the script `ingestion_local_to_raw.sh` to ingest the datasets from the local to raw bucket. 

After the initial EDA (Exploratory Data Analysis), the JSON files and CSV files will need preprocessing before continuing. The JSON files will need parsing and converting the dataset from JSON to Parquet format. The CSV files need to convert certain column data types from `string` to `bigint` and the necessary conversion from CSV format to Parquet Format.


**Step 3:** Cleansed Bucket.
After the initial EDA (Exploratory Data Analysis), the JSON files and CSV files will need preprocessing before continuing. The JSON files will need parsing and converting the dataset from JSON to Parquet format. The CSV files need to convert certain column data types from `string` to `bigint` and the necessary conversion from CSV format to Parquet Format. The preprocessing for the CSV file  `etl_cleansed_csv_to_parquet.py` and The JSON file will be preprocessed by AWS Lambda Function `lambda_function.py` set to an S3 upload Trigger. 


**Step 4:** Reporting Bucket.
Created an ETL to build reporting layer which is a join of the two cleansed tables.  The `etl_parquet_analytics_version` ETL glue job will run an ETL to join the two cleanse tables 


## Data Analytics

**Step 5 :** Tableau Dashboard
Create a Dashboard by making a Connection from Tableau to Athena to access the reporting layer. In order to keep costs at a minumim, Tableau was used instead of QuickSight.

![ProjectAnalyticsReport](img/youtubeAdCampaignFinalAnalytics.jpg)


<u>Next Steps</u>

* Sentiment analysis in a variety of forms
* Categorising YouTube videos based on their comments and statistics.
* Training ML algorithms like RNNs to generate their own YouTube comments.
* Analysing what factors affect how popular a YouTube video will be.
* Statistical analysis over time