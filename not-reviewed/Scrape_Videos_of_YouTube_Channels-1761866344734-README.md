# Scrape Videos from YouTube Channels for Content Analysis

## Who Is This For?
This workflow is designed for content creators, digital marketers, social media managers, and data analysts who need to monitor and analyze YouTube channel performance. It's particularly useful for agencies managing multiple channels, competitive analysis teams, and content strategists tracking video performance metrics.

## What Does This Workflow Solve?
- 📊 **Automated video data collection** from multiple YouTube channels
- 🔍 **Comprehensive metadata extraction** including views, likes, duration, and sponsorship status
- ⏰ **Scheduled monitoring** with configurable time windows
- 📈 **Performance tracking** across multiple content creators
- 💰 **Sponsorship detection** to identify paid product placements
- 🗄️ **Flexible storage options** including databases, spreadsheets, and files

## Setup Guide
**Prerequisites:**
- YouTube API credentials with OAuth 2.0 authentication
- Configure channel handles in the "Config" node (e.g., "@Blitz,@RealCivilEngineerGaming")
- Set time window in days for video collection

**Step-by-Step Configuration:**
1. **Configure YouTube Credentials:** Set up YouTube OAuth 2.0 API credentials in all YouTube nodes
2. **Set Channel Parameters:** In the "Config" node, specify channel handles and days back to scrape
3. **Enable Storage Destinations:** Activate PostgreSQL, Google Sheets, or file export nodes as needed
4. **Schedule Execution:** Configure the Schedule Trigger for automated runs
5. **Test Workflow:** Execute once to verify data collection and storage

## Requirements
- **YouTube API Account** - [YouTube OAuth 2.0 credentials](https://docs.n8n.io/integrations/builtin/credentials/youtube/) with appropriate API permissions
- **PostgreSQL Database** (optional) - For structured data storage
- **Google Sheets** (optional) - For spreadsheet-based analysis
- **Google Drive** (optional) - For cloud file storage
- **Local File System** - For CSV export (enabled by default)

## How to Customize the Workflow
- **Add More Channels:** Modify the channel_handles parameter in the Config node
- **Adjust Time Window:** Change days_from value to collect videos from different time periods
- **Custom Data Processing:** Modify the Code node to add new calculated fields or transform existing data
- **Add Storage Options:** Enable additional output nodes for different database systems or cloud services
- **Filter Content:** Add conditional logic to exclude certain video types or categories
- **Enhance Analytics:** Integrate with data visualization tools using the exported data