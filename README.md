# Cyber Crime Evidence Tool

A free, privacy-first bank statement analyzer designed to help **police officers** and **citizens** extract, analyze, and prepare financial evidence for cyber crime complaints in India.

**Live Tool:** https://leonkaushikdeka.github.io/cybercrime-transactionid-extracting-tool/

## Who Is This For?

- **Citizens** who are victims of UPI fraud, phishing, or online scams
- **Police officers** investigating cyber crime cases
- **Cyber crime cells** processing financial evidence
- **Legal professionals** preparing evidence for court

## Key Features

### Case Management & Evidence Chain
- **Complainant Details Form** — Capture name, phone, FIR number, police station, bank details
- **File Integrity Hash (SHA-256)** — Cryptographic proof that the uploaded file was not tampered with
- **Bilingual Interface** — English + Hindi labels for key fields
- **Step-by-Step Wizard** — Guided workflow: Case Details → Upload → Analyze → Report

### Evidence Report Generator
- **Professional Evidence Report** — Court-ready format with complainant details, bank info, fraud description, and suspicious transaction table
- **Print-Ready** — Clean print stylesheet for physical filing
- **Cybercrime Portal Export** — CSV format compatible with cybercrime.gov.in complaint forms
- **Copy to Clipboard** — Formatted plain text for pasting into online complaint forms

### Enhanced Fraud Detection (Multi-Layer Analysis)

#### 1. Keyword Pattern Detection
Scans for 8 categories of scam patterns:
- Lottery/Prize scams
- Crypto/Investment schemes
- Urgency/Account blocking scams
- Government impersonation (Aadhar, PAN, KYC)
- Job scams
- Romance scams
- Refund scams
- Tech support scams

#### 2. Transaction Behavior Analysis
| Check | Logic | Risk Score |
|-------|-------|------------|
| Very High Amount | Debits >= Rs 1,00,000 | 35 |
| High Amount | Debits >= Rs 50,000 | 20 |
| Round Amount | 1000, 5000, 10000, 50000, etc. | 10 |
| Repeated Amount | Same amount 3+ times | 15 |
| Late Night | 1 AM - 5 AM transactions | 15 |
| Repeated Recipient | 3+ transactions to same UPI | 15 |
| Burst Pattern | 5+ transactions in 30 minutes | 20 |
| Unusual Amount | 3x average transaction | 15 |

#### 3. Risk Scoring (0-100)
| Risk Level | Score Range | Color |
|------------|-------------|-------|
| Low | 0-25 | Green |
| Medium | 26-50 | Yellow |
| High | 51-75 | Orange |
| Critical | 76-100 | Red |

### File Upload & Parsing
- **CSV** — Comma-separated bank statement files
- **Excel** — `.xlsx` and `.xls` files via SheetJS
- **PDF** — Experimental PDF parsing via PDF.js
- **Drag & Drop** — File upload interface with progress tracking
- **Max Size** — 15MB limit

### Automatic Column Detection
Fuzzy matches common bank statement headers:
- **Date**: `date`, `transaction date`, `value date`
- **Description**: `description`, `narration`, `particulars`, `remarks`
- **Amount**: `amount`, `debit`, `credit`, `withdrawal`, `deposit`
- **Balance**: `balance`, `closing balance`

### Metadata Extraction
- **UPI IDs** — Pattern: `user@bank`
- **Transaction IDs** — UTR, RRN, IMPS, NEFT, UPI references (12+ digits)

### Filtering, Sorting & Batch Operations
- Search by description, transaction ID, or UPI ID
- Filter by date range, transaction type, risk level
- Sort by any column
- Batch select, delete, tag as Fraud/Legitimate/Pending

### Visual Analytics
- Transaction timeline (last 20)
- Daily activity bar chart (last 7 days)
- Category distribution (UPI, Bank Transfer, ATM, Other)

### Auto-Save & Keyboard Shortcuts
- Auto-saves every 30 seconds to localStorage
- `Ctrl+A` Select All, `Ctrl+D` Deselect All
- `Ctrl+S` Save, `Ctrl+L` Load, `Escape` Close Modal

## Privacy & Security

- **100% Client-Side** — All processing happens in your browser
- **No Server Uploads** — Your financial data never leaves your device
- **XSS Protection** — HTML content is sanitized before rendering
- **SHA-256 File Hash** — Proves file integrity for evidence chain
- **Works Offline** — After initial library load, no internet required

## Usage Guide

### For Citizens (Victims)

1. **Fill Case Details** — Enter your name, phone, FIR number (if filed), bank details
2. **Upload Bank Statement** — Drag and drop your CSV/Excel/PDF file
3. **Click "Analyze Risk"** — The tool automatically detects suspicious transactions
4. **Review Flagged Transactions** — Check the highlighted transactions
5. **Generate Report** — Click "Generate Report" for a complete evidence document
6. **File Your Complaint:**
   - Call **1930** (National Cyber Crime Helpline, 24x7)
   - Visit **https://cybercrime.gov.in** and paste the report
   - Visit your local police station with the printed report

### For Police Officers

1. **Receive Bank Statement** from complainant
2. **Upload and Analyze** — Tool flags suspicious patterns automatically
3. **Review Risk Scores** — Focus on Critical (76-100) and High (51-75) risk transactions
4. **Generate Evidence Report** — Professional format ready for case file
5. **Export CSV** — Use "Export for Cybercrime Portal" for structured data

## Supported Date Formats

- `DD/MM/YYYY` (e.g., 15/01/2024)
- `DD-MM-YYYY` (e.g., 15-01-2024)
- `YYYY-MM-DD` (e.g., 2024-01-15)
- Excel Serial Dates (automatically converted)

## Browser Support

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | 90+ | Fully Supported |
| Edge | 90+ | Fully Supported |
| Firefox | 88+ | Fully Supported |
| Safari | 14+ | Fully Supported |

## Dependencies

All libraries loaded via CDN (no server required):
- **PapaParse** v5.3.0 — CSV parsing
- **SheetJS** v0.18.5 — Excel file reading
- **PDF.js** v3.11.174 — PDF text extraction
- **Web Crypto API** — SHA-256 file hashing (built into browsers)

## Demo Mode

Click **Load Demo Data** to test all features with sample transactions without uploading personal data.

## License

MIT License — Free to use and modify for personal, government, or commercial use.

## Disclaimer

This tool assists in organizing evidence for cyber crime complaints. It does not constitute legal advice. Always consult appropriate authorities and file complaints through official channels.

**National Cyber Crime Helpline: 1930**
**Online Complaint Portal: https://cybercrime.gov.in**
