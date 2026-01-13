# Cyber Crime Reporting Assistant

A secure, client-side bank statement analyzer designed to help victims extract, analyze, and prepare financial evidence for cyber crime complaints.

# Site link: 

https://leonkaushikdeka.github.io/cybercrime-transactionid-extracting-tool/

## Features

### Enhanced Fraud Detection System

The app now uses a multi-layer fraud detection analysis:

#### 1. Keyword Pattern Detection
Scans transaction descriptions for common scam patterns:

| Pattern Category | Keywords | Risk Score |
|-----------------|----------|------------|
| Lottery/Prize | lottery, prize, winner, award, lucky draw | 25 |
| Financial Schemes | bitcoin, crypto, forex, investment, trading, profit | 25 |
| Urgency Scams | urgent, immediate, limited time, act now, account blocked | 25 |
| Government Impersonation | aadhar, pan card, kyc, bank verify, government, tax refund | 25 |
| Job Scams | job offer, work from home, part time, recruitment | 25 |
| Romance Scams | love, romance, dating, match, partner | 25 |
| Refund Scams | refund, cashback, duplicate, wrong transfer | 25 |
| Tech Scams | upi app, app update, technical support, microsoft | 25 |

#### 2. Transaction Behavior Analysis

| Check | Logic | Risk Score |
|-------|-------|------------|
| Very High Amount | Debits >= Rs 100,000 | 35 |
| High Amount | Debits >= Rs 50,000 | 20 |
| Round Amount | 1000, 5000, 10000, 50000, etc. | 10 |
| Repeated Amount | Same amount 3+ times | 15 |
| Late Night | 1 AM - 5 AM transactions | 15 |
| Repeated Recipient | 3+ transactions to same UPI | 15 |
| New Recipient | First transaction to UPI ID | 5 |
| Burst Pattern | 5+ transactions in 30 minutes | 20 |
| Unusual Amount | 3x average transaction | 15 |

#### 3. Risk Scoring (0-100)

| Risk Level | Score Range | Color |
|------------|-------------|-------|
| **Low** | 0-25 | Green |
| **Medium** | 26-50 | Yellow |
| **High** | 51-75 | Orange |
| **Critical** | 76-100 | Red |

#### 4. Risk Summary Dashboard

After running analysis, a summary panel shows:
- Critical Risk count
- High Risk count
- Medium Risk count
- Low Risk count
- Total amount at risk (high + critical debits)

#### 5. Interactive Risk Indicators

Each transaction in the table shows:
- Risk score (0-100)
- Color-coded indicator
- Hover tooltip with specific risk factors

#### 6. Filter by Risk Level

Filter transactions by:
- All Risk Levels
- Critical Risk Only
- High Risk Only
- Medium+ Risk (medium, high, critical)
- Flagged Transactions (high + critical)

### File Upload & Parsing
- **CSV Support**: Parse comma-separated bank statement files
- **Excel Support**: Read `.xlsx` and `.xls` files using SheetJS
- **PDF Support**: Experimental PDF parsing using PDF.js with regex-based extraction
- **Drag & Drop**: Convenient file upload interface
- **Progress Tracking**: Real-time progress bar with cancel option
- **Max File Size**: 15MB limit

### Automatic Fraud Detection
- **High Value Threshold**: Debits over Rs 50,000 are flagged
- **Unusual Time**: Transactions between 1 AM - 4 AM over Rs 10,000
- **Repeated Beneficiary**: Same UPI ID appearing 2+ times
- **Repeated Amount**: Same amount (Rs 5,000+) appearing 2+ times

### Filtering & Sorting
- **Search**: Filter by description, transaction ID, or UPI ID
- **Date Range**: Filter transactions by date period
- **Transaction Type**: Show debits, credits only
- **Risk Level**: Filter by risk (low/medium/high/critical)
- **Column Sorting**: Click any column header to sort

### Batch Operations
- **Batch Selection**: Select multiple transactions with checkboxes
- **Bulk Delete**: Remove unwanted transactions
- **Bulk Tagging**: Mark multiple transactions as Fraud/Legitimate/Pending
- **Clear Selection**: Quick deselect all selected transactions

### Transaction Management
- **Select/Deselect**: Individual checkboxes or Select All
- **Keyboard Shortcuts**:
  - `Ctrl+A` - Select All
  - `Ctrl+D` - Deselect All
  - `Ctrl+S` - Save Progress
  - `Ctrl+L` - Load Progress
  - `Escape` - Close Modal
- **Notes**: Add custom notes to each transaction
- **Tags**: Categorize transactions as Fraud, Legitimate, or Pending Review
- **Color Coding**: Debits (red), Credits (green), Suspicious (red background)

### Visual Analytics
- **Transaction Timeline**: Visual timeline of recent transactions (last 20)
- **Daily Activity Chart**: Bar chart showing transaction activity over 7 days
- **Category Distribution**: Category breakdown (UPI, Bank Transfer, ATM, Other)

### Quick Stats Dashboard
Real-time statistics display:
- Total Transactions count
- Total Debits (sum)
- Total Credits (sum)
- Suspicious Transactions count
- Selected Transactions count
- Average Transaction value
- Active Days count
- Largest Single Debit
- UPI Transactions count

### Transaction Details Modal
Click any transaction to view full details:
- Date, Amount, Balance
- Transaction ID and UPI ID
- Risk score and factors
- Tags and Notes
- Quick actions: Delete, Copy Details, Tag

### Export Options
- **Copy to Clipboard**: Formatted text for pasting into complaint forms
- **CSV Export**: Download selected transactions with all details
- **Date Filename**: Export files are named with current date

### Auto-Save & Progress Storage
- **Auto-Save**: Progress automatically saves every 30 seconds
- **Manual Save**: Click Save button or `Ctrl+S`
- **Local Storage**: All data stored in browser localStorage
- **Persistent**: Data survives browser refresh/close
- **Load Progress**: Restore previously saved work

## Privacy & Security

- **100% Client-Side**: All processing happens in your browser
- **No Server Uploads**: Your financial data never leaves your device
- **XSS Protection**: HTML content is sanitized before rendering
- **Works Offline**: After initial library load, no internet required

## Supported Date Formats

- `DD/MM/YYYY` (e.g., 15/01/2024)
- `DD-MM-YYYY` (e.g., 15-01-2024)
- `YYYY-MM-DD` (e.g., 2024-01-15)
- Excel Serial Dates (automatically converted)

## Metadata Extraction

- **UPI IDs**: Pattern `user@bank`
- **Transaction IDs**: UTR, RRN, IMPS, NEFT, or UPI references (12+ digits)

## Demo Mode

Click the **Load Demo Data** button to load sample data with 6 transactions including:
- Multiple payments to the same UPI ID
- A credit transaction
- A high-value debit (Rs 60,000)
- Transactions with various risk patterns

Test all features without uploading personal data.

## Usage Guide

1. **Open the Application**
   - Open `cyber-crime-reporting-assistant.html` in any modern browser
   - Click **Load Demo Data** to explore with sample data

2. **Upload Your Bank Statement**
   - Drag and drop your file or click "Choose File"
   - Supported formats: `.csv`, `.xlsx`, `.xls`, `.pdf`
   - Wait for parsing to complete

3. **Run Risk Analysis**
   - Click **Analyze Risk** to run comprehensive fraud detection
   - Review the Risk Summary panel
   - Filter by risk level to focus on suspicious transactions
   - Hover over risk indicators to see specific factors

4. **Filter & Review**
   - Use search box to find specific transactions
   - Set date range to narrow down time period
   - Filter by type (debit/credit) and risk level
   - Sort by any column (Date, Amount, Risk Score, etc.)

5. **Batch Operations**
   - Click **Batch Select** to enter batch mode
   - Click multiple transactions to select them
   - Use batch toolbar to Delete, Mark Fraud, or Mark Legit

6. **View Analytics**
   - Click **Timeline** to see visual transaction timeline
   - Click **Charts** to view daily activity and categories

