# 3v3 Calculator — iOS App Setup Guide

## What you have
A fully self-contained PWA (Progressive Web App) that works as:
1. **A website** — open the HTML file in any browser
2. **An iPhone home screen app** — no App Store needed (instructions below)
3. **A native iOS App Store app** — using Capacitor (instructions below)

---

## Option A: iPhone Home Screen App (Instant, Free)

This is the quickest way to get it on your phone feeling like a real app.

### Files needed (keep all together in one folder):
```
iokf_3v3_calculator.html
manifest.json
sw.js
icon-192.png
icon-512.png
icon-180.png
favicon.ico
```

### To deploy (you need a web server — even a simple one):

**Easiest: Use GitHub Pages (free)**
1. Create a free account at github.com
2. Create a new repository called `3v3-calculator`
3. Upload all the files above
4. Go to Settings → Pages → set Source to "main branch"
5. Your app will be live at `https://yourusername.github.io/3v3-calculator/iokf_3v3_calculator.html`

**On iPhone:**
1. Open the URL in Safari (must be Safari, not Chrome)
2. Tap the Share button (box with arrow)
3. Tap "Add to Home Screen"
4. Name it "3v3 Calculator" and tap Add
5. The app icon appears on your home screen — tap it and it opens full-screen with no browser chrome, just like a native app ✅

---

## Option B: Native iOS App (App Store submission)

This requires a Mac with Xcode and an Apple Developer account ($99/year).

### Prerequisites
- Mac computer
- Xcode installed (free from Mac App Store)
- Node.js installed (nodejs.org)
- Apple Developer account (developer.apple.com)

### Steps

**1. Install Capacitor**
```bash
npm install -g @capacitor/cli
npm install @capacitor/core @capacitor/ios
```

**2. Set up the project**
```bash
# Create a folder and put all your files in it
mkdir iokf-3v3
cd iokf-3v3
# Copy all files here

# Initialise Capacitor (uses capacitor.config.json)
npx cap init "3v3 Calculator" "com.itsonlykidsfootball.calculator3v3" --web-dir .

# Add iOS platform
npx cap add ios
```

**3. Copy web assets**
```bash
npx cap copy ios
```

**4. Open in Xcode**
```bash
npx cap open ios
```

**5. In Xcode:**
- Set your Team (Apple Developer account) under Signing & Capabilities
- Replace the default app icons with `icon-192.png` and `icon-512.png`
  (Xcode will ask you to provide all required sizes — use an online tool like
  appicon.co to generate the full iOS icon set from icon-512.png)
- Set the Bundle Identifier to: `com.itsonlykidsfootball.calculator3v3`
- Set the Display Name to: `3v3 Calculator`

**6. Test on your iPhone**
- Connect iPhone via USB
- Select your iPhone as the target in Xcode
- Press the Play button
- Trust the developer certificate on your iPhone (Settings → General → VPN & Device Management)

**7. Submit to App Store**
- Product → Archive in Xcode
- Follow the App Store Connect upload process
- App Review typically takes 1-3 days

---

## App Details (for App Store submission)

- **App Name:** 3v3 Calculator
- **Bundle ID:** com.itsonlykidsfootball.calculator3v3
- **Category:** Sports / Utilities
- **Age Rating:** 4+
- **Description:** Work out the best 3v3 format for your grassroots football session. By It's Only Kids' Football Podcast.

---

## Offline Support

The service worker (`sw.js`) caches the entire app on first load.
After that it works completely offline — perfect for the sideline with no signal.

---

## Questions?
Visit itsonlykidsfootball.com or contact the podcast team.
