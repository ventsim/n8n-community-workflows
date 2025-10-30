 Yellow Note:
 **YouTube Channel Video Scraper**

**Purpose:** Automates collection and analysis of video data from multiple YouTube channels for content monitoring and performance tracking.

**Workflow Description:**
1. Starts with scheduled trigger for automated execution
2. Configures channel handles and time window parameters
3. Fetches channel IDs using YouTube API
4. Retrieves videos published within specified timeframe
5. Enriches video data with detailed metadata (views, likes, duration, sponsorship)
6. Processes and transforms data for storage
7. Outputs to multiple destinations (PostgreSQL, Google Sheets, CSV files)

**Key Features:**
- Multi-channel monitoring with configurable time ranges
- Comprehensive video metadata extraction
- Sponsorship detection capabilities
- Flexible storage options
- Automated scheduled execution

White Note:
 **Configuration & Channel Setup**

**Purpose:** Sets up workflow parameters and prepares channel data for API calls

**Configuration Requirements:**
- _channel_handles_: CSV list of YouTube channel handles (e.g: @Blitz, @RealCivilEngineerGaming)
- _days_from_: Days back in the past from now window to scrape for (default: 1 day)

**Nodes:** Set, Format Channel Handles

White Note:
 **YouTube API Integration**

**Purpose:** Efficiently fetches channel information and video data from YouTube API

**Configuration Requirements:**
- YouTube OAuth 2.0 credentials with appropriate API permissions
- Valid YouTube API access
- Available YouTube API Access quota

**Nodes:** Get Channel Ids by handles, Get Channels Videos, Enrich Additional Video Metadata

White Note:
 **Data Processing**

**Purpose:** Processes and transforms raw YouTube API data into structured format

**Key Functions:**
- Converts ISO duration to minutes
- Cleans and structures data for storage
- Allows for flexible mapping modifications

**Nodes:** Split Out Channels, Split Out Videos, Aggregate, Merge, Code

White Note:
 **Storage & Output Options**

**Purpose:** Allows storage of scraped and processed data in multiple destinations

**Configuration Requirements:**
- **File Export:** Local file system access
- **PostgreSQL:** Database credentials and table schema
- **Google Sheets:** OAuth credentials and sheet ID
- **Google Drive:** OAuth credentials for cloud storage

**Nodes:** Insert or update rows in a table, Append or update row in sheet, Convert to File, Read/Write Files from Disk, Upload file