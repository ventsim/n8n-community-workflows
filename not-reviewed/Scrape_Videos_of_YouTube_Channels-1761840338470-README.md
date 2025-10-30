# Scrape YouTube Channel Videos for Content Analysis

## Who Is This For?
This workflow is designed for content creators, digital marketers, researchers, and data analysts who need to systematically monitor and analyze YouTube channel performance. It's particularly useful for agencies managing multiple channels, competitive analysis teams, and content strategists tracking video performance metrics.

## What Does This Workflow Solve?
- 📊 **Automated video data collection** from multiple YouTube channels
- 🔍 **Comprehensive metadata extraction** including views, likes, comments, and duration
- 🎯 **Sponsorship detection** to identify paid product placements
- 📈 **Performance tracking** with configurable time windows
- 💾 **Flexible data storage** options (PostgreSQL, Google Sheets, CSV files)
- ⏰ **Scheduled monitoring** for continuous data collection

## Setup Guide

**Prerequisites:**
- YouTube API credentials with OAuth 2.0 access
- Configured storage destination (PostgreSQL, Google Sheets, or local file system)

**Configuration Steps:**
1. Set up YouTube OAuth credentials in n8n
2. Configure channel handles in the "Config" node (e.g., @Blitz, @RealCivilEngineerGaming)
3. Set the time window for video collection (days_from parameter)
4. Enable your preferred storage destination (PostgreSQL, Google Sheets, or file export)
5. Configure the schedule trigger for automated execution

## Requirements
- YouTube API access with appropriate permissions
- PostgreSQL database (optional)
- Google Sheets account (optional)
- Google Drive account (optional)
- n8n instance with internet connectivity

## How to Customize the Workflow
- **Add more channels** by updating the channel_handles parameter
- **Adjust time range** by modifying days_from value
- **Extract additional metrics** by enhancing the Code node
- **Change storage destinations** by enabling/disabling output nodes
- **Modify scheduling** frequency in the Schedule Trigger node
- **Add data transformations** in the processing pipeline for custom analytics