# Laundry Reminder & Tracker

A simple web application to remind and track your laundry schedule. When you drop off your laundry, the app automatically creates a reminder to pick it up and syncs it with Google Calendar.

## Features

- ✅ "Drop Off Laundry" button to record new laundry with ID and location
- ⏰ Countdown timer for each active laundry
- ⚡ Configurable pickup duration (3 hours, 5 hours, or 24 hours)
- 🔄 Change pickup time for active laundry with calendar sync
- 📊 Statistics dashboard for active and completed laundry
- 👤 Google Sign-In integration
- 📅 Google Calendar integration with automatic sync
- 🌍 Multiple timezone support (System, UTC+7, UTC+8, UTC+0)
- 📜 Laundry history with pagination
- 💾 Local storage using localStorage
- 📱 Responsive design with Mazer template

## How to Use

### 1. Setup Google Calendar API

To enable Google Calendar synchronization:

1. Open [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable **Google Calendar API**:
   - In the sidebar, click "APIs & Services" > "Library"
   - Search for "Google Calendar API"
   - Click "Enable"

4. Create OAuth 2.0 Client ID:
   - Click "APIs & Services" > "Credentials"
   - Click "Create Credentials" > "OAuth client ID"
   - If prompted, configure OAuth consent screen first:
     - User Type: External
     - Add your email as test user
     - Scopes: Add `https://www.googleapis.com/auth/calendar.events`
   - Select "Web application"
   - Add Authorized JavaScript origins:
     - `http://localhost:5173` (for development)
     - `http://localhost:3000`
     - Your production URL
   - Copy the generated Client ID

5. Create API Key:
   - Click "Create Credentials" > "API Key"
   - Copy the generated API Key

6. **Create credentials folder and configuration file**:
   - Create a folder named `credentials` in the project root
   - Create a file `credentials/google_calendar_key` (no extension)
   - Add the following content:
     ```javascript
     const CLIENT_ID = 'YOUR_CLIENT_ID.apps.googleusercontent.com';
     const API_KEY = 'YOUR_API_KEY';
     ```
   - Replace `YOUR_CLIENT_ID` and `YOUR_API_KEY` with your credentials from step 4 and 5

   **Note**: The `credentials` folder is already in `.gitignore` to prevent accidentally committing sensitive credentials.

### 2. Running the Application

#### Option 1: Using NPM (Development)

```bash
# Install dependencies
npm install

# Run development server
npm run dev
```

The application will run at `http://localhost:5173`

#### Option 2: Using Live Server

Open the `index.html` file using Live Server extension in VS Code or any other web server.

#### Option 3: Direct Browser Access

You can directly open `index.html` in a browser, but Google Calendar features may not work due to CORS policy.

### 3. Using the Application

1. **Sign In**: Click "Sign in with Google" to enable Google Calendar sync features
2. **Drop Off Laundry**:
   - Click the "Taruh Laundry" button on the dashboard
   - Enter Laundry ID and Location
   - Laundry will automatically sync to Google Calendar if signed in
3. **Change Pickup Time**:
   - Use the duration buttons (3 Hours, 5 Hours, 24 Hours) on active laundry cards
   - Calendar event will automatically update if synced
4. **Monitor Countdown**: View the countdown timer for each active laundry
5. **Sync Calendar Manually**:
   - Click on your profile picture/name in the top right
   - Select "Sync Calendar" from the dropdown
6. **Mark as Complete**: Click the "Selesai" button when you've picked up your laundry
7. **View History**:
   - Scroll down to see the history of completed laundry
   - Click on any row to see detailed information
   - Use pagination buttons to navigate through history
8. **Change Timezone**:
   - Click on your profile in the top right
   - Select your preferred timezone (System, UTC+7, UTC+8, UTC+0)
9. **Sign Out**:
   - Click on your profile and select "Sign out"
   - Completed laundry data will be cleared on sign out

## Project Structure

```
Laundry-Reminder-and-Tracker/
├── src/
│   ├── index.html                    # Main application file
│   └── config/
│       └── laundry-config.json       # Pickup duration configuration
├── credentials/                      # Google API credentials (gitignored)
│   └── google_calendar_key           # Client ID and API Key
├── assets/                           # Assets from Mazer template
│   ├── compiled/                    # Compiled CSS and JS
│   ├── extensions/                  # Extension libraries
│   └── static/                      # Static assets
├── layouts/                         # Layout templates
├── partials/                        # Partial components
├── package.json                     # NPM dependencies
├── vite.config.js                   # Vite configuration
└── README.md                        # This documentation
```

## Technologies

- **UI Template**: [Mazer](https://github.com/zuramai/mazer) by zuramai
- **Build Tool**: Vite 5.0.2
- **Google Calendar API**: For calendar synchronization
- **Google Sign-In**: OAuth 2.0 authentication
- **localStorage**: For local data storage
- **Vanilla JavaScript**: Pure JavaScript with ES6 modules
- **Bootstrap 5.3.0**: UI components and styling

## Troubleshooting

### Google Sign-In not working

- Make sure you have created the `credentials` folder and `google_calendar_key` file
- Verify Client ID and API Key are correctly set in the credentials file
- Ensure Authorized JavaScript origins have been added in Google Cloud Console
- Make sure the application is running through a web server (not directly opening the HTML file)
- Check OAuth consent screen has your email as a test user

### Google Calendar not syncing

- Sign in with Google first by clicking "Sign in with Google"
- Click on your profile and select "Sync Calendar" to authorize calendar access
- Check the browser console for error messages
- Ensure the Google Calendar API is enabled in Google Cloud Console
- Verify the OAuth scope `https://www.googleapis.com/auth/calendar.events` is configured

### Duration buttons not updating calendar

- Make sure the laundry item has been synced to calendar first
- If not synced, click "Sync Calendar" from your profile dropdown
- Check browser console for detailed error messages
- Verify you're still signed in (token may have expired)

### Data lost after refresh

- Data is stored in the browser's localStorage
- Don't clear browser cache/cookies
- Data will be lost if opened in a different browser
- Completed data is cleared when signing out (by design)

### Pickup duration configuration

- Pickup duration options can be customized in `src/config/laundry-config.json`
- Modify the `pickupDurations` array to add/remove/change duration options
- Each duration must have: `label`, `hours`, and `buttonClass` properties

## License

Uses the [Mazer](https://github.com/zuramai/mazer) template which is open source.

## Credits

- UI Template: [Mazer](https://github.com/zuramai/mazer) by [@zuramai](https://github.com/zuramai)
- Icons: Bootstrap Icons
- Google Calendar API

## Contributing

Feel free to create pull requests or issues if you find bugs or have suggestions for improvements!

---

Made with ❤️ to make laundry tracking easier
