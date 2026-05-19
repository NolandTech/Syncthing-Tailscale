# Syncthing + Tailscale for muOS
**v0.5.0**

## What is it?
**Syncthing + Tailscale** is an automated, battery-friendly synchronization engine for muOS. It seamlessly syncs your game saves and save states in the background using Syncthing, with Tailscale support so your handheld can sync anywhere in the world.

Instead of leaving Syncthing running constantly and draining your battery, this app does exactly what you need and then gets out of the way. Once you launch the app (or set it to run on boot), it automatically connects to the network, waits for your devices to sync to 100%, and then gracefully shuts down all services.

## Key Features
* **Fully Automated**: Turns on Wi-Fi, scans, syncs, and shuts itself down when finished.
* **Tailscale Integration**: Securely sync with your PC or server even when you are away from home.
* **Boot Support**: Can be configured to run silently in the background every time you turn on your device.
* **Smart Network Handling**: Automatically checks your Wi-Fi connection and safely navigates muOS network boot sequences.
* **Battery Saver**: Option to automatically turn off your handheld's Wi-Fi once the sync is complete.

## Installation & Setup
To get started, you will need to install the application and link it to your existing Syncthing setup by editing the configuration file.

> **Note:** If you want to use Tailscale with this app, you must already have it set up in muOS. This app only toggles Tailscale on and off for syncing.

### Step 1: Install the App
1. Download the `Syncthing + Tailscale.muxapp` file.
2. Place the file onto your SD card in the following directory: `SD Card -> ARCHIVE`.
3. Put the SD card back into your device and boot into muOS. (Can also access SD card via FTP/SFTP)
4. Navigate to **Applications -> Archive Manager** and select `Syncthing + Tailscale.muxapp` to install it. 

### Step 2: Locate the Config File
Plug your SD card into your PC (or access it via FTP/SFTP, or Dingux Commander found in Applications) and navigate to the newly created application directory: 
`SD Card -> MUOS -> application -> Syncthing + Tailscale -> config.txt`

*(Note: If you ever accidentally delete this file, don't worry. Simply launching the app on your muOS device will instantly generate a new blank config file for you.)*

### Step 3: Edit the Settings
Open `config.txt` in any basic text editor (like Notepad). You will see the following layout:

```bash
# === MUOS SYNCTHING + TAILSCALE CONFIG ===
# Open Syncthing in your Browser to find the API Key and Folder IDs.

API_KEY=""                            # API Key found in Syncthing Actions > Settings > General
Folder1_ID=""                         # Syncthing Folder ID
Folder2_ID=""                         # Syncthing Folder ID

# Options: Use "yes" or "no"
USE_TAILSCALE="no"                    # Use Tailscale tunnel to Sync 
WIFI_OFF="no"                         # Turn WiFi off after syncing is complete.
LAUNCH_AT_BOOT="no"                   # Run Sync on system boot.
```

## Configuration Guide
* **`API_KEY`**: You need your Syncthing API Key to allow the script to check your sync progress.
  * *How to find it:* Open the Syncthing Web GUI running from your handheld device, click **Actions** (top right) -> **Settings** -> **General** -> **API Key**. Copy and paste it between the quotes.
* **`Folder1_ID` & `Folder2_ID`**: These are the unique IDs for the folders you want to sync (typically your Saves and States folders).
  * *How to find it:* In the Syncthing Web GUI, click on the folder you want to sync, and look for the **Folder ID** (usually a string of letters and numbers with hyphens). Paste one ID into `Folder1_ID` and the other into `Folder2_ID`.
* **`USE_TAILSCALE`**: Set to `"yes"` if you want the app to start Tailscale before syncing. If you only sync locally on your home Wi-Fi, leave this as `"no"`.
* **`WIFI_OFF`**: Set to `"yes"` if you want the script to automatically disable your Wi-Fi after the sync reaches 100% to save battery.
* **`LAUNCH_AT_BOOT`**: Set to `"yes"` if you want the sync process to run automatically in the background every time you turn on your handheld.

### Step 4: Save and Sync!
Save your changes to `config.txt`, put the SD card back into your device, and run the app. You are all set!

*To change settings, you can edit the config file whenever you want and rerun the application to load the updated configuration.*



