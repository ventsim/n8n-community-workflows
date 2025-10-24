# Extract Invoice Data from PDF and Images to Google Sheets

## Who Is This For?
This workflow is designed for small business owners, accountants, and finance teams who need to automate invoice processing. It's perfect for anyone who receives invoices in various formats (PDF and images) and wants to extract structured data automatically into a spreadsheet for accounting and record-keeping.

## What Does This Workflow Solve?
- 📄 **Automated Invoice Processing**: Automatically extracts data from PDF invoices and image files
- 🔍 **OCR Technology**: Uses OCR.Space API to read text from image-based invoices
- 📊 **Structured Data Export**: Organizes extracted invoice information into Google Sheets
- 🗂️ **Smart Folder Management**: Processes invoices organized by company and month folders
- 🤖 **AI-Powered Extraction**: Uses DeepSeek AI to intelligently parse invoice data
- 🔄 **Batch Processing**: Handles multiple invoices in a single automated run

## Setup Guide

### Prerequisites
1. Google Drive account with organized folder structure (company > month folders)
2. OCR.Space API key
3. DeepSeek AI API access
4. Google Sheets template for invoice data

### Step-by-Step Configuration
1. **Configure Google Drive Credentials**: Set up OAuth2 authentication for Google Drive and Google Sheets
2. **Set Up OCR.Space API**: Add your API key to the HTTP Request node
3. **Configure AI Model**: Set up DeepSeek AI credentials for intelligent data extraction
4. **Organize Your Folders**: Ensure invoices are in company/month folder structure
5. **Update Spreadsheet Template**: Modify the Google Sheets template to match your needs

## Requirements
- Google Drive account with folder access
- OCR.Space API account (free tier available)
- DeepSeek AI API access
- Google Sheets account
- Basic folder structure: Company folders containing month subfolders

## How to Customize the Workflow
- **Change Folder Structure**: Modify the folder ID in the "Get Company Folders" node
- **Add More Invoice Fields**: Update the Information Extractor schema to include additional fields
- **Modify Processing Logic**: Adjust the filter conditions for different file types or naming patterns
- **Integrate with Other Systems**: Add nodes to send processed data to accounting software or databases
- **Customize Schedule**: Modify the Schedule Trigger to run at your preferred frequency