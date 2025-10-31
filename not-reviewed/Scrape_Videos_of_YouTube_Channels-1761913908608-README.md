## Who's it for
This template is designed for content managers, digital marketers, and data analysts who need to automate the collection and monitoring of YouTube video performance metrics. It's ideal for teams tracking multiple channels for competitive analysis, content strategy optimization, or reporting purposes.

## How it works
This workflow uses a scheduled trigger to periodically scrape video data from specified YouTube channels. It processes channel handles, fetches video lists within a configurable time window, enriches data with detailed metadata like views and likes, and stores results in CSV, PostgreSQL, or Google Sheets. Data is transformed for consistency, including duration conversion to minutes and URL generation.

## Requirements
- YouTube OAuth2 API credentials with sufficient quota for API calls.
- Optional: PostgreSQL database, Google Sheets, or Google Drive credentials for storage.
- Valid YouTube channel handles in CSV format.
- n8n instance with internet access for API calls.

## How to set up
1. Import the workflow into n8n.
2. Configure the Schedule Trigger node with your desired execution interval.
3. Set up credentials: YouTube OAuth2 API for video data access, and optionally PostgreSQL, Google Sheets, or Google Drive for storage.
4. In the Config node, input channel handles (e.g., @Blitz) and adjust time parameters (published_after_days_ago, published_before_days_ago).
5. Enable storage nodes as needed: CSV is active by default; enable PostgreSQL or Google Sheets nodes if required.
6. Test the workflow with a small dataset to verify data flow and outputs.

## How to customize the workflow
- Modify the time window in the Config node to scrape videos from different periods.
- Add or remove channel handles in the input list.
- Enable disabled storage nodes (PostgreSQL, Google Sheets, Google Drive) by toggling their active status.
- Adjust batch size in the Loop Over Videos node to optimize API usage.
- Extend the Code node to add custom data transformations or filters based on specific metrics.