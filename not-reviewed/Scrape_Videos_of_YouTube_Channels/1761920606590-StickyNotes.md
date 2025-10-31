=============== Yellow Note ===============

📌 This template automates YouTube video scraping for content monitoring and performance analysis. It collects video data from specified channels within a customizable time window, enriches it with metadata like views and tags, and stores results in CSV, database, or sheets. Perfect for tracking channel growth and content trends without manual effort.

=============== White Notes ===============

🔍 Trigger & Configuration: Starts with a schedule-based trigger and configurable parameters for channel handles and time range. Ensures proper initialization and input validation for seamless execution.

🔄 Data Processing & Enrichment: Fetches channel IDs, retrieves videos in batches, enriches metadata via YouTube API, and transforms data (e.g., duration conversion). Includes error handling and retry logic for reliability.

💾 Storage & Outputs: Supports multiple destinations—CSV (default), PostgreSQL, Google Sheets, Google Drive. Users can enable selective storage based on needs, with data formatted for easy analysis.