## YELLOW NOTE: Complete Workflow Overview
This workflow automatically scrapes video data from multiple YouTube channels, processes the metadata, and stores it in your preferred destination. It collects video titles, statistics, duration, and sponsorship information from specified channels within a configurable time period. Perfect for content analysis, competitor monitoring, and performance tracking across multiple YouTube accounts.

## WHITE NOTES: Node Group Configuration

**Channel Configuration & Scheduling**
- Schedule Trigger: Sets workflow execution frequency
- Config1: Define days to look back and channel handles
- Code4: Processes channel handles to ensure proper @ format

**Channel ID Resolution**
- Get Channel Ids by handle1: Converts channel handles to YouTube IDs
- Split Out11: Separates channel data for individual processing

**Video Data Collection**
- Get many videos: Fetches recent videos from each channel
- Loop Over Items: Processes channels in batches for efficiency
- Aggregate: Groups video IDs for batch API calls

**Video Metadata Enrichment**
- HTTP Request3: Gets detailed video statistics and content details
- Split Out4: Separates enriched video data
- Merge6: Combines basic video info with detailed metadata

**Data Processing & Output**
- Code: Cleans and transforms data, converts duration formats
- Output Nodes: Choose between PostgreSQL, Google Sheets, or file export