## 📋 Sticky Notes: YouTube Video Scraper

### 🟡 YELLOW NOTE: Complete Workflow Overview
This workflow automatically scrapes video data from multiple YouTube channels, processes the metadata, and stores it in your preferred destination. It fetches channel IDs from handles, retrieves videos published within a custom date range, enriches data with detailed statistics, and outputs to database, file, or cloud storage. Perfect for content analysis and competitive monitoring.

### ⚪ WHITE NOTE: Channel Configuration
**Purpose:** Sets up workflow parameters including channel handles and date range  
**Configuration:** Edit `channel_handles` field with comma-separated YouTube handles (with or without @) and adjust `days_from` to control how far back to search

### ⚪ WHITE NOTE: Channel ID Resolution  
**Purpose:** Converts YouTube channel handles to channel IDs using YouTube API  
**Configuration:** Requires YouTube OAuth credentials, automatically processes multiple channels in sequence

### ⚪ WHITE NOTE: Video Data Collection
**Purpose:** Fetches all videos from specified channels within date range  
**Configuration:** Uses YouTube API to get video metadata, processes in batches for efficiency

### ⚪ WHITE NOTE: Data Enrichment & Processing
**Purpose:** Combines and enriches video data with detailed statistics and content details  
**Configuration:** Merges basic video info with detailed metadata, converts duration formats, and prepares for storage

### ⚪ WHITE NOTE: Storage Options
**Purpose:** Stores processed video data in selected destinations  
**Configuration:** Choose between PostgreSQL database, local files, Google Sheets, or Google Drive - enable desired nodes