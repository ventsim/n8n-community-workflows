=============== Yellow Note ===============

This template automates YouTube video data scraping for multiple channels. It collects video metadata within a configurable time window, enriches it with details like views and duration, and stores results in CSV, PostgreSQL, or Google Sheets. Ideal for content monitoring and performance analysis.

=============== White Notes ===============

**Data Collection Nodes**: Includes trigger, config, channel ID lookup, and video fetching. Handles input parameters and initial API calls to YouTube, with batching to manage rate limits.

**Processing & Storage Nodes**: Enriches video metadata, transforms data (e.g., duration to minutes), and outputs to multiple destinations. Storage nodes are disabled by default for flexible setup.