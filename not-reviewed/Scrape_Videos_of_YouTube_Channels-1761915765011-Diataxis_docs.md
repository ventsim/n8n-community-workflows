# Explanation

## Purpose
This workflow automates the extraction and enrichment of YouTube video data to support content monitoring, performance analysis, and reporting. It reduces manual effort by systematically collecting metadata such as view counts, durations, and engagement metrics across multiple channels.

## Target Audience
Content strategists, marketing analysts, and data engineers who require automated, scalable solutions for tracking YouTube channel performance. Users should have basic familiarity with n8n and API integrations.

## Conceptual Overview
The workflow initiates on a schedule, processes channel handles to retrieve IDs, fetches videos within a time frame, and enriches data through YouTube API calls. It employs batching to manage API limits, merges metadata, and outputs to multiple storage options. Key concepts include data aggregation, transformation, and conditional storage routing.

# How-to Guide

## Step-by-Step
1. **Configure Trigger**: Set the Schedule Trigger node to run at desired intervals (e.g., daily).
2. **Input Parameters**: In the Config node, specify channel handles as a CSV list and define time ranges (e.g., published_after_days_ago: 1).
3. **Authenticate APIs**: Add YouTube OAuth2 credentials to nodes requiring API access.
4. **Enable Storage**: Activate PostgreSQL, Google Sheets, or CSV nodes based on your output needs.
5. **Execute and Monitor**: Run the workflow, check execution logs for errors, and verify output files or databases.

## Conditional Paths
- Storage nodes are disabled by default; enable PostgreSQL for database storage, Google Sheets for spreadsheet updates, or rely on CSV for local files.
- The workflow handles API rate limits via batching; adjust the Loop Over Videos node if quotas change.
- Error retry logic is built into key API nodes to handle temporary failures automatically.

## Success Criteria
- Workflow executes without errors in n8n logs.
- CSV files are generated with video data, including all enriched fields.
- If enabled, data appears in PostgreSQL or Google Sheets as expected.
- Video counts match expected ranges based on the time window and channels.

# Reference

## Technical Specifications
- **APIs Used**: YouTube Data API v3 for channel and video metadata; Google Sheets, Drive, and PostgreSQL APIs for storage.
- **Input Parameters**: channel_handles (CSV), published_after_days_ago (integer), published_before_days_ago (integer).
- **Output Fields**: id, title, published_at, channel_title, duration_min, view_count, like_count, video_url, etc.
- **Execution**: Scheduled, with configurable intervals; batch processing of 25 videos per API call.

## Input/Output
- **Input**: Channel handles (e.g., @Blitz), time window parameters.
- **Output**: Structured data in CSV, PostgreSQL, or Google Sheets, including video IDs, metadata, and derived metrics like duration in minutes.
- **Data Flow**: Raw video lists → enriched metadata → transformed data → multi-format storage.

## Dependencies
- **Credentials**: YouTube OAuth2, PostgreSQL, Google Sheets, Google Drive (optional).
- **External Services**: YouTube API, Google APIs, PostgreSQL database.
- **n8n Nodes**: Schedule Trigger, HTTP Request equivalents for APIs, data processing nodes.

# Tutorial

## Learning Path
Start by understanding the basic workflow structure, then explore API integrations. Practice modifying the Config node to change channels and time windows. Advance by enabling storage nodes and analyzing output data for insights into video performance trends.

## Practice Exercises
1. Add a new YouTube channel handle to the Config node and run the workflow to see updated data.
2. Enable the Google Sheets node and map output fields to a new spreadsheet.
3. Modify the Code node to add a custom field, such as calculating engagement rate from likes and views.
4. Test error handling by temporarily invalidating API credentials and observing retry behavior.