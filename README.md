# NAA Test App

Minimal test app to validate NAA (Nested App Authentication) works on iOS Teams mobile.

## Quick Setup

### 1. Azure AD App Registration

1. Go to [Azure Portal](https://portal.azure.com) → App registrations → New registration
2. Name: `NAA-Test-App`
3. Supported account types: Single tenant
4. Click Register
5. Note the **Application (client) ID** and **Directory (tenant) ID**

### 2. Configure Redirect URIs

1. Go to Authentication → Add a platform → Single-page application
2. Add these redirect URIs:
   ```
   https://YOUR_GITHUB_USERNAME.github.io
   brk-multihub://YOUR_GITHUB_USERNAME.github.io
   ```
3. Check: Access tokens, ID tokens
4. Save

### 3. API Permissions

1. Go to API permissions → Add a permission
2. Microsoft Graph → Delegated → `User.Read`
3. Grant admin consent

### 4. Update manifest.json

Replace these placeholders in `manifest.json`:
- `YOUR_GITHUB_USERNAME` → your actual GitHub username
- `YOUR_AZURE_CLIENT_ID` → your Azure AD Client ID

### 5. Create Icons

Create two simple PNG icons (can be solid color squares):
- `color.png` - 192x192 pixels
- `outline.png` - 32x32 pixels

Quick way: Use any image editor or online tool like https://placeholderlogo.com

### 6. Create manifest.zip

Zip these files together:
- manifest.json
- color.png
- outline.png

On Windows: Select all 3 files → Right-click → Send to → Compressed folder

### 7. Deploy to GitHub Pages

1. Create a new GitHub repo (e.g., `naa-test`)
2. Push `index.html` to the repo
3. Go to Settings → Pages → Enable from main branch
4. Wait 1-2 minutes for deployment
5. Your URL: `https://YOUR_USERNAME.github.io/naa-test/`

### 8. Sideload to Teams

1. Open Microsoft Teams desktop
2. Go to Apps → Manage your apps → Upload a custom app
3. Select your `manifest.zip`
4. Open the app

### 9. Test

1. Enter your Azure AD Client ID and Tenant ID in the app
2. Click "Initialize Teams SDK"
3. Click "Check NAA Support"
4. Click "Authenticate with NAA"

### 10. Test on iOS

1. Open Teams on your iPhone (same account)
2. Go to Apps → find "NAA Test"
3. Repeat the authentication test
4. Check if it works!

## Troubleshooting

- **"Not in Teams"**: Make sure you're running inside Teams, not in a browser
- **NAA not supported**: Your Teams version may be too old (need recent version)
- **Popup blocked**: Check Teams/browser popup settings
- **Invalid redirect**: Make sure Azure AD has the `brk-multihub://` redirect URI
