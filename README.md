Since you want this in plaintext, I have removed the fancy formatting and HTML tags. You can copy and paste this directly into your `README.md` file on GitHub.

***

# Network-Wide Ad Blocking with Pi-hole

## Project Overview
This project documents the deployment of a Pi-hole instance on a Raspberry Pi. The objective was to create a DNS sinkhole that blocks advertisements and tracking domains for every device on the local network without requiring individual software installation on each client.

## Technical Stack
- Hardware: Raspberry Pi
- OS: Raspberry Pi OS
- Software: Pi-hole
- Protocol: SSH (Secure Shell)
- Networking: Static IP Assignment, DNS Routing

## Implementation Steps

Step 1: OS Installation & Initial Boot
- Used the Raspberry Pi Imager to flash the OS onto a microSD card.
- Configured custom settings (hostname, user credentials, and Wi-Fi/SSH) within the imager to allow for a headless setup.
- Inserted the SD card into the Raspberry Pi and initiated the boot sequence.

Step 2: Remote Access & Installation
- Established a remote terminal session via SSH from the host PC:
  ssh loganpranger@pihole
- Executed the automated Pi-hole installation script:
  curl -sSL https://install.pi-hole.net | bash
- Followed the interactive installer to configure the administrative password and basic preferences.

Step 3: Network Configuration
- Static IP Assignment: To prevent the DNS server from becoming unreachable due to DHCP lease changes, a static IP was assigned to the Raspberry Pi.
- Router Integration: Modified the DNS settings on the local router to point to the Pi-hole's static IP address. This ensures that all devices connecting to the router automatically use the Pi-hole for DNS resolution.

## How it Works
Pi-hole acts as a DNS server. When a device requests a domain, Pi-hole checks its blocklist. If the domain is flagged as an advertisement, Pi-hole returns a null response, preventing the ad from loading.

## Results
- Network-wide ad blocking: All devices (iOS, Android, Windows, Smart TVs) now have ad-blocking capabilities.
- Increased Privacy: Prevented telemetry and tracking domains from communicating with external servers.
- Improved Page Load Speeds: Reduced bandwidth consumption by blocking heavy ad scripts.
