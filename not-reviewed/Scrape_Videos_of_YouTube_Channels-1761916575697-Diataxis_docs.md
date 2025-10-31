# Explanation

🎥 The purpose of this workflow is to automate the collection and analysis of video data from multiple YouTube channels. It eliminates manual scraping by systematically retrieving videos within a configurable time window, enriching them with metadata, and storing the results for content monitoring, performance tracking, and trend analysis. This enables users to gain insights into video engagement metrics efficiently.

👥 This workflow is tailored for content strategists, marketing professionals, and data analysts who require regular updates on YouTube channel performance. It suits individuals or teams involved in competitive analysis, content planning, or reporting, especially those managing multiple channels and needing structured data for decision-making.

🔄 Conceptually, the workflow operates in sequential stages: initiation via a scheduled trigger, configuration of parameters like channel handles and time range, scraping of video data using YouTube APIs, enrichment with additional metadata, data transformation for consistency, and storage across multiple platforms. Key decision points include time window settings and batch processing to handle API limits, ensuring scalable and reliable data extraction.

# How-to Guide

🚀 1. Start by enabling the Schedule Trigger node and configuring the execution frequency. 2. In the Config node, input channel handles as a comma-separated list and define the time range using days ago parameters. 3. Authenticate the YouTube API nodes with OAuth2 credentials. 4. Enable desired storage nodes: for CSV, verify the file path in Read/Write Files from Disk; for database, set up PostgreSQL connection in Insert or update rows in a table; for sheets, configure Google Sheets credentials. 5. Execute the workflow and check outputs for completeness, ensuring all videos within the time window are captured and stored correctly.

🛤️ The workflow includes conditional elements such as batch processing in the Loop Over Videos node, which processes 25 videos at a time to avoid API rate limits. Storage nodes are selectively enabled, allowing users to choose outputs without modifying the core logic. Error handling with retry mechanisms in API nodes ensures resilience against temporary failures, and the Merge node prioritizes the latest data to resolve clashes.

✅ Success is achieved when the workflow executes without errors, all specified channels are processed, video data is enriched with complete metadata, and outputs are saved to the configured destinations. Verify by checking that CSV files contain expected fields, database rows are inserted, or sheets are updated with accurate information, and that no videos are missing from the time range.

# Reference

🔧 The workflow comprises 24 nodes, including a Schedule Trigger, configuration nodes, YouTube API calls for data retrieval, data processing nodes (Code for transformation), and multiple storage options. Key technical aspects: uses YouTube Data API v3 for scraping, supports OAuth2 authentication, and includes error retry logic. Batch processing is implemented to manage large datasets efficiently.

| Input Parameter | Data Type | Description |
|-----------------|-----------|-------------|
| channel_handles | string | Comma-separated list of YouTube channel handles (e.g., @Blitz,@RealCivilEngineerGaming) |
| published_after_days_ago | integer | Number of days ago to start scraping videos from |
| published_before_days_ago | integer | Number of days ago to end scraping videos to |

| Output Field | Data Type | Description |
|--------------|-----------|-------------|
| id | string | Unique YouTube video identifier |
| title | string | Title of the video |
| published_at | string | Publication date and time |
| channel_title | string | Name of the YouTube channel |
| channel_id | string | Unique channel identifier |
| description | string | Video description text |
| tags | string | Combined tags as a string |
| thumbnail | string | URL to the video thumbnail |
| category | string | YouTube video category |
| duration_min | number | Video duration in minutes |
| privacy_status | string | Privacy setting of the video |
| view_count | number | Total view count |
| like_count | number | Total like count |
| comment_count | number | Total comment count |
| is_sponsored | boolean | Indicates if video contains sponsorships |
| video_url | string | Direct URL to the video |

📥 Inputs are provided via the Config node, including channel handles and time parameters. Outputs are generated after data processing and include comprehensive video metadata stored in formats like CSV, database tables, or spreadsheets. The workflow ensures data consistency by transforming fields, such as converting ISO duration to minutes and handling null values.

🔗 Core dependencies include YouTube OAuth2 API for video data retrieval. Optional dependencies: PostgreSQL for database storage, Google Sheets and Drive OAuth2 for cloud outputs, and GitHub API for file management. External services must be accessible, and credentials configured in n8n for seamless operation.

# Tutorial

📚 Begin by exploring the workflow structure in n8n, focusing on the trigger and configuration nodes. Practice by setting up a simple instance with one channel and a short time window. Progress to adding multiple channels and enabling different storage options to understand data flow and customization.

💡 Exercise 1: Modify the time window to scrape videos from the last 30 days and observe how data volume changes. Exercise 2: Add a new channel handle to the Config node and verify it is processed correctly. Exercise 3: Enable the Google Sheets storage node and map the output fields to a new sheet, then analyze the results for trends.