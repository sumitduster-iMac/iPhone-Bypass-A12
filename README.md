# iPhone Bypass A12+

Open source iOS activation bypass tool for A12+ devices.

## Setup Guide

Initial Setup

Server Configuration:

Get your computer's network IP address

ipconfig getifaddr en1
ifconfig works too

Start the server (replace x.x.x.x with your actual IP)
cd server/
php -S x.x.x.x:8000 -t public

2. File Configuration:

Open downloads.28.png in a text editor

Find and replace all paths to badfile.plist with your server IP

Example: http://192.168.0.103:8000/badfile.plist

Activation Process (3 Stages)
Stage 1 - Initial Activation:

The generator program automatically sends downloads.28.sqlitedb

The device will reboot after this stage

Important: Periodically delete downloads.28.sqlitedb-shm and downloads.28.sqlitedb-val files in the downloads folder before reboot

Stage 2 - Metadata Transfer:

After first reboot, the server creates iTunesMetadata.plist

Manually copy this file to /var/mobile/Media/Books/ folder

Reboot iPhone - asset.epub will appear after this

Stage 3 - Data Population:

Server receives requests like: 192.168.0.105:52588 [200]: GET /firststp/8dc56bf27aa8b527/fixedfile

The asset.epub book gets populated with data from these requests

Do not stop the server until the process fully completes!

## Important Notes

**GUID for Generation:**

Get it manually from external sources or generate it programmatically.

**Critical Reminders:**

✅ Server must run continuously until the final reboot

✅ Don't interrupt the process after launching activator.py

✅ Monitor server logs to track progress

✅ Keep the server active throughout all stages


## Prerequisites

### Client-Side (macOS/Linux)

- Python 3.6+

- `libimobiledevice` (via Homebrew on macOS)

- `pymobiledevice3` (via pip)

- `curl`

### Server-Side

- PHP 7.4 or newer

- SQLite3 extension enabled

- Write permissions for cache directories


## Disclaimer

This tool is provided for educational and research purposes only. The authors are not responsible for any misuse of this software or damage to devices. Ensure you have authorization before performing operations on any device.