7. **Transaction Details**
   - Click **Details** button to view selected transaction
   - Click any row to open detailed modal
   - Add tags and notes directly in the modal

8. **Save Your Work**
   - Progress auto-saves every 30 seconds
   - Click **Save** or press `Ctrl+S` to save manually
   - Click **Load** or press `Ctrl+L` to restore saved work

9. **Export Evidence**
   - Select transactions using checkboxes
   - Click **Copy** to copy formatted text to clipboard
   - Click **Export** to download as CSV file
   - Paste copied data directly into cyber crime complaint forms

## Reporting Information Requirements

Cyber crime portals (e.g., cybercell.gov.in) typically require:
- **Transaction ID (UTR/RRN)**: 12-22 digit unique reference number
- **Beneficiary Details**: Bank Name, Account Number, or UPI ID
- **Date & Amount**: Precise timestamp and value

## Browser Support

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | 90+ | Fully Supported |
| Edge | 90+ | Fully Supported |
| Firefox | 88+ | Fully Supported |
| Safari | 14+ | Fully Supported |

## Dependencies

All libraries are loaded via CDN:
- **PapaParse** v5.3.0 - CSV parsing
- **SheetJS** v0.18.5 - Excel file reading
- **PDF.js** v3.11.174 - PDF text extraction

## Configuration

Edit `CONFIG` object in the HTML file to customize:
```javascript
{
    MAX_FILE_SIZE: 15 * 1024 * 1024,  // 15MB
    DEBOUNCE_DELAY: 300,              // Filter delay (ms)
    SUSPICIOUS_AMOUNT_THRESHOLD: 50000, // High value threshold (Rs)
    REPEAT_COUNT_THRESHOLD: 2,         // Repeat detection count
    SUPPORTED_TYPES: ['.csv', '.xlsx', '.xls', '.pdf'],
    DATE_FORMATS: ['DD/MM/YYYY', 'YYYY-MM-DD', 'DD-MM-YYYY']
}
```

## File Column Mapping

The app automatically detects bank statement columns using fuzzy matching:
- **Date**: `date`, `transaction date`, `value date`, `time`
- **Description**: `description`, `narration`, `particulars`, `remarks`, `details`
- **Amount**: `amount`, `debit`, `credit`, `withdrawal`, `deposit`
- **Balance**: `balance`, `closing balance`

## Troubleshooting

### File Not Parsing
- Ensure file format is supported (.csv, .xlsx, .xls, .pdf)
- Check file size is under 15MB
- PDF parsing is experimental - use CSV/Excel for best results

### Libraries Not Loading
- Check your internet connection (CDNs required on first load)
- Try refreshing the page
- Check browser console for specific error messages

### Copy/Export Buttons Not Working
- If opening via `file://` protocol, some browsers restrict clipboard/download APIs
- Use the fallback copy method or try in a local server
- Some browsers require HTTPS for clipboard API

### Data Not Saving
- Check browser localStorage is enabled
- Clear browser cache and try again
- Some privacy modes disable localStorage

## New Features (Enhanced Fraud Detection)

### Version 2.0 - Enhanced Fraud Detection
- **Multi-Layer Detection**: 8 scam pattern categories with keyword matching
- **Risk Scoring**: 0-100 score per transaction with 4 risk levels
- **Risk Summary Dashboard**: Overview of all transactions by risk level
- **Interactive Tooltips**: Hover over risk indicators to see specific factors
- **Risk Filtering**: Filter transactions by risk level
- **Visual Indicators**: Color-coded risk badges in the transaction table
- **India-Specific Patterns**: Aadhar, PAN, UPI scam patterns
- **Burst Detection**: Identify rapid successive transactions
- **Anomaly Detection**: Flag unusual amounts compared to average

## License

MIT License - Feel free to use and modify for personal or commercial use.

## Disclaimer

This tool is designed to assist victims in organizing evidence for cyber crime complaints. It does not replace legal advice. Always consult appropriate authorities for official reporting procedures.
