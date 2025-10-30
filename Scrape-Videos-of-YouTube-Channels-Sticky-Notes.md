## Yellow Sticky Note - Main Explanation

**Template Purpose:** This workflow automates the collection and analysis of YouTube video data from multiple channels. It systematically scrapes video metadata, engagement metrics, and content details for competitive analysis, trend monitoring, and content strategy development.

**Workflow Description:** The workflow starts by processing a list of YouTube channel handles, converts them to proper format, then queries the YouTube API to get channel IDs. It then retrieves videos published within a specified time range, gathers detailed video metadata through additional API calls, processes and cleans the data, and stores it in your preferred destination (PostgreSQL, Google Sheets, or local files).

**Key Features:**
- Multi-channel video data collection
- Scheduled automated execution
- Comprehensive video metadata extraction
- Multiple storage options
- Data cleaning and transformation
- Batch processing for efficiency

## White Sticky Notes - Node Explanations

### Schedule Trigger & Config1
**Purpose:** Sets up the workflow execution schedule and configuration parameters
**Configuration:** Define channel handles (e.g., @Blitz, @RealCivilEngineerGaming) and days to look back for videos

### Channel Processing Nodes (Code4, Get Channel IDs, Split Out11)
**Purpose:** Processes channel handles and retrieves channel IDs from YouTube API
**Requirements:** YouTube OAuth2 credentials, valid channel handles

### Video Collection Nodes (Get Many Videos, Loop Over Items)
**Purpose:** Retrieves videos from channels within specified time range
**Configuration:** Batch size (25), time range filtering, channel ID mapping

### Detailed Video Data (Aggregate, HTTP Request3, Split Out4)
**Purpose:** Fetches comprehensive video metadata including statistics, content details, and status
**Requirements:** YouTube API access for detailed video information

### Data Processing (Merge6, Code)
**Purpose:** Combines video data and transforms it into clean, structured format
**Features:** Duration conversion, data normalization, field mapping

### Storage Options (PostgreSQL, Google Sheets, File Export)
**Purpose:** Stores processed video data in selected destination
**Configuration:** Database connection, sheet selection, or file path setup

**Note:** Enable only one storage node based on your preference and disable the others