# 🌴 Palm Fruit Worker Pay System

A modern web-based system to manage worker pay for palm fruit collection business, with AI-powered slip processing.

## Features

✅ **Admin Panel**
- Upload slip photos → Claude AI auto-reads tonnage
- Record daily tons, prices, pay rates
- Track worker loans
- Record payments and auto-deduct loans
- Full payment history

✅ **Worker Dashboard**
- View earnings breakdown by day
- See loan status
- Track payments received
- Real-time updates

✅ **Smart Calculations**
- Auto-calculate: Earnings = Tons × Daily Price × Pay Rate
- Auto-deduct loans from payments
- Monthly summary

✅ **Data Storage**
- All data stored locally in browser (no server needed)
- Easy backup/import

---

## Setup Instructions

### 1. Get Claude API Key (2 minutes)

1. Visit https://console.anthropic.com
2. Sign up or log in
3. Go to **API Keys** → **Create Key**
4. Copy the key (starts with `sk-ant-api03-...`)

**⚠️ Security Note:** The API key will be in your website code (since it's hosted on GitHub Pages). This is fine for a small family business, but you may want to regenerate the key periodically.

### 2. Deploy to GitHub Pages (5 minutes)

#### Option A: Using GitHub Web Interface (Easiest)

1. Go to https://github.com/new (create new repository)
2. Repository name: `palm-fruit-pay` (or any name)
3. Make it **Public**
4. Click **Create repository**

5. Upload files:
   - Click **Add file** → **Upload files**
   - Select `index.html`, `worker.html`
   - Commit

6. Enable GitHub Pages:
   - Go to **Settings** → **Pages**
   - Under "Build and deployment", select **main** branch
   - Click **Save**

7. Your site is now live at: `https://your-username.github.io/palm-fruit-pay/`

#### Option B: Using Git (Command line)

```bash
# Create folder
mkdir palm-fruit-pay
cd palm-fruit-pay

# Copy index.html and worker.html here

# Initialize git
git init
git add .
git commit -m "Initial commit"
git branch -M main

# Add GitHub remote (replace YOUR_USERNAME and REPO_NAME)
git remote add origin https://github.com/YOUR_USERNAME/palm-fruit-pay.git

# Push
git push -u origin main
```

Then enable GitHub Pages (same as Option A step 6).

### 3. First Time Setup

1. Open your site: `https://your-username.github.io/palm-fruit-pay/`
2. You'll see the **Admin Panel**
3. Try uploading a slip photo to test Claude AI integration
4. Add a daily record to start tracking

---

## How to Use

### Admin Workflow

1. **Daily:**
   - Collect slip from worker
   - Upload slip → AI reads tonnage automatically
   - Enter price for that day
   - Enter pay rate (RM/ton)
   - Click "Save Daily Record"

2. **When Worker Borrows:**
   - Go to **Loans** tab
   - Enter amount and reason
   - System tracks it

3. **Payment Day:**
   - Go to **Payments** tab
   - Enter amount paid, method, reference
   - System auto-deducts loans
   - Mark loan as "Deducted"

### Worker View

- Click **Worker View** button to see worker dashboard
- Worker sees only their earnings, loans, and payment history
- Updates in real-time (auto-refreshes every 5 seconds)

---

## Data Format

### Daily Record
```
Date: 2024-01-15
Tons: 2.5
Price per Ton: 700 (RM)
Pay Rate: 70 (RM/ton)
Earnings: 2.5 × 700 × 70 / 100 = 1,225 RM
```

### Example Calculation
- Worker collected: 2.5 tons
- Price that day: RM 700 per ton
- Worker's rate: RM 70 per ton
- Worker's share: 2.5 × 700 × 70 ÷ 100 = **RM 1,225**

---

## Backup & Data Recovery

### Backup Your Data

Your browser stores data in "Local Storage". To backup:

1. Admin Panel → Open **Browser Console** (F12 or Ctrl+Shift+I)
2. Paste this command:
   ```javascript
   copy(localStorage.getItem('workerPayData'))
   ```
3. Save the output somewhere safe (your computer, email, Google Drive)

### Restore Data

1. Go to Admin Panel
2. Open **Browser Console** (F12)
3. Paste this (replace `DATA` with your backed-up data):
   ```javascript
   localStorage.setItem('workerPayData', 'DATA')
   ```
4. Refresh page

---

## AI Slip Reading

Claude AI reads slip photos to extract tonnage automatically. It works best with:
- Clear, well-lit photos
- Numbers clearly visible
- Slip in focus

If AI fails to read, you can manually enter the tonnage.

---

## Customization

### Change Pay Rate Calculation

Edit this line in `index.html` (around line 700):

```javascript
const earnings = tons * price * rate / 100;
```

Example calculations:
- `tons * price * rate / 100` → Current: RM/ton is a percentage
- `tons * rate` → Simple: fixed rate per ton
- `tons * price * (rate / 100)` → Alternative percentage

### Change Colors

Edit the CSS variables at the top of each HTML file:

```css
:root {
    --primary: #d4a574;      /* Change to your preferred color */
    --success: #52b788;
    --warning: #e76f51;
}
```

---

## Troubleshooting

### AI Not Reading Slips
- Check Claude API key is correct in `index.html`
- Ensure photo is clear and well-lit
- Try a different angle
- Manually enter tonnage as backup

### Data Not Saving
- Check browser's Local Storage is enabled
- Try a different browser
- Clear cache and reload

### Can't Access Admin Panel
- You're viewing the worker dashboard
- Click the **Admin Panel** button
- Or visit the main URL

### GitHub Pages Not Working
- Wait 1-2 minutes after enabling Pages
- Make sure files are named exactly: `index.html`, `worker.html`
- Check repository is Public

---

## Security Notes

✅ **What's secure:**
- All data stays on the device (no server)
- No account login needed
- No backend infrastructure

⚠️ **What to be aware of:**
- API key is visible in website code (anyone can see it)
- Regenerate API key monthly
- Delete old keys from Claude Console
- Data stored in browser can be accessed if device is compromised

---

## Support

If you have questions, check:
1. This README
2. Browser console (F12) for error messages
3. Claude's website settings for API key issues

---

## Version
- **Created:** August 2026
- **Last Updated:** August 26, 2026

---

**Made with ❤️ for palm fruit traders**
