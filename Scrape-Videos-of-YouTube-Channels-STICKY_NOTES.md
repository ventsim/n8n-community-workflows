## YELLOW NOTE: Complete Workflow Overview
This workflow automatically scrapes video data from multiple YouTube channels and stores it in your preferred destination. It handles channel lookup by handle, fetches recent videos, processes detailed video metadata, and outputs to Google Sheets, PostgreSQL, or files. Perfect for content analytics and competitor monitoring without manual data collection.

## WHITE NOTE: Configuration Setup
Set your target YouTube channel handles and timeframe in the Config1 node. Use comma-separated channel handles (with or without @ symbol) and specify how many days back to look for videos. This centralizes all user-configurable settings.

## WHITE NOTE: Channel ID Resolution
The workflow first converts channel handles to channel IDs using YouTube API calls. This ensures accurate channel identification regardless of handle format and prepares for subsequent video data collection.

## WHITE NOTE: Video Data Collection
Fetches all videos from target channels within the specified timeframe. Uses batch processing to handle large datasets efficiently and ensures complete data retrieval from YouTube's API.

## WHITE NOTE: Video Metadata Enrichment
Makes additional API calls to get detailed video statistics, content details, and metadata. Combines basic video information with rich analytics like view counts, likes, comments, and duration.

## WHITE NOTE: Data Processing & Output
Transforms raw YouTube API data into clean, structured format. Converts ISO duration to minutes, handles optional fields, and prepares data for storage in Google Sheets, PostgreSQL, or file export.