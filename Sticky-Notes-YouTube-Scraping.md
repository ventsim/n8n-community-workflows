## Yellow Sticky Note (Main Explanation)

**YouTube Channel Video Scraper**

This workflow automates the collection and analysis of video data from multiple YouTube channels. It systematically scrapes video metadata including titles, descriptions, engagement metrics, duration, and sponsorship information. The workflow supports configurable time windows, handles multiple channels simultaneously, and provides flexible data storage options including PostgreSQL, Google Sheets, and file exports.

**Key Features:**
- Multi-channel monitoring with configurable time ranges
- Comprehensive video metadata extraction
- Automated data processing and transformation
- Multiple storage destination options
- Scheduled execution for continuous monitoring

## White Sticky Notes (Node Explanations)

### Configuration Section
**Nodes: Schedule Trigger, Config1, Code4**
- **Schedule Trigger**: Sets execution frequency (daily, weekly, etc.)
- **Config1**: Central configuration node with days_from (time window) and channel_handles parameters
- **Code4**: Processes channel handles, ensures proper @ format and case consistency

### Channel ID Resolution
**Nodes: Get Channel Ids by handle1, Split Out11**
- **Get Channel Ids by handle1**: Uses YouTube API to convert channel handles to channel IDs
- **Split Out11**: Breaks down API response to extract individual channel IDs for processing

### Video Data Collection
**Nodes: Get many videos, Loop Over Items, Aggregate**
- **Get many videos**: Fetches video lists from YouTube API using channel IDs and date filters
- **Loop Over Items**: Processes videos in batches (25 items per batch) for API efficiency
- **Aggregate**: Collects video IDs from multiple batches for detailed data retrieval

### Detailed Video Information
**Nodes: HTTP Request3, Split Out4, Merge6**
- **HTTP Request3**: Fetches comprehensive video details using aggregated video IDs
- **Split Out4**: Separates individual video records from API response
- **Merge6**: Combines basic video info with detailed metadata using video ID matching

### Data Processing
**Node: Code**
- **Code**: Transforms raw YouTube API data into structured format
- Converts ISO duration to minutes
- Extracts and formats tags, thumbnails, statistics
- Handles optional fields like sponsorship information
- Creates clean, database-ready data structure

### Storage Options
**Nodes: Insert or update rows in a table, Append or update row in sheet, Convert to File, Read/Write Files from Disk, Upload file**
- **PostgreSQL**: Upserts video data into database table with proper schema
- **Google Sheets**: Appends or updates spreadsheet with video information
- **File Export**: Converts data to file format and saves locally
- **Google Drive**: Uploads processed data files to cloud storage

## Configuration Requirements

- **YouTube API Credentials**: OAuth2 setup with appropriate permissions
- **Channel Handles**: Comma-separated list of YouTube channel handles
- **Storage Credentials**: Database, Google Sheets, or file system access
- **Time Window**: Configure days_from parameter for historical data collection

## Technical Details

- **API Rate Limiting**: Uses batch processing to respect YouTube API limits
- **Data Transformation**: Converts YouTube-specific formats (ISO duration) to usable data
- **Error Handling**: Built-in handling for missing or optional fields
- **Scalability**: Supports multiple channels and configurable time ranges