# Scrape YouTube Channel Videos for Content Analysis and Monitoring

## Who Is This For?
This workflow is designed for content creators, digital marketers, social media managers, and data analysts who need to systematically monitor and analyze YouTube channel performance. It's particularly valuable for agencies managing multiple client channels, content strategists tracking competitor activity, and researchers studying video content trends.

## What Does This Workflow Solve?
- 📊 **Automated Video Monitoring** - Continuously tracks new video uploads across multiple channels
- 🔍 **Comprehensive Metadata Collection** - Gathers views, likes, comments, duration, and sponsorship data
- ⏰ **Time-Based Filtering** - Focuses on videos published within specific date ranges
- 📈 **Performance Analysis** - Enables trend analysis and content strategy optimization
- 💰 **Sponsorship Detection** - Identifies paid product placements in videos
- 🗄️ **Multi-Format Storage** - Saves data to databases, spreadsheets, and files for flexible analysis

## Setup Guide
**Prerequisites:**
- YouTube API access with OAuth 2.0 credentials
- Configured storage destination (PostgreSQL, Google Sheets, or local files)

**Configuration Steps:**
1. **Set YouTube Credentials** - Configure YouTube OAuth 2.0 API credentials in the workflow
2. **Configure Channels** - Update the "Config" node with target YouTube channel handles (e.g., @Blitz, @RealCivilEngineerGaming)
3. **Set Time Window** - Adjust published_after_days_ago and published_before_days_ago parameters
4. **Enable Storage** - Activate your preferred storage destination nodes (PostgreSQL, Google Sheets, or file export)
5. **Schedule Execution** - Configure the Schedule Trigger for automated runs

## Requirements
- **YouTube API Account** - [YouTube OAuth 2.0 credentials](https://docs.n8n.io/integrations/builtin/credentials/youtube/) with appropriate API permissions
- **Storage Options** (choose one or more):
  - PostgreSQL database with table schema
  - Google Sheets with OAuth credentials
  - Local file system access
  - Google Drive for cloud storage

## How to Customize the Workflow
- **Add More Channels** - Modify the channel_handles parameter in the Config node
- **Adjust Time Range** - Change published_after_days_ago for different monitoring periods
- **Extract Additional Data** - Modify the Code node to include more YouTube API fields
- **Add Notifications** - Integrate with email or messaging platforms for alerts
- **Custom Storage** - Connect to alternative databases or cloud storage services
- **Filter Content** - Add conditional logic to exclude certain video types or categories