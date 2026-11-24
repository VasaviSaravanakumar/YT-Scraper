# YouTube Scraper Pro 🎬📊

> A modern, professional bulk YouTube video and channel intelligence research platform with real-time harvesting, deep filters, in-browser preview, and RFC 4180 CSV export.

---

## 🌟 Key Highlights & Features

### 1. 🎛️ Modern SaaS-Style Dashboard Overview
- **KPI Metrics Cards**: Track all-time total searches, videos collected, keywords explored, and CSV datasets exported.
- **Recent Search Runs**: Instant access to previous keyword batches with one-click reload into the active results table and re-export to CSV.
- **Clean Aesthetic**: Slate-900 dark sidebar navigation, indigo/purple primary gradients, YouTube-red accent badges, and rounded card layouts.

### 2. 📝 Bulk Keyword Input & Queue Management
- **Three Versatile Input Modes**:
  1. **Paste Multiple**: Add dozens of keywords at once (one keyword per line or comma-separated).
  2. **Add Individually**: Type single keywords and press Enter.
  3. **Upload TXT or CSV File**: Drag & drop or upload `.txt` or `.csv` files. Includes bundled test samples (`sample_keywords.txt` and `sample_keywords.csv`).
- **Interactive Keyword Tags**: Removable tags with real-time keyword count indicator, quick presets (`+ Digital Marketing`, `+ SEO Tutorial`, `+ Google Ads`, `+ Social Media Marketing`, `+ AI Marketing Tools`), and single-click clear.

### 3. 🔍 Granular YouTube Search Filters
- **Location / Region Filter**: Filter by India (`IN`), USA (`US`), United Kingdom (`GB`), Canada (`CA`), Australia (`AU`), Germany (`DE`), France (`FR`), Japan (`JP`), Brazil (`BR`), etc., or **Global / All**.
- **Results Count**: Select `10`, `20`, `50`, `100`, `200`, or enter a **custom number of results**.
- **Upload Date**: Any time, Last 24 hours (`today`), This week (`this_week`), This month (`this_month`), or Past year (`this_year`).
- **Video Duration**: Any, Under 4 minutes (Short), 4–20 minutes (Medium), or Over 20 minutes (Long).
- **Sorting**: Relevance, Upload date (Newest first), View count (Highest views), or Rating.

### 4. ⚡ Data Collection & Dual API Engine
- **Sequential Automated Harvester**: Iterates over every keyword in the queue automatically.
- **SearchApi.io Integration (Pre-Configured & Active)**:
  - Pre-loaded with your active SearchApi.io key: `HZYcqZGJEphmEyxAp3NR2YxY`.
  - Direct CORS-enabled REST API connection querying YouTube search results in real time.
  - Automatically fetches video durations, exact view counts, channel URLs, and high-resolution thumbnail images.
  - Automatic pagination token handling for requests of 20, 50, 100+ videos per keyword.
- **Official YouTube Data API v3 Engine (Alternate)**:
  - Selectable in Settings for users with a Google Cloud YouTube API Key.
  - Batched `videos.list` and `channels.list` calls for efficient quota usage.
- **Real-time Visual Feedback**:
  - Main percentage progress bar.
  - Active keyword display (`Current Keyword: [name]`).
  - Per-keyword card status (`Pending` &rarr; `Fetching...` &rarr; `[N] videos`).
  - Expandable live execution log console.
- **Deduplication Engine**: Automatically avoids duplicate video entries across keywords while tagging which keyword(s) discovered each video.
- **Smart Demo & Fallback Simulation Engine**: Built-in simulator can be toggled on to test with synthetic data whenever desired.

### 5. 📋 All 12 Extracted Fields
Every collected video record contains:
1. **Video Thumbnail URL**: High-resolution clickable thumbnail image.
2. **Video Title**: Full unescaped video title.
3. **Video Description**: Complete video description text.
4. **Video URL**: Direct link (`https://www.youtube.com/watch?v=VIDEO_ID`).
5. **Video ID**: Unique YouTube 11-character identifier.
6. **Duration**: Formatted as `MM:SS` or `HH:MM:SS`.
7. **Published Date**: ISO date, formatted readable date, and relative time (e.g., "3 days ago").
8. **Views**: Exact view count with comma formatting and compact notation (`1.4M`).
9. **Channel Name**: Creator's YouTube channel title.
10. **Channel URL**: Direct channel link (`https://www.youtube.com/channel/CHANNEL_ID`).
11. **Channel Subscribers**: Public subscriber count or "Hidden".
12. **Search Keyword**: Specific keyword that discovered the video.

### 6. 📊 Structured Results Table & Interactive Tools
- **Live Search**: Instant client-side search across titles, channels, keywords, descriptions, and video IDs.
- **In-Table Multi-Filters**: Filter by keyword, minimum views (`>10K`, `>50K`, `>100K`, `>1M`), duration range, and upload date.
- **Multi-Column Sorting**: Sort by views, subscribers, duration, publication date, title, or channel.
- **Interactive Checkbox Selection**: Select individual rows, select all on current page, or select all filtered videos with bulk action bar.
- **Interactive Modals**:
  - **Video Player Modal**: Click any thumbnail or play icon to launch an in-app 16:9 responsive YouTube preview player.
  - **Video Details Drawer**: Deep inspect tags, engagement numbers, and full descriptions.
- **Configurable Pagination**: Page sizes of 10, 25, 50, or 100 with jump controls.

### 7. 📥 RFC 4180 Compliant CSV Export
- **One-Click Export**: Prominent "Download CSV" button in the top bar and results table.
- **Flexible Scope**:
  - Export all collected results.
  - Export currently filtered results.
  - Export selected videos only (using checkboxes).
  - Export past search runs directly from History.
- **Excel & Spreadsheet Friendly**: Encoded with UTF-8 BOM (`\uFEFF`) and RFC 4180 escaping (double-quoted cells, escaped internal quotes, commas, and newlines).
- **Descriptive Filename**: Automatically formatted as `youtube_scraper_pro_export_YYYY-MM-DD_HHMMSS.csv`.

### 8. 🕒 Search History & Persistence
- Automatically archives search date/time, keywords list, region, requested count, total fetched, and the entire video dataset in browser persistent storage (`localStorage`).
- Reopen past searches at any time to reload them into the active dashboard table.
- Re-download CSV datasets from any past run.

### 9. 🔐 API Settings & Quota Management
- Secure local storage for YouTube Data API v3 key (never sent to third-party backends).
- Built-in "Test API Connection" live verification.
- Real-time API Quota tracker (Search: 100 units, Videos: 1 unit, Channels: 1 unit) showing daily consumption against Google's free 10,000 units/day quota.

---

## 🚀 Getting Started

### Option 1: Direct Browser Launch (Simplest)
Double-click `start_app.bat` or open `index.html` directly in any web browser (Google Chrome, Microsoft Edge, Mozilla Firefox, Brave).

```powershell
start index.html
```

### Option 2: Local Server via PowerShell
Run the included native PowerShell HTTP server on port 3000:

```powershell
powershell -ExecutionPolicy Bypass -File .\server.ps1
```
The server will start listening at `http://localhost:3000` and automatically launch your default browser.

---

## 📁 File Structure

```
Youtube scraper - automation class/
├── index.html              # Main application shell with SaaS dashboard UI
├── styles.css              # Custom SaaS design system & responsive styling
├── app.js                  # Core scraping engine, API connectors, CSV export & state
├── server.ps1              # Lightweight native PowerShell HTTP web server
├── start_app.bat           # 1-click Windows shortcut batch file
├── sample_keywords.txt     # Test keywords file (one per line)
├── sample_keywords.csv     # Test keywords file (CSV format)
└── README.md               # Complete documentation & usage guide
```

---

## 🔑 How to Get a Free YouTube Data API v3 Key
1. Go to [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project (e.g., "YouTube Scraper Pro").
3. Navigate to **APIs & Services > Library**, search for **YouTube Data API v3**, and click **Enable**.
4. Navigate to **APIs & Services > Credentials** and click **Create Credentials > API key**.
5. Copy the API key and paste it into the **API & Quota** tab inside YouTube Scraper Pro.
6. Free tier grants **10,000 quota units per day** at zero cost!
