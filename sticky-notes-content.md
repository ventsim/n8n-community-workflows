## Yellow Sticky Note - Main Workflow Overview

**Template Purpose**: Automatically extract structured data from PDF and image invoices stored in Google Drive, then populate organized Google Sheets with the extracted information.

**Complete Workflow Description**:
This workflow scans designated Google Drive folders for new invoices, processes them using OCR and AI extraction, and stores the structured data in monthly spreadsheets. It handles both PDF files (direct text extraction) and image files (OCR processing) through parallel processing paths. The system automatically creates missing spreadsheets and maintains organized records by company and month.

**Key Features & Benefits**:
- Dual processing paths for PDFs and images
- Automatic spreadsheet creation and management
- Company and month-based organization
- AI-powered intelligent data extraction
- Batch processing for multiple invoices
- Error handling and retry mechanisms

---

## White Sticky Notes - Node Group Explanations

### Folder Discovery & Organization
**Nodes**: Schedule Trigger, Get Company Folders, Get All Company Month Folders, Keep Only This Month
**Function**: Scans the main "Attachments" folder for company subfolders, then identifies current month folders within each company. Filters to process only the current month's invoices to maintain chronological organization.
**Configuration**: Requires Google Drive OAuth2 credentials and the main Attachments folder ID.
**Technical Details**: Uses date-based filtering to ensure only relevant monthly folders are processed.

### Spreadsheet Management
**Nodes**: Loop Over Items3, Find Spreadsheet, If, Google Drive1, Edit Fields2/4
**Function**: Searches for existing spreadsheets in each month folder. If none exists, creates a new spreadsheet from a template. Passes spreadsheet metadata through the workflow for data insertion.
**Configuration**: Requires template spreadsheet ID and Google Drive/Sheets permissions.
**Troubleshooting**: Ensure template spreadsheet is accessible and has proper sharing permissions.

### File Processing & Classification
**Nodes**: Get All Files, Keep Only Images And PDF, Switch1, Edit Fields3
**Function**: Retrieves all files from monthly folders, filters to include only PDFs and images, then routes files to appropriate processing paths based on file type.
**Configuration**: No additional setup required beyond initial folder structure.
**Technical Details**: Uses MIME type detection to classify files and route them correctly.

### Image Processing (OCR Path)
**Nodes**: Loop Over Items1, Google Drive2, HTTP Request, Edit Fields
**Function**: Downloads image files, sends them to OCR.space API for text extraction, then prepares the extracted text for AI processing.
**Configuration**: Requires OCR.space API key in HTTP Request headers.
**Troubleshooting**: Check OCR.space API quota and ensure images are clear and readable.

### PDF Processing (Direct Extraction)
**Nodes**: Loop Over Items, Google Drive, Extract from File, Edit Fields1
**Function**: Downloads PDF files, extracts text content directly using n8n's PDF extraction capabilities, then prepares text for AI processing.
**Configuration**: No external API required for PDF processing.
**Technical Details**: Uses native PDF parsing which is faster than OCR for PDF files.

### AI Data Extraction
**Nodes**: Merge, Loop Over Items2, OpenAI Chat Model1, Information Extractor1
**Function**: Combines processed text from both paths, then uses AI to extract structured invoice data according to predefined schema (invoice numbers, dates, amounts, vendor info, etc.).
**Configuration**: Requires OpenAI-compatible API credentials and proper schema definition.
**Troubleshooting**: Verify API quota and check schema matches your invoice format requirements.

### Data Storage
**Nodes**: Google Sheets
**Function**: Inserts extracted invoice data into the appropriate monthly spreadsheet, updating existing records or creating new ones.
**Configuration**: Requires Google Sheets OAuth2 credentials and proper column mapping.
**Technical Details**: Uses appendOrUpdate operation to avoid duplicate entries based on document file reference.