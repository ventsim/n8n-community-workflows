🎯 This template is designed for content managers, digital marketers, and data analysts who need to automate the monitoring and analysis of YouTube channel performance. It helps users track video metrics, content trends, and engagement data across multiple channels without manual intervention.

⚙️ The workflow starts with a schedule trigger to initiate execution. It processes a list of YouTube channel handles, fetches their channel IDs using the YouTube API, retrieves videos published within a specified time window, enriches each video with detailed metadata (like view counts and tags), transforms the data for consistency, and stores it in multiple destinations including CSV files, PostgreSQL databases, and Google Sheets.

🔑 Required credentials and accounts:
- **YouTube OAuth2 API**: For fetching channel IDs, videos, and metadata.
- **Optional Storage Credentials**:
  - PostgreSQL database credentials
  - Google Sheets OAuth2 API
  - Google Drive OAuth2 API
- Ensure sufficient YouTube API quota to avoid rate limits.

🔧 Follow these steps to set up the workflow:
1. **Configure the Schedule Trigger**: Set your desired execution interval (e.g., daily or weekly).
2. **Adjust Parameters**: In the Config node, specify:
   - `channel_handles` as a CSV list (e.g., `@Blitz,@RealCivilEngineerGaming`)
   - `published_after_days_ago` and `published_before_days_ago` to define the time window
3. **Set Up Credentials**: Ensure YouTube OAuth2 API credentials are configured for API nodes.
4. **Enable Storage**: Activate desired storage nodes (CSV is enabled by default; others like PostgreSQL or Google Sheets can be enabled as needed).
5. **Test Execution**: Run the workflow to verify data is scraped and stored correctly.

🎨 Customization options:
- **Time Window**: Modify `published_after_days_ago` and `published_before_days_ago` to scrape different date ranges.
- **Channel List**: Add or remove channel handles in the Config node.
- **Storage Destinations**: Enable/disable PostgreSQL, Google Sheets, or Google Drive nodes based on your needs.
- **Data Fields**: Adjust the Code node to include or exclude specific video metadata fields.
- **Batch Size**: Change the batch size in the Loop Over Videos node to optimize API usage.