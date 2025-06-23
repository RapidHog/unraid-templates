# Testing Unraid Community Apps Template

## Prerequisites
1. Access to an Unraid server (6.0+ recommended)
2. Community Applications plugin installed
3. GitHub account with 2FA enabled

## Testing Steps

### 1. Local Testing (Before Submission)

#### A. Test Template Installation

**Method 1: Private CA Template (Recommended for Testing)**
1. SSH into your Unraid server
2. Create the private apps directory:
   ```bash
   mkdir -p /boot/config/plugins/community.applications/private/gklassy/
   ```
3. Copy your template XML to this directory:
   ```bash
   cp /path/to/mamapi.xml /boot/config/plugins/community.applications/private/gklassy/
   ```
4. In Unraid, go to **Apps** tab
5. Search for "mamapi" - it will appear in the results
6. Install and test from your private template

**Method 2: Docker Manual Installation**
1. In Unraid, go to **Docker** tab
2. Click **Add Container**
3. Fill in Repository: `elforkhead/mamapi:latest`
4. Manually configure all settings from your template

**Method 3: Direct Docker Hub Search**
1. In Unraid, go to **Apps** tab
2. Search for "elforkhead/mamapi" or just "mamapi"
3. If your Docker image is public on Docker Hub, it will appear
4. Install and configure (note: this won't use your custom template)

#### B. Validate Template Format
- Ensure all required fields are present:
  - `Name`: mamapi
  - `Repository`: elforkhead/mamapi:latest
  - `Support`: GitHub link
  - `Overview`: Clear description
  - `Icon`: Accessible PNG image
  - `Category`: Properly formatted

#### C. Test Container Functionality
1. Create a test MAM session ID (use a dummy value for testing)
2. Configure the container with your network settings
3. Verify the container starts without errors
4. Check logs for proper initialization

### 2. Repository Testing

#### A. GitHub Repository Setup
Your repository structure should be:
```
unraid-templates/
├── templates/
│   ├── mamapi.xml
│   └── images/
│       └── mamapi.png
└── README.md
```

#### B. Raw File Access Test
Verify these URLs are accessible:
- Template: https://raw.githubusercontent.com/gklassy/unraid-templates/main/templates/mamapi.xml
- Icon: https://raw.githubusercontent.com/gklassy/unraid-templates/main/templates/images/mamapi.png

### 3. Community Apps Submission

#### A. Before Submitting
- [ ] GitHub 2FA is enabled
- [ ] Template validates against CA requirements
- [ ] No security violations (no bash commands in template)
- [ ] Icon is 100x100 to 256x256 PNG
- [ ] Description is family-friendly
- [ ] Support link works

#### B. Submit to Community Apps
1. Go to: https://www.myanonamouse.net/f/t/992936 (referenced form)
2. Fill out the submission form with:
   - GitHub repository URL
   - Contact preference
   - Brief description

#### C. Post-Submission Testing
After 48 hours:
1. Check **Apps > Statistics > Repositories** for your repository
2. If not appearing, check:
   - **Statistics > Template Errors**
   - **Statistics > Invalid Templates**

### 4. Network Configuration Testing

For VPN users (common use case):
1. Test with bridge network mode
2. Test with custom network (container:vpn_name)
3. Verify IP detection works correctly

### 5. Common Issues to Test

- [ ] MAM_ID environment variable is properly masked
- [ ] Data directory persists between container restarts
- [ ] Debug mode toggles correctly
- [ ] Container handles rate limiting gracefully
- [ ] Timezone setting works

## Validation Checklist

Before considering the template ready:
- [ ] Container installs without errors
- [ ] All environment variables are configurable
- [ ] Paths are correct for Unraid (/mnt/user/appdata/)
- [ ] Icon displays properly in CA
- [ ] Support links are functional
- [ ] No hardcoded values that should be variables

## Notes
- The container should work with both direct connections and VPN setups
- ASN lock should be set to "Yes" in MAM settings
- Dynamic seedbox should be set to "Yes" 
- The MAM_ID regenerates each time it's viewed - users should be warned
