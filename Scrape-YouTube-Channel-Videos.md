# Scrape Videos from YouTube Channels for Content Analysis

## Who Is This For?

This workflow is designed for content creators, marketers, researchers, and data analysts who need to systematically monitor and analyze YouTube channel content. It's perfect for tracking competitor channels, monitoring industry trends, or building datasets for content strategy analysis.

## What Does This Workflow Solve?

- 📊 **Automated Video Data Collection**: Automatically scrapes video metadata from multiple YouTube channels on a scheduled basis
- 🔄 **Historical Data Tracking**: Captures videos published within a configurable time window (default: 7 days)
- 📈 **Performance Analytics**: Gathers view counts, like counts, comment counts, and engagement metrics
- ⏱️ **Content Duration Analysis**: Converts YouTube's ISO duration format to readable minutes
- 🏷️ **Content Categorization**: Extracts tags, categories, and sponsorship information
- 💾 **Flexible Data Storage**: Supports multiple output options including PostgreSQL, Google Sheets, and local file exports

## Setup Guide

### Prerequisites
1. YouTube API credentials (OAuth2)
2. Choose one or more storage options:
   - PostgreSQL database (recommended)
   - Google Sheets
   - Local file system
   - Google Drive

### Configuration Steps
1. **Set up YouTube API credentials** in n8n credentials
2. **Configure channel handles** in the "Config1" node (comma-separated list)
3. **Adjust time window** in "Config1" node (days_from parameter)
4. **Enable desired storage nodes** (PostgreSQL, Google Sheets, or file export)
5. **Configure schedule trigger** for automated execution

### Storage Setup
- **PostgreSQL**: Configure table schema and connection
- **Google Sheets**: Set up document ID and sheet name
- **File Export**: Configure output directory and file format

## Requirements

- **YouTube API Access**: OAuth2 credentials with appropriate permissions
- **Storage Solution**: PostgreSQL database, Google Sheets, or local file system
- **n8n Instance**: Self-hosted or cloud version
- **Channel Handles**: List of YouTube channel handles to monitor

## How to Customize the Workflow

- **Add More Channels**: Update the channel_handles parameter in Config1 node
- **Adjust Time Range**: Modify days_from parameter to capture different time periods
- **Custom Data Fields**: Edit the Code node to extract additional video metadata
- **Change Storage**: Enable/disable different storage nodes based on your needs
- **Add Notifications**: Integrate with email or messaging platforms for alerts
- **Filter Content**: Add conditional logic to exclude certain video types or categories