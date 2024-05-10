[中文](README.md)

# Schengen Chrome Extension

## Usage Steps

1. Download the latest version of the Chrome extension from [this link](https://github.com/visa-lol/schengen-chrome-extension/releases) and load it into your Chrome browser.
2. Visit our website at [vis.lol](https://vis.lol/) and submit a request. A token will be automatically created and sent to you via email.
3. Enter the received token into the Chrome extension and click "Start." The program will operate automatically, no manual intervention needed.
4. Ensure your computer remains powered on.
5. (Optional) If concerned about CAPTCHAs like those from Cloudflare affecting your scheduling, consider installing the [nopecha Chrome extension](https://nopecha.com/chrome) to bypass these automatically.

## Program Operation

### Client-side (Chrome extension):
- Maintains online status by regularly refreshing the pages that won't be suspended, allowing immediate slot booking when available.
- Receives and executes server-side commands:
  1. Retrieves slots and sends them to the server (every 10 minutes depending on online user count).
  2. Books slots and forwards confirmation to the server.

### Server-side:
- Intelligently schedules clients to fetch slots based on the number of online users.
- Processes received slots to match user requirements and initiates booking commands.
- Sends email notifications to users on successful bookings, prompting quick payment as slots expire after an hour.

## Analysis

Depending on active clients:
- 60 clients: Fetches slots every 10 seconds.
- 300 clients: Fetches slots every 2 seconds.
- 600 clients: Fetches slots every second.
- 900 clients: Fetches slots every second but at 15-minute intervals per client.

Excessive refreshing can lead to account bans; hence the server's role in scheduling is crucial to avoid this.

## How Can Users Contribute?

### Promotion
Spread the word through various channels such as social media to increase the project's visibility and reduce scalper influence.

### Donations
Support is welcome to help with ongoing maintenance and server costs, particularly if the project adds value or aids in combatting scalpers.
