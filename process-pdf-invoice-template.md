# Extract invoice data from PDFs and images to Google Sheets automatically

## Who Is This For?

This workflow is designed for businesses, freelancers, and accounting teams who need to automate invoice processing. It's perfect for those who receive invoices in various formats (PDFs and images) via Google Drive and want to automatically extract key information into organized spreadsheets. Whether you're managing dozens or hundreds of invoices monthly, this template eliminates manual data entry and reduces processing time from hours to minutes.

## What Does This Workflow Solve?

- 📄 **Automated Data Extraction**: Processes both PDF invoices and image-based invoices (JPG, PNG, etc.) using OCR technology
- 📊 **Organized Record Keeping**: Automatically creates monthly spreadsheets in Google Sheets with extracted invoice data
- 🗂️ **Smart File Organization**: Processes invoices from company-specific folders and maintains organized monthly records
- ⚡ **Time Savings**: Eliminates manual invoice data entry, reducing processing time by 90%
- 🔍 **Accurate Information Capture**: Extracts key fields like invoice numbers, dates, amounts, tax details, and vendor information
- 🔄 **Batch Processing**: Handles multiple invoices simultaneously with intelligent looping mechanisms

## Setup Guide

### Prerequisites
1. Active Google Workspace account with Drive and Sheets access
2. OCR.space API key (free tier available)
3. OpenAI-compatible API for data extraction (supports DeepSeek or similar)
4. n8n instance with Google OAuth2 configured

### Step-by-Step Configuration

1. **Google Drive Structure Setup**:
   - Create an "Attachments" folder in your Google Drive
   - Inside, create company-specific folders (e.g., "Company A", "Company B")
   - Within each company folder, create monthly subfolders using format "YYYY/MM" (e.g., "2024/11")
   - Place invoice files (PDFs or images) in the appropriate monthly folders

2. **Template Spreadsheet Creation**:
   - Create a Google Sheets template with columns: invoice_number, issue_date, due_date, currency, total, subtotal, tax_rate, tax_amount, amount_due, buyer_email, buyer_country, seller_name, seller_email, line_item_description, document_file
   - Note the spreadsheet ID for configuration

3. **API Configuration**:
   - Obtain OCR.space API key from [ocr.space](https://ocr.space/ocrapi)
   - Configure OpenAI-compatible API credentials (DeepSeek recommended for cost-effectiveness)

4. **Workflow Configuration**:
   - Update the Attachments folder ID in the "Get Company Folders" node
   - Replace the template spreadsheet ID in the "Google Drive1" node
   - Update the OCR.space API key in the "HTTP Request" node
   - Configure the Schedule Trigger for your preferred frequency

5. **Testing**:
   - Place a sample invoice in a monthly folder
   - Execute the workflow manually
   - Verify the extracted data appears in the corresponding Google Sheet

## Requirements

- **Google Drive OAuth2**: Read/write access to Drive folders and files
- **Google Sheets OAuth2**: Create and update spreadsheet permissions
- **OCR.space API Key**: For optical character recognition of image files
- **OpenAI-compatible API**: For intelligent data extraction (DeepSeek, OpenAI, or similar)
- **n8n Version**: 1.0.0 or higher with LangChain nodes support

## How to Customize the Workflow

### Modify Extraction Fields
Edit the JSON schema in the "Information Extractor1" node to add or remove invoice fields based on your requirements. The current schema includes standard invoice fields but can be extended for industry-specific needs.

### Adjust Folder Structure
Change the folder hierarchy by modifying the "Get Company Folders" and "Get All Company Month Folders" nodes. You can implement different organizational structures like department-based or project-based folders.

### Processing Frequency
Adjust the Schedule Trigger to run hourly, daily, or weekly based on your invoice volume. For real-time processing, consider replacing with a Google Drive Trigger node.

### Enhanced Error Handling
Add Error Trigger nodes and notification systems (email, Slack) to alert when invoice processing fails or when unusual patterns are detected.

### Multi-language Support
Configure the AI model prompts in different languages to process international invoices by modifying the system prompt in the Information Extractor node.