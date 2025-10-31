# Explanation

This workflow automates the collection, enrichment, and storage of video data from multiple YouTube channels. It is designed to support content monitoring, performance tracking, and data analysis by systematically scraping video metadata within configurable time windows and persisting it in structured formats for further use.

The primary users are content strategists, social media managers, data analysts, and digital marketers who require automated, scalable solutions for tracking YouTube channel performance. It is suitable for individuals or teams managing multiple channels and needing consistent data for reporting or insights.

The workflow operates through a sequential process: it initiates on a scheduled basis, processes input parameters to identify YouTube channels, retrieves channel IDs, fetches videos published within a defined time range, enriches each video with additional metadata such as view counts and tags, transforms the data into a standardized format, and stores it in one or more output destinations. This enables efficient data aggregation and reduces manual effort in content analysis.

# How-to Guide

To implement this workflow:
1. **Activate the Schedule Trigger**: Configure the trigger node to define how often the workflow runs (e.g., every 24 hours).
2. **Set Configuration Parameters**: In the Config node, input the channel handles as a comma-separated list and specify the time window using `published_after_days_ago` and `published_before_days_ago`.
3. **Configure Credentials**: Set up YouTube OAuth2 API credentials in the relevant nodes (Get Channel Ids by handles, Get Channels Videos, Enrich Additional Video Metadata).
4. **Enable Storage Nodes**: By default, CSV storage is active; enable PostgreSQL, Google Sheets, or Google Drive nodes by providing respective credentials and adjusting settings.
5. **Execute and Validate**: Run the workflow and check output destinations to ensure data is captured accurately without errors.

The workflow includes conditional execution paths primarily through enabled/disabled storage nodes. Users can selectively activate PostgreSQL, Google Sheets, or Google Drive nodes based on their data persistence requirements. The batch processing in the Loop Over Videos node handles large datasets efficiently, and error retry mechanisms in API nodes ensure robustness against transient failures.

Successful execution is indicated by:
- Completion of all nodes without errors.
- Video data from specified channels within the time window is fully captured and enriched.
- Data is stored in the enabled destinations (e.g., CSV file generated, database updated).
- All output fields (e.g., view_count, duration_min) are populated correctly for analysis.

# Reference

The workflow comprises 24 nodes, including a Schedule Trigger, configuration nodes, YouTube API integration nodes for data retrieval and enrichment, data transformation nodes, and multiple storage nodes. Key technical components include batch processing (25 items per batch) to manage API limits, data merging for enrichment, and output formatting for consistency. APIs utilized: YouTube Data API v3, Google Sheets API, Google Drive API, and PostgreSQL.

| Input/Output        | Data Type | Description                                                                 |
|---------------------|-----------|-----------------------------------------------------------------------------|
| channel_handles     | string    | Comma-separated list of YouTube channel handles (e.g., @Blitz,@ChannelName) |
| published_after_days_ago | number | Days before current date to start scraping videos (default: 1)              |
| published_before_days_ago | number | Days before current date to end scraping videos (default: 0)                |
| id                  | string    | Unique YouTube video identifier                                             |
| title               | string    | Title of the video                                                          |
| published_at        | string    | Publication date and time in ISO format                                     |
| channel_title       | string    | Name of the YouTube channel                                                 |
| duration_min        | number    | Video duration converted to minutes                                         |
| view_count          | number    | Total number of views                                                       |
| like_count          | number    | Total number of likes                                                       |
| comment_count       | number    | Total number of comments                                                    |
| video_url           | string    | Direct URL to the video on YouTube                                          |

Credential dependencies include YouTube OAuth2 API for video data retrieval, and optional credentials for PostgreSQL, Google Sheets OAuth2 API, and Google Drive OAuth2 API if storage nodes are enabled. External API dependencies are YouTube Data API v3 (for channel and video metadata), Google APIs (for Sheets and Drive), and PostgreSQL for database operations. Ensure all APIs have sufficient quotas and access permissions.

# Tutorial

Begin by setting up the workflow with basic CSV output to understand the data flow. Then, experiment with enabling additional storage options like PostgreSQL or Google Sheets. Finally, customize the time parameters and channel list to adapt the workflow for specific monitoring needs, such as tracking weekly content updates or comparing multiple channels.

1. Modify the time window: Change `published_after_days_ago` to 7 and `published_before_days_ago` to 0 to scrape videos from the past week. Observe how the data volume changes.
2. Add a new channel: Include an additional channel handle in the Config node and verify that videos from this channel are captured in the output.
3. Enable Google Sheets storage: Configure the Google Sheets node and run the workflow to append data to a sheet, ensuring all fields are mapped correctly.