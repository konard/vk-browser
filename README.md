# VK Browser Bot - Long Polling Demo

A proof of concept VK bot that runs entirely in the browser using long polling to send and receive messages to yourself. Uses Kate Mobile for authentication and works perfectly with GitHub Pages.

## Live Demo

Access the live demo at: https://konard.github.io/vk-browser/

## Features

- **Kate Mobile Authentication** - Uses Kate Mobile app credentials for easy VK login
- **GitHub Pages Compatible** - Works with OAuth redirect to GitHub Pages URL
- **Pure Browser Implementation** - No server required
- **React.js Single-Page Application**
- **VK Long Polling** - Real-time message updates
- **JSONP API Calls** - Bypasses CORS restrictions
- **Self-Messaging** - Send and receive messages to yourself

## Setup for GitHub Pages

1. **Fork or Clone this Repository**
   ```bash
   git clone https://github.com/konard/vk-browser.git
   ```

2. **Enable GitHub Pages**
   - Go to Settings → Pages
   - Select "Deploy from a branch"
   - Choose "main" branch and "/ (root)" folder
   - Save

3. **Access Your Bot**
   - Navigate to https://konard.github.io/vk-browser/
   - Click "Login with Kate Mobile"
   - Authorize the app
   - Copy the entire URL from the blank page
   - Paste it back in the app (token will be extracted automatically) and click "Connect"

## How It Works

### Authentication Flow

1. User clicks "Login with Kate Mobile"
2. Redirects to VK OAuth page with Kate Mobile app ID
3. After authorization, VK redirects to blank.html with access token in URL
4. User copies the entire URL from their browser
5. User pastes the URL into the app (the token will be extracted automatically)
6. User clicks "Connect to VK" to start the bot

The app also saves your token in localStorage for convenience, so you don't need to re-authenticate each time.

### Technical Implementation

- **Kate Mobile App ID**: 2685278 (official Kate Mobile ID)
- **OAuth Scope**: messages, offline
- **API Version**: 5.131
- **Polling**: Uses periodic message checking (true long polling not available in browser due to CORS)

### Security

- Access token is only stored in browser memory
- Token is never sent to any third-party servers
- Uses official Kate Mobile app ID for trusted authentication

## Local Development

To run locally:

1. Open `index.html` in your browser
2. For OAuth redirect to work locally, you might need to use a local server:
   ```bash
   python -m http.server 8000
   # or
   npx http-server
   ```

## Browser Compatibility

Works in modern browsers:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## Limitations

- JSONP only supports GET requests
- VK API rate limits apply (3 requests/second)
- Some VK features may not be available through JSONP
- True long polling is not available in browser (uses periodic polling every 2 seconds instead)
- VK Long Poll servers don't support JSONP, limiting real-time capabilities

## License

This is free and unencumbered software released into the public domain under The Unlicense.
