# SSIS Inventory Management System (Gateway Wrapper Method)

Production-ready code for **San Simon Integrated School Inventory System** with:
1. **Premium Loading Overlay**: Same design as the SSIS Leave Card & Portal (bouncing emoji, spinner, smooth fade).
2. **Advanced Pagination**: Items-per-page selector (12, 24, 48, 96, All), range indicator ("Showing 1–12 of 142"), and smart numbered page buttons (« First, ‹ Prev, 1, 2, 3..., Next ›, Last »).
3. **Gateway Wrapper Method (Vercel Serverless)**: Edit `Index.html` or `Code.gs` in Google Apps Script, and Vercel updates **100% automatically without touching GitHub again**.
4. **Universal Backend Caller**: Works both inside Google Apps Script (`google.script.run`) and externally on Vercel (`fetch API`).

---

## 📁 Project Structure

```text
ssis-inventory/
├── api/
│   └── index.js     # Vercel Serverless Gateway (pulls live Index.html from Apps Script)
├── Index.html       # Frontend template (paste into Apps Script Index.html)
├── Code.gs          # Backend code (paste into Apps Script Code.gs)
├── vercel.json      # Vercel routing configuration
└── README.md        # Setup & documentation
```

---

## 🚀 How to Set Up (One-Time Setup)

### Step 1: Update Google Apps Script
1. Open your Google Spreadsheet for Inventory.
2. Go to **Extensions** > **Apps Script**.
3. Replace the content of **`Code.gs`** with the code from [`Code.gs`](./Code.gs).
4. Replace the content of **`Index.html`** with the code from [`Index.html`](./Index.html).
5. Click **Save** (💾).
6. Click **Deploy** > **Manage deployments**.
7. Click the **Pencil (Edit)** icon on your active deployment.
8. Set **Version** to **New version**.
9. Ensure:
   - **Execute as**: `Me`
   - **Who has access**: `Anyone`
10. Click **Deploy** and copy your **Web App URL**.

---

### Step 2: Set your Apps Script URL in `api/index.js`
In [`api/index.js`](./api/index.js), ensure `APPSCRIPT_URL` has your Google Apps Script Web App URL with `?action=getAppHtml` at the end:
```javascript
const APPSCRIPT_URL = 'https://script.google.com/macros/s/YOUR_SCRIPT_ID/exec?action=getAppHtml';
```

---

### Step 3: One-Time Upload to GitHub
1. Create a repository on GitHub named `ssis-inventory`.
2. Upload:
   - The `api/` folder (with `index.js`)
   - `vercel.json`
3. Commit the changes.

---

### Step 4: Deploy to Vercel
1. In Vercel, import your `ssis-inventory` GitHub repository.
2. Click **Deploy**.
3. Done!

---

## 🔄 Future Updates (No GitHub Needed!)

Whenever you change **`Index.html`** or **`Code.gs`** inside Google Apps Script:
1. Make your changes in Apps Script.
2. Click **Deploy** > **Manage deployments** > **Edit** > Version: **New version** > **Deploy**.
3. **That's it!** Open your Vercel URL — your changes are immediately live. You never need to upload to GitHub again!
