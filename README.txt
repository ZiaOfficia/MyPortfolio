# Mohammad Abdullah — Portfolio
## Setup Guide

---

## Google Sheets Contact Form Integration

When you're ready to connect the contact form to Google Sheets, follow these steps:

### Step 1: Create a Google Sheet
1. Go to sheets.google.com and create a new spreadsheet
2. Add these headers in Row 1:
   - A1: Timestamp
   - B1: Name
   - C1: Email
   - D1: Subject
   - E1: Message

### Step 2: Create Apps Script
1. In your Google Sheet, click Extensions → Apps Script
2. Delete all existing code
3. Paste this code:

function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = e.parameter;
  sheet.appendRow([
    data.timestamp || new Date().toISOString(),
    data.name || '',
    data.email || '',
    data.subject || '',
    data.message || ''
  ]);
  return ContentService
    .createTextOutput(JSON.stringify({ result: 'success' }))
    .setMimeType(ContentService.MimeType.JSON);
}

### Step 3: Deploy as Web App
1. Click Deploy → New Deployment
2. Type: Web App
3. Execute as: Me
4. Who has access: Anyone
5. Click Deploy and copy the Web App URL

### Step 4: Add URL to index.html
Find this line in index.html:
   const SHEET_URL = 'YOUR_GOOGLE_APPS_SCRIPT_URL_HERE';
Replace with your copied URL.

---

## Customization Tips
- Change accent color: Find --accent: #d63031 in :root CSS variables
- Replace portrait photo: Update src in .portrait-frame img
- Update contact links: Search for mohammad@email.com etc.
- Add real project links: Update href="#" on each .project-card

Built with intent. (c) 2025 Mohammad Abdullah
