=============== Yellow Note ===============

📌 This n8n template automates scraping video data from multiple YouTube channels. It collects videos within a customizable time window, enriches them with metadata like views and likes, and stores results in CSV, PostgreSQL, Google Sheets, or Drive. Ideal for content monitoring, performance analysis, and reporting. Save time on manual data collection and focus on insights! 🎥📈

=============== White Notes ===============

⚙️ Configuration and Trigger Group: Includes Schedule Trigger for initiation, Config node for parameters (channel handles, time range), and Format node to ensure proper handle formatting. This group sets the foundation for the workflow execution and user inputs.

🔄 Data Processing and Storage Group: Covers YouTube API nodes for fetching channel IDs and videos, Code node for data transformation (e.g., duration conversion), and storage nodes for outputs. Handles enrichment, batching, and multi-destination saving efficiently.