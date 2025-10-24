## Yellow Sticky Note - Main Workflow Explanation

**Template Purpose**: Automatically extract and process invoice data from PDF files and images stored in Google Drive, then export structured information to Google Sheets for accounting and analysis.

**Workflow Description**: This workflow scans organized company/month folders in Google Drive, identifies invoice files (PDF and images), processes them using OCR and AI extraction, and populates a structured spreadsheet with key invoice data including invoice numbers, dates, amounts, seller/buyer information, and line items.

**Key Features**:
- Multi-format support (PDF and image files)
- Intelligent AI-powered data extraction
- Automated folder organization
- Batch processing capabilities
- Structured spreadsheet output

## White Sticky Notes - Node Explanations

### Folder Discovery & Organization
**Nodes**: Schedule Trigger, Get Company Folders, Get All Company Month Folders, Keep Only This Month
**Function**: Scans Google Drive for company folders and their month subfolders, filtering to only process current month's data
**Configuration**: Update folder IDs and date filtering logic as needed
**Technical**: Uses Google Drive API to list folders and filter by current month

### Spreadsheet Management
**Nodes**: Find Spreadsheet, Google Drive1, Edit Fields2/4, Loop Over Items3
**Function**: Searches for existing spreadsheets in month folders, creates new ones from template if missing
**Configuration**: Requires Google Sheets template file ID
**Technical**: Copies template spreadsheet and tracks spreadsheet metadata

### File Processing Pipeline
**Nodes**: Get All Files, Keep Only Images And PDF, Switch1, Edit Fields3
**Function**: Identifies invoice files, categorizes by file type, and prepares for processing
**Configuration**: File type filters can be modified for different formats
**Technical**: Uses MIME type detection and conditional routing

### Image Invoice Processing
**Nodes**: Loop Over Items1, Google Drive2, HTTP Request, Edit Fields
**Function**: Downloads image files, sends to OCR.Space API for text extraction
**Configuration**: Requires OCR.Space API key in HTTP Request headers
**Technical**: Uses multipart form data upload to OCR service

### PDF Invoice Processing
**Nodes**: Loop Over Items, Google Drive, Extract from File, Edit Fields1
**Function**: Downloads PDF files and extracts text content directly
**Configuration**: No external API required for PDF text extraction
**Technical**: Uses n8n's built-in PDF text extraction capabilities

### AI Data Extraction
**Nodes**: Merge, Loop Over Items2, OpenAI Chat Model1, Information Extractor1
**Function**: Processes extracted text using AI to identify and structure invoice data
**Configuration**: Requires AI model credentials and schema definition
**Technical**: Uses structured extraction with predefined invoice schema

### Data Export
**Nodes**: Google Sheets
**Function**: Writes extracted invoice data to Google Sheets with proper formatting
**Configuration**: Maps extracted fields to spreadsheet columns
**Technical**: Uses append/update operations to maintain data integrity