# AutoMate IP

A Bash script to automate changing your public IP address using the Tor network. This script installs Tor (and curl if needed), starts the Tor service, and periodically reloads Tor to obtain a new IP address. It can be used for privacy, testing, or bypassing IP-based restrictions.

## Features

- Installs Tor and curl automatically for most Linux distributions.
- Starts and manages the Tor service.
- Changes your public IP address at user-defined intervals.
- Displays your new IP address after each change.

## Installation

1. **Clone or Download the Script**

   Download or clone this repository to your Linux machine.

2. **Make the Script Executable**

   ```sh
   chmod +x setup.sh
   ```

3. **Run the Script as Root**

   The script must be run as root to install packages and manage services:

   ```sh
   sudo ./setup.sh
   ```

   > **Note:** The script will attempt to install `tor` and `curl` using your system's package manager. Supported distributions include Ubuntu, Debian, Fedora, CentOS, Red Hat, Amazon Linux, and Arch Linux.

## Usage

- When prompted, enter:
  - The time gap (in seconds) between IP changes (minimum 10 seconds recommended).
  - The number of times to change the IP (enter `0` for infinite changes).

- The script will reload the Tor service at the specified interval and display your new public IP address.

## Browser Network Configuration

To route your browser traffic through Tor (using the same Tor instance as the script):

1. **Set Your Browser's Proxy Settings:**
   - **SOCKS Host:** `127.0.0.1`
   - **Port:** `9050`
   - **SOCKS v5** (if prompted)

2. **Firefox Example:**
   - Go to `Settings` > `Network Settings` > `Manual proxy configuration`.
   - Enter the above SOCKS host and port.
   - Check "Proxy DNS when using SOCKS v5" for better privacy.

3. **Chrome Example:**
   - Start Chrome with the following command:
     ```sh
     google-chrome --proxy-server="socks5://127.0.0.1:9050"
     ```

## Warnings

- **Root Privileges:** The script must be run as root. Running as a normal user will result in an error.
- **Network Stability:** Changing IP too frequently may cause unstable connections or temporary bans from some services.
- **Tor Usage:** Some websites may block or restrict access from Tor exit nodes.
- **Privacy:** While Tor provides anonymity, it is not foolproof. Do not rely solely on Tor for critical privacy needs.
- **Legal:** Ensure your use of Tor and IP changing complies with local laws and the terms of service of the websites you access.

## Troubleshooting

- If Tor fails to start, check the service status:
  ```sh
  systemctl status tor.service
  ```
- If your browser does not connect, ensure the proxy settings are correct and Tor is running.

---

**Author:**  
Alosious Benny