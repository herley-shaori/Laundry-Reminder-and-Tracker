# Laundry Reminder & Tracker

A simple web application to remind and track your laundry schedule. When you drop off your laundry, the app automatically creates a reminder to pick it up 24 hours later and syncs it with Google Calendar.

## Features

- ✅ "Drop Off Laundry" button to record new laundry
- ⏰ 24-hour countdown timer for each laundry
- 📊 Statistics dashboard for active and completed laundry
- 📅 Google Calendar integration
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

4. Create credentials:
   - Click "APIs & Services" > "Credentials"
   - Click "Create Credentials" > "API Key"
   - Copy the generated API Key

5. Create OAuth 2.0 Client ID:
   - Click "Create Credentials" > "OAuth client ID"
   - Select "Web application"
   - Add Authorized JavaScript origins:
     - `http://localhost:5173` (for development)
     - `http://localhost:3000`
     - Your production URL
   - Copy the generated Client ID

6. Edit the `index.html` file and replace:
   ```javascript
   const CLIENT_ID = 'YOUR_CLIENT_ID.apps.googleusercontent.com';
   const API_KEY = 'YOUR_API_KEY';
   ```
   With your Client ID and API Key.

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

1. **Drop Off Laundry**: Click the large "Taruh Laundry" button on the dashboard
2. **Monitor Countdown**: View the countdown timer for each active laundry
3. **Sync with Google Calendar**: Click the red Google button in the bottom-right corner to synchronize
4. **Mark as Complete**: Click the "Selesai" button when you've picked up your laundry
5. **View History**: Scroll down to see the history of completed laundry

## Project Structure

```
Laundry-Reminder-and-Tracker/
├── index.html              # Main application file
├── assets/                 # Assets from Mazer template
│   ├── compiled/          # Compiled CSS and JS
│   ├── extensions/        # Extension libraries
│   └── static/            # Static assets
├── layouts/               # Layout templates
├── partials/              # Partial components
├── package.json           # NPM dependencies
└── README.md             # This documentation
```

## Technologies

- **UI Template**: [Mazer](https://github.com/zuramai/mazer) by zuramai
- **Google Calendar API**: For calendar synchronization
- **localStorage**: For local data storage
- **Vanilla JavaScript**: Pure JavaScript without frameworks

## Troubleshooting

### Google Calendar not syncing

- Make sure you have set up the Client ID and API Key correctly
- Ensure Authorized JavaScript origins have been added in Google Cloud Console
- Make sure the application is running through a web server (not directly opening the HTML file)
- Check the browser console for error messages

### Data lost after refresh

- Data is stored in the browser's localStorage
- Don't clear browser cache/cookies
- Data will be lost if opened in a different browser

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
