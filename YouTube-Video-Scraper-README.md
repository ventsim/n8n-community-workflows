# Scrape Videos from YouTube Channels to Database

## Who Is This For? 
📊 **Content analysts** tracking competitor channels  
🎬 **Marketing teams** monitoring brand mentions  
📈 **Researchers** analyzing video performance trends

## What This Solves
- **Automates** video data collection from multiple channels
- **Tracks** new uploads within custom date ranges  
- **Stores** comprehensive metadata (views, likes, duration, etc.)
- **Eliminates** manual YouTube API queries

## Quick Start
1. **Configure** channel handles in the "Config1" node
2. **Set up** YouTube OAuth credentials  
3. **Enable** database or file storage nodes
4. **Activate** workflow and run manually or on schedule

## Requirements
🔑 **YouTube OAuth2 API** (Get many videos, HTTP Request3, Get Channel Ids by handle1 nodes)  
🗄️ **PostgreSQL** (Insert or update rows in a table node) - *optional*  
📁 **Google Drive** (Upload file node) - *optional*  
📊 **Google Sheets** (Append or update row in sheet node) - *optional*

## Basic Customization  
- **Adjust** date range in "Config1" node (default: 7 days)
- **Add/remove** channels in the channel_handles field
- **Choose** storage destination (database, file, or both)

🚀 Happy automating! Start tracking your favorite YouTube channels effortlessly!