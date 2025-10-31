# ProcessPDFInvoice
## Purpose
🎯 This workflow automates the extraction and storage of invoice data from PDF and image files in Google Drive, leveraging OCR and AI technologies to reduce manual data entry, minimize errors, and improve operational efficiency for repetitive financial tasks.
## Target audience
👥 The primary users are finance professionals, small business owners, accountants, and automation specialists who handle regular invoice processing and seek to integrate AI-driven data extraction into their workflows for better accuracy and time savings.

🧠 The workflow operates on a scheduled basis, scanning a structured Google Drive hierarchy (company → month folders) for invoice files. It uses conditional logic to filter relevant files, applies OCR for images and text extraction for PDFs, merges the data, and employs AI to parse structured information (e.g., invoice details) before storing it in Google Sheets. This end-to-end automation handles multiple batches of data with built-in error handling.

# How-to Guide

📝 To implement this workflow:
1. **Prepare APIs**: Secure API keys for OCR.SPACE and OpenAI/DeepSeek, and set up OAuth2 for Google Drive and Sheets in n8n.
2. **Set Up Folders**: In Google Drive, create a root 'Attachments' folder, add company subfolders, and within each, month-named subfolders (e.g., 'Company_A/January').
3. **Configure Spreadsheet**: Use the provided template spreadsheet ID or create a new sheet and note its ID for the workflow.
4. **Import and Adjust**: Import the workflow into n8n, update node credentials with your API keys and folder/spreadsheet IDs, and set the schedule trigger (e.g., daily at 9 AM).
5. **Validate**: Test with sample invoices in the folders; check the n8n execution log for errors and verify data in Sheets.

🔄 Key conditional flows include:
- **Month Filtering**: Only processes folders matching the current month; others are skipped.
- **File Type Routing**: Images are sent to OCR.SPACE, PDFs to text extraction; non-supported files are ignored.
- **Error Handling**: Retries failed HTTP requests, and AI extraction continues on error to prevent workflow stoppage.
- **Spreadsheet Creation**: Checks if a spreadsheet exists for the month; creates one if missing.

✅ Success is achieved when:
- Invoice data (e.g., invoice number, date, amount) is accurately populated in Google Sheets without duplicates.
- All supported files in the current month's folders are processed without errors in the n8n log.
- The workflow runs consistently on schedule, and data integrity is maintained.

# Reference

🔧 Technical details:
- **Trigger**: Schedule-based (cron expression)
- **APIs Used**: Google Drive v3, Google Sheets v4, OCR.SPACE, OpenAI/DeepSeek
- **File Support**: JPEG, PNG, PDF
- **Processing**: Batch loops for companies, months, and files
- **Error Handling**: Retry on fail for HTTP nodes, continue on error for AI extraction
- **Data Flow**: JSON-structured data between nodes

📊 Input and output parameters:

**Input Parameters**
| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| Schedule Interval | String | Cron expression for trigger timing (e.g., '0 9 * * *' for daily at 9 AM) |
| Google Drive Root Folder ID | String | ID of the 'Attachments' folder in Google Drive |
| OCR.SPACE API Key | String | API key for OCR service authentication |
| AI API Key | String | API key for OpenAI or DeepSeek API |
| Template Spreadsheet ID | String | ID of the Google Sheets template for data storage |

**Output Parameters**
| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| Invoice Number | String | Extracted invoice identifier from the file |
| Invoice Date | String | Extracted date of the invoice |
| Total Amount | Number | Extracted total monetary value from the invoice |
| Vendor Name | String | Extracted name of the vendor or supplier |
| File Name | String | Original name of the processed file |
| Processing Timestamp | String | Date and time when the data was stored in Sheets |

🔗 Dependencies include:
- **External Services**: Google Drive API, Google Sheets API, OCR.SPACE API, OpenAI/DeepSeek API
- **Internal n8n Nodes**: Schedule Trigger, Google Drive, Filter, Switch, HTTP Request, Extract from File, Information Extractor, Google Sheets, Set, Merge
- **Prerequisites**: Specific folder structure in Google Drive, valid API credentials, internet connectivity for n8n

# Tutorial

🧩 Start by understanding the folder hierarchy and API integrations. Progress to modifying data extraction fields and error handling. Advanced topics include scaling for multiple companies and integrating with accounting software.

💡 Practice exercises:
1. Modify the workflow to extract additional fields like tax amount or purchase order number.
2. Add a node to send a Slack notification when an invoice is processed.
3. Change the file type support to include Word documents by updating the filter and extraction logic.
4. Test error scenarios by uploading corrupted files and observing the workflow's response.