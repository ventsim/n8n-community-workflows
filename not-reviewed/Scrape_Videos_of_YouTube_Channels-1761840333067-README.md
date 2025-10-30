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

**Nodes:** Config, Format Channel Handles

**Purpose:** Sets up workflow parameters and prepares channel data for API calls

**Configuration Requirements:**
- Set channel_handles parameter with YouTube channel handles (e.g., @Blitz, @RealCivilEngineerGaming)
- Configure days_from parameter for time window (default: 1 day)
- Handles formatting and validation of channel handles

White Note:
 **YouTube API Integration**

**Nodes:** Get Channel Ids by handles, Get Channels Videos, Enrich Additional Video Metadata

**Purpose:** Fetches channel information and video data from YouTube API

**Configuration Requirements:**
- YouTube OAuth 2.0 credentials with appropriate API permissions
- Valid YouTube API access
- Proper authentication setup in n8n

White Note:
 **Data Processing Pipeline**

**Nodes:** Split Out Channels, Loop Over Videos, Aggregate, Split Out Videos, Merge, Code

**Purpose:** Processes and transforms raw YouTube API data into structured format

**Key Functions:**
- Splits channel and video data into individual items
- Batches video processing for API efficiency
- Aggregates video IDs for bulk metadata requests
- Converts ISO duration to minutes
- Cleans and structures data for storage

White Note:
 **Storage & Output Options**

**Nodes:** Insert or update rows in a table, Append or update row in sheet, Convert to File, Read/Write Files from Disk, Upload file

**Purpose:** Stores processed data in multiple destinations

**Configuration Requirements:**
- **PostgreSQL:** Database credentials and table schema
- **Google Sheets:** OAuth credentials and sheet ID
- **File Export:** Local file system access
- **Google Drive:** OAuth credentials for cloud storage

**Note:** Enable only the storage destinations you need