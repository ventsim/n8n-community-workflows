# Scrape Videos of YouTube Channels for Content Analysis

## Who Is This For?

This workflow is designed for content creators, digital marketers, and data analysts who need to systematically monitor and analyze YouTube channel performance. It's particularly useful for tracking competitor channels, monitoring industry trends, or conducting content research across multiple YouTube channels.

## What Does This Workflow Solve?

- 📊 **Automated Video Data Collection** - Systematically scrapes video metadata from multiple YouTube channels
- 🔄 **Scheduled Monitoring** - Runs on a regular schedule to capture new content as it's published
- 📈 **Performance Analytics** - Gathers view counts, like counts, and engagement metrics for analysis
- ⏱️ **Duration Tracking** - Converts ISO duration formats to readable minutes for easy analysis
- 🏷️ **Content Categorization** - Captures tags, categories, and sponsorship information
- 💾 **Multiple Storage Options** - Supports PostgreSQL database, Google Sheets, and file exports

## Setup Guide

### Prerequisites
- YouTube API credentials with OAuth2 authentication
- Configure channels to monitor in the Config1 node
- Set up storage destination (PostgreSQL, Google Sheets, or local files)

### Configuration Steps
1. **Set Channel Handles**: Update the Config1 node with YouTube channel handles (e.g., @Blitz, @RealCivilEngineerGaming)
2. **Configure Time Range**: Set the number of days to look back for videos (default: 7 days)
3. **Choose Storage**: Enable your preferred storage node (PostgreSQL, Google Sheets, or file export)
4. **Set Schedule**: Configure the Schedule Trigger for automatic execution
5. **Test Execution**: Run the workflow to verify data collection and storage

## Requirements

- **YouTube API Access**: OAuth2 credentials with appropriate permissions
- **Storage Solution**: PostgreSQL database, Google Sheets account, or local file system access
- **n8n Credentials**: YouTube OAuth2, Google Sheets (optional), PostgreSQL (optional)

## How to Customize the Workflow

- **Add More Channels**: Extend the channel_handles list in Config1 node
- **Adjust Time Range**: Modify the days_from parameter to capture different time periods
- **Custom Data Fields**: Edit the Code node to include additional video metadata
- **Change Storage Format**: Enable/disable different storage nodes based on your needs
- **Add Notifications**: Integrate with email or messaging platforms for alerts
- **Filter Content**: Add conditions to exclude certain video types or categories