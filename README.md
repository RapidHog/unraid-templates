# Unraid Community Application Templates

This repository contains Unraid Community Application templates.

## mamapi - MyAnonamouse Dynamic Seedbox IP Updater

The mamapi container automatically updates your MyAnonamouse (MAM) dynamic seedbox IP when using a VPN connection. This ensures continuous connectivity with the MAM tracker even when your VPN IP changes.

For features and detailed information, visit the [mamapi GitHub repository](https://github.com/elforkhead/mamapi).

### Setup Instructions

1. **Create a MAM Session:**
   - Go to your MAM Security preferences
   - Create a new session using your current VPN IP
   - Set "Locked session" to "ASN"
   - Set "Dynamic seedbox" to "Yes"
   - Copy the mam_id cookie immediately (viewing it again regenerates it!)
   - Add additional ASNs as needed through "Manage Session"

2. **Container Configuration:**
   - **MAM_ID**: Your session cookie from step 1 (required)
   - **Network**: For VPN users, set to your VPN container (e.g., `container:vpn_container_name`)
   - **Data Path**: Default `/mnt/user/appdata/mamapi`

3. **Advanced Options:**
   - **DEBUG**: Enable detailed logging
   - **NOTIFY_URLS**: Apprise URLs for error notifications
   - **SHUTDOWN_ON_DISCONNECT**: Exit on network loss (use with restart policy)

### Network Configuration for VPN Users

If using with a VPN container (recommended), change the network type:
- Network Type: `Container`
- Container: Select your VPN container (e.g., gluetun, binhex-qbittorrentvpn)

### Support

- [GitHub Repository](https://github.com/elforkhead/mamapi)
- [MAM Forum Thread](https://www.myanonamouse.net/f/t/992936)

### Contributing

To submit updates or new templates, please follow the [Unraid Community Applications guidelines](https://forums.unraid.net/topic/87144-ca-application-policies/).

## Repository Structure

```
unraid-templates/
├── templates/
│   ├── mamapi.xml
│   └── images/
│       └── mamapi.png
└── README.md
```
