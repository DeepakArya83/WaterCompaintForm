# 🚰 Water Complaint Form — Colony SDM Complaint Tool

A simple Hindi/English web form to collect water complaints (कम पानी, बदबूदार पानी, गंदा पानी) from colony residents via WhatsApp, with responses saved directly to Google Sheets.

**Live Form:** https://deepakarya83.github.io/WaterCompaintForm/

---

## 📋 What This Form Does

- Collects resident complaints about water issues in **Sector 2B / 2C**
- Saves all responses directly to **Google Sheets** (via SheetDB)
- Can be shared as a link on **WhatsApp groups**
- Data can be used to file a formal complaint with the **SDM office**

### Fields Collected
| Field | Details |
|---|---|
| Name | Full name of resident |
| Mobile | 10-digit mobile number |
| Sector | Sector 2B or Sector 2C (dropdown) |
| House No | Numeric, max 4 digits (1–9999) |
| Issue | कम पानी / बदबूदार पानी / गंदा पानी (multi-select) |
| Severity | हल्की / मध्यम / गंभीर / बहुत गंभीर |
| Since When | 1 हफ्ते से → 1 साल से ज़्यादा |

---

## 🛠️ Setup & Deployment

### Step 1 — Google Sheet Setup
1. Go to [sheets.google.com](https://sheets.google.com) → Create new sheet
2. Name it: `Pani Shikayat`
3. Add these exact headers in Row 1:
   ```
   Timestamp | Name | Mobile | Sector | House No | Issues | Severity | Since When
   ```
4. Copy the sheet URL

### Step 2 — SheetDB API Setup
1. Go to [sheetdb.io](https://sheetdb.io) → Sign up (free)
2. Click **Create new API** → paste your Google Sheet URL
3. Copy the API URL you receive (format: `https://sheetdb.io/api/v1/XXXXXXXX`)
4. In `index.html`, find this line and replace with your API URL:
   ```javascript
   const res = await fetch('https://sheetdb.io/api/v1/YOUR_API_ID', {
   ```

> **Current API in use:** `https://sheetdb.io/api/v1/6zxrzclrqc5ze`

### Step 3 — GitHub Pages Deployment
1. Upload `index.html` to this repository (rename from `pani_shikayat_v2.html` → `index.html`)
2. Go to **Settings** → **Pages**
3. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)`
4. Click **Save**
5. Wait 2–3 minutes → your link will appear:
   ```
   https://deepakarya83.github.io/WaterCompaintForm/
   ```

---

## 📱 How to Share on WhatsApp

Copy and send this message in your colony WhatsApp group:

```
🚰 कॉलोनी पानी शिकायत फॉर्म

सभी निवासियों से अनुरोध है कि नीचे दिए link पर अपनी पानी की
समस्या दर्ज करें। इन शिकायतों को SDM कार्यालय में submit किया जाएगा।

👉 https://deepakarya83.github.io/WaterCompaintForm/

कृपया सही जानकारी भरें 🙏
```

---

## 📊 Viewing Responses

All submitted responses go directly to your **Google Sheet** in real time.

To export for SDM complaint:
1. Open your Google Sheet
2. **File** → **Download** → **CSV** or **Excel**
3. Attach to your SDM complaint letter

---

## 🔧 Making Changes to the Form

| What to change | Where to edit in `index.html` |
|---|---|
| Add/remove sectors | Find `<select id="f_sector">` |
| Add/remove issue types | Find `<div class="chip-group">` |
| Add/remove "since when" options | Find `<select id="f_since">` |
| Change SheetDB API | Find `fetch('https://sheetdb.io/...')` |
| Change colony name / heading | Find `<h1>` and `<p>` in header |

After any edit, re-upload `index.html` to GitHub → changes go live in ~1 minute.

---

## 🆘 Troubleshooting

| Problem | Solution |
|---|---|
| Form submits but data not in Sheet | Check SheetDB API URL in `index.html` |
| GitHub Pages link not working | Wait 5 min after enabling Pages; check Settings → Pages |
| Old version showing after update | Hard refresh browser: `Ctrl+Shift+R` (Windows) / `Cmd+Shift+R` (Mac) |
| SheetDB free plan limit reached | Free plan allows 500 requests/month; upgrade or create new SheetDB API |

---

## 📞 Useful Contacts

- **Delhi Jal Board Helpline:** 1916
- **SheetDB Support:** [sheetdb.io](https://sheetdb.io)
- **GitHub Pages Docs:** [pages.github.com](https://pages.github.com)

---

*Form created for colony water complaint drive — Sector 2B/2C*
