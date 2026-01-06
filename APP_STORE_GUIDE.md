# Market Pulse - App Store Submission Guide

## Prerequisites
1. **Apple Developer Account** - $99/year at https://developer.apple.com
2. **Mac with Xcode 15+** installed
3. **App icons** (see below)

## Step 1: Open in Xcode
```bash
cd /Users/borishazanov/borishazanov.github.io
npx cap open ios
```

## Step 2: Configure Signing
1. In Xcode, select the **App** project in the navigator
2. Go to **Signing & Capabilities** tab
3. Select your **Team** (your Apple Developer account)
4. Xcode will automatically create provisioning profiles

## Step 3: Create App Icons
You need these icon sizes for the App Store:

| Size | Usage |
|------|-------|
| 1024x1024 | App Store |
| 180x180 | iPhone @3x |
| 120x120 | iPhone @2x |
| 167x167 | iPad Pro |
| 152x152 | iPad @2x |
| 76x76 | iPad @1x |

### Quick way to generate icons:
1. Go to https://appicon.co/
2. Upload your icon image
3. Download the generated icons
4. Replace files in `ios/App/App/Assets.xcassets/AppIcon.appiconset/`

## Step 4: Update App Info
In Xcode, edit these files:

### Info.plist (ios/App/App/Info.plist)
- Bundle Display Name: `Market Pulse`
- Privacy descriptions (if needed)

### Project Settings
- Version: `1.0.0`
- Build: `1`
- Deployment Target: `iOS 14.0` (or higher)

## Step 5: Test on Device
1. Connect your iPhone via USB
2. Select your device in Xcode
3. Click **Run** (▶️)
4. Trust the developer on your iPhone (Settings > General > Device Management)

## Step 6: Archive for App Store
1. Select **Any iOS Device (arm64)** as the build target
2. Go to **Product** → **Archive**
3. Wait for the build to complete
4. In the **Organizer** window, click **Distribute App**
5. Select **App Store Connect**
6. Follow the prompts to upload

## Step 7: App Store Connect
1. Go to https://appstoreconnect.apple.com
2. Create a new app:
   - Bundle ID: `io.github.borishaz.marketpulse`
   - Name: `Market Pulse`
   - Primary Language: English
   - SKU: `market-pulse-001`
3. Fill in the required information:
   - Description
   - Keywords
   - Screenshots (required sizes below)
   - Support URL
   - Privacy Policy URL

## Required Screenshots
| Device | Size |
|--------|------|
| iPhone 6.7" | 1290 x 2796 |
| iPhone 6.5" | 1242 x 2688 |
| iPhone 5.5" | 1242 x 2208 |
| iPad Pro 12.9" | 2048 x 2732 |

### Take Screenshots:
1. Run app in Simulator
2. Press `Cmd + S` to save screenshot
3. Or use **File** → **New Screen Shot**

## Step 8: Submit for Review
1. In App Store Connect, click **Submit for Review**
2. Answer the export compliance questions
3. Wait 24-48 hours for review

## Tips for Approval
- ✅ Add a Privacy Policy URL
- ✅ Explain what the app does in the description
- ✅ Include "Data is for informational purposes only" disclaimer
- ✅ Don't claim to provide financial advice
- ✅ Ensure all API calls work properly

## Useful Commands
```bash
# Sync web changes to iOS
npx cap sync ios

# Open in Xcode
npx cap open ios

# Update Capacitor
npm update @capacitor/core @capacitor/ios
```

## Troubleshooting

### "Signing certificate not found"
- Go to Xcode → Preferences → Accounts → Manage Certificates
- Create a new Apple Development certificate

### "App crashes on launch"
- Check Console.app for error logs
- Ensure all API URLs are in the allowNavigation list

### "Network requests fail"
- Add domains to capacitor.config.json `server.allowNavigation`
- Or use App Transport Security exceptions in Info.plist

