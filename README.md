# Media Downloader — Chrome Extension

A minimalist, high-performance Chrome extension (Manifest V3) designed to detect, extract, and download high-resolution media (images, videos, audio, and background assets) from any active webpage with a single click, or export the webpage directly as a clean PDF.

Built with a sleek, monochromatic dark UI, real-time extraction status feedback, and a responsive global kill switch to stop downloads at any moment.

---

## ✨ Features

- **⚡ Deep Media Extraction**:
  - **Images & Responsive `srcset`**: Scrapes all `<img>` tags and parses `srcset` / `data-srcset` attributes to automatically select and download the highest-resolution version available.
  - **Lazy-Loaded Elements**: Gracefully handles lazy-loaded media (`data-src`, `data-original`).
  - **Videos & Audio**: Extracts `<video>` and `<audio>` sources, including nested `<source>` tags.
  - **CSS Background Assets**: Inspects computed styles to pull high-res background images defined in stylesheets or inline styles.
  - **Data URLs**: Supports inline data URIs while filtering out 1x1 tracking pixels.

- **💾 Dual Download Modes**:
  - **Direct Downloads**: Uses Chrome's native `chrome.downloads` API with automatic filename conflict handling (`uniquify`) and throttled request dispatching to prevent browser choking.
  - **Custom Folder Selection**: Uses the modern **File System Access API** (`window.showDirectoryPicker`) to let you save media directly into any local folder (e.g., Desktop, external SSD, or a specific project directory) without cluttering your browser's default download directory.

- **🛑 Mid-Process Kill Switch**:
  - Instant `STOP` control that immediately halts downloads midway.
  - Cancels pending `chrome.downloads` jobs and aborts active network fetch streams using `AbortController`.

- **🖨️ Webpage Print-to-PDF**:
  - Instant one-click trigger for the browser's native print dialog to save the entire page as a clean PDF document.

- **🖤 Minimalist Monochromatic Interface**:
  - Non-standard, clean 2x2 asymmetric card grid layout.
  - Pure grayscale/dark-mode aesthetic without bright or distracting colors.
  - Live status indicator dot and media counter.

---

## 📁 Project Structure

```text
media_download_extension/
├── manifest.json      # Extension metadata, permissions, and Manifest V3 configuration
├── popup.html         # Monochromatic popup interface and action cards
├── popup.css          # Dark-mode styling, asymmetric grid, and animations
├── popup.js           # Media extraction dispatch, download handlers, File System API & Kill Switch
├── content.js         # Injected DOM scraper for images, srcset, videos, audio, and styles
├── images.jpg         # Extension icon
└── README.md          # Project documentation
```

---

## 🚀 Installation & Setup

Because this extension is built with standard Manifest V3 web standards, you can load it into any Chromium-based browser (Google Chrome, Brave, Microsoft Edge, Opera, Vivaldi) without needing Node.js or any build steps.

1. **Clone or Download the Repository**:
   ```bash
   git clone https://github.com/dhyey-doshi/media_download_extension.git
   ```
   *(Or download and extract the ZIP archive).*

2. **Open Extensions Page**:
   - In Google Chrome, navigate to `chrome://extensions/`
   - In Brave, navigate to `brave://extensions/`
   - In Microsoft Edge, navigate to `edge://extensions/`

3. **Enable Developer Mode**:
   - Toggle the **Developer mode** switch in the top-right corner.

4. **Load the Extension**:
   - Click **Load unpacked** in the top-left corner.
   - Select the folder containing `manifest.json` (e.g., `media_download_extension`).

5. **Pin to Toolbar**:
   - Click the puzzle icon (Extensions) in your browser toolbar and pin **CHROME MEDIA DOWNLOADER** for quick access.

---

## 📖 How to Use

1. **Navigate to Any Webpage**:
   - Open any webpage containing media you want to save.
2. **Open the Extension**:
   - Click the extension icon in your browser toolbar. The extension scans the page and displays the total number of detected media files.
3. **Choose an Action**:
   - **Download Media**: Saves all discovered high-resolution media into your default browser `Downloads` folder.
   - **Custom Folder**: Prompts a system directory picker (`showDirectoryPicker`) so you can select any custom directory on your computer to save all files directly.
   - **Print Page**: Opens the browser's print dialog to save the webpage as a PDF.
4. **Kill Switch (Abort)**:
   - While downloading, a red **STOP** button appears. Clicking it immediately aborts remaining downloads and network requests.

---

## 🔒 Permissions & Security

This extension adheres to the Chrome Manifest V3 security model with minimal, scoped permissions:

| Permission | Purpose |
| :--- | :--- |
| `activeTab` | Scrapes media only from the tab currently focused when you open the popup. |
| `scripting` | Injects the lightweight `content.js` scraper into the active tab on demand. |
| `downloads` | Uses Chrome's download manager for rapid, conflict-safe file downloads. |
| `<all_urls>` | Enables downloading media hosted on external CDNs and cross-origin domains. |

> **Privacy Notice**: This extension operates completely locally on your machine. No telemetry, browsing data, or downloaded media is collected, tracked, or sent to any external server.

---

## 🛠️ Built With

- **HTML5 & CSS3** (Vanilla, CSS Grid, Custom SVG Icons)
- **JavaScript** (Modern ES6+, Async/Await, Fetch API, AbortController)
- **Chrome Extensions API** (Manifest V3, `chrome.scripting`, `chrome.downloads`, `chrome.tabs`)
- **File System Access API** (`window.showDirectoryPicker`, `FileSystemWritableFileStream`)

---

## 👤 Author

Developed by **[Dhyey Doshi](https://github.com/dhyey-doshi)**.

---

## 📄 License

Distributed under the [MIT License](LICENSE). Feel free to inspect, modify, and improve!
