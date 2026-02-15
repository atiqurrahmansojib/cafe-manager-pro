# 📱 Cafe Manager Pro - Installation Guide

## 🚀 Quick Start Options

You have **3 ways** to use Cafe Manager Pro as an app:

---

## ✅ **Method 1: Install as Progressive Web App (PWA) - RECOMMENDED**

This method lets you install the app on your device like a native app!

### **For Desktop (Chrome, Edge, Brave):**

1. **Host the files:**
   - Upload all 3 files to a web hosting service:
     - `index.html`
     - `manifest.json`
     - `service-worker.js`
   
   **Free hosting options:**
   - **GitHub Pages** (recommended): https://pages.github.com
   - **Netlify**: https://www.netlify.com (drag & drop)
   - **Vercel**: https://vercel.com
   - **Cloudflare Pages**: https://pages.cloudflare.com

2. **Visit your hosted URL**

3. **Install the app:**
   - Click the **install icon** (⊕) in the address bar
   - OR click the popup banner that appears
   - OR go to Menu → "Install Cafe Manager Pro"

4. **Launch:** The app will now appear in your applications menu and can run as a standalone window!

### **For Android:**

1. Host files (same as desktop)
2. Open the URL in **Chrome**
3. Tap the **banner** that says "Add Cafe Manager Pro to Home screen"
4. OR tap Menu (⋮) → "Add to Home screen"
5. The app icon will appear on your home screen!

### **For iOS (iPhone/iPad):**

1. Host files (same as desktop)
2. Open the URL in **Safari**
3. Tap the **Share** button (□↑)
4. Scroll and tap **"Add to Home Screen"**
5. Tap **"Add"**
6. The app icon will appear on your home screen!

---

## 🌐 **Method 2: Use Locally with Simple HTTP Server**

Run it directly from your computer without hosting:

### **Option A: Using Python (Built-in on Mac/Linux)**

```bash
# Navigate to the folder with your files
cd /path/to/cafe-manager-files

# Python 3
python3 -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

Then open: **http://localhost:8000**

### **Option B: Using Node.js**

```bash
# Install http-server globally
npm install -g http-server

# Run in the folder
http-server -p 8000
```

Then open: **http://localhost:8000**

### **Option C: Using VS Code**

1. Install **"Live Server"** extension
2. Right-click `index.html`
3. Select **"Open with Live Server"**

---

## 💻 **Method 3: Convert to Desktop App with Electron**

For a true native desktop app experience:

### **Step 1: Install Node.js**
Download from: https://nodejs.org

### **Step 2: Create Electron App**

Create a new folder and add these files:

**package.json:**
```json
{
  "name": "cafe-manager-pro",
  "version": "1.0.0",
  "main": "main.js",
  "scripts": {
    "start": "electron ."
  },
  "devDependencies": {
    "electron": "^28.0.0"
  }
}
```

**main.js:**
```javascript
const { app, BrowserWindow } = require('electron');
const path = require('path');

function createWindow() {
  const win = new BrowserWindow({
    width: 1280,
    height: 800,
    icon: path.join(__dirname, 'icon.png'),
    webPreferences: {
      nodeIntegration: false,
      contextIsolation: true
    }
  });

  win.loadFile('index.html');
}

app.whenReady().then(createWindow);

app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') app.quit();
});

app.on('activate', () => {
  if (BrowserWindow.getAllWindows().length === 0) createWindow();
});
```

### **Step 3: Install & Run**

```bash
# Install dependencies
npm install

# Run the app
npm start
```

### **Step 4: Build Executable (Optional)**

```bash
# Install electron-builder
npm install electron-builder --save-dev

# Add to package.json scripts:
"build": "electron-builder"

# Build
npm run build
```

---

## 📂 **Method 4: Use Directly in Browser**

Simplest option - just double-click `index.html`!

**Note:** Some features may be limited due to browser security restrictions when opening files directly.

---

## 🎯 **Recommended Setup for Different Use Cases:**

| Use Case | Best Method |
|----------|-------------|
| **Personal use on one device** | Double-click HTML or Local Server |
| **Access from multiple devices** | PWA with GitHub Pages hosting |
| **Professional desktop app** | Electron |
| **Mobile app** | PWA (iOS/Android) |
| **Offline use** | PWA or Electron |

---

## 🔧 **Easy GitHub Pages Setup (5 minutes):**

1. Create free account at https://github.com
2. Create new repository named `cafe-manager`
3. Upload your 3 files
4. Go to Settings → Pages
5. Select "main" branch → Save
6. Your app will be live at: `https://yourusername.github.io/cafe-manager`

---

## 💡 **Tips:**

- ✅ All your data is saved **locally** in your browser
- ✅ Works **offline** after first visit (PWA)
- ✅ No backend or database needed
- ✅ **100% privacy** - nothing is sent to any server
- ✅ Can export reports as PDF anytime

---

## 🆘 **Troubleshooting:**

**Q: Install button doesn't appear?**
- Make sure you're using HTTPS or localhost
- PWA requires a web server (can't install from file://)

**Q: Data disappeared?**
- Check if you're using the same browser
- Clear browsing data can delete localStorage

**Q: Can't download PDF?**
- Ensure pop-ups are allowed for the site
- Check browser's download settings

---

## 📞 **Need Help?**

The app stores all data in your browser's localStorage. To backup:
1. Open browser console (F12)
2. Go to Application → Local Storage
3. Copy the data

Enjoy your Cafe Manager Pro! ☕✨
