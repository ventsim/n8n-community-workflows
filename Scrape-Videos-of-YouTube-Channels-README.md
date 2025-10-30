# Scrape Videos from YouTube Channels

## Who Is This For?
- Content creators tracking their video performance
- Marketing teams monitoring competitor channels
- Researchers analyzing YouTube content trends

## What This Solves
- Automates video data collection from multiple channels
- Eliminates manual YouTube API calls and data processing
- Provides structured video analytics in Google Sheets or databases
- Tracks new videos published within customizable timeframes

## Quick Start
1. Configure YouTube OAuth credentials
2. Set target channel handles in Config1 node
3. Choose output destination (Google Sheets or PostgreSQL)

## Requirements
- YouTube OAuth2 API credentials
- Google Sheets or PostgreSQL database (optional)
- Google Drive account (optional for file export)

## Basic Customization
- Adjust days_from in Config1 to change timeframe
- Modify channel_handles to add/remove channels
- Choose between database, spreadsheet, or file output