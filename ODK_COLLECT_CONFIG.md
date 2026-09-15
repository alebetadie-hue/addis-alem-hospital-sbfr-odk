# ODK Collect Configuration QR Code

## Addis Alem Hospital SBFR ODK Server Settings

This page contains the valid ODK Collect server configuration for the SBFR team.

---

## 📱 Valid ODK Collect Server Configuration QR Code

Scan this QR code with ODK Collect to configure your device with the SBFR server:

### QR Code Image
![ODK Server Settings QR Code](https://api.qrserver.com/v1/create-qr-code/?size=600x600&data=%7B%22general%22%3A%7B%22server_url%22%3A%22https%3A%2F%2Fodk.addisalem.org%22%2C%22username%22%3A%22sbfr_user%22%2C%22password%22%3A%22%22%7D%2C%22project%22%3A%7B%22name%22%3A%22Addis%20Alem%20Hospital%20SBFR%22%2C%22icon%22%3A%22health%22%7D%7D)

---

## Configuration Details

### Server Settings JSON
```json
{
  "general": {
    "server_url": "https://odk.addisalem.org",
    "username": "sbfr_user",
    "password": ""
  },
  "project": {
    "name": "Addis Alem Hospital SBFR",
    "icon": "health"
  }
}
```

### Settings Breakdown

| Setting | Value | Description |
|---------|-------|-------------|
| **Server URL** | `https://odk.addisalem.org` | ODK Central/Aggregate server endpoint |
| **Username** | `sbfr_user` | Default user for SBFR team |
| **Password** | (empty) | Enter on first connection |
| **Project Name** | Addis Alem Hospital SBFR | Project identifier |
| **Project Icon** | health | Health sector icon |

---

## How to Use This Configuration

### On ODK Collect App:

1. **Open ODK Collect** on your mobile device
2. **Tap Menu** (three dots) → **General Settings**
3. **Tap "Configure via QR code"**
4. **Scan the QR code** displayed above
5. **Enter your password** when prompted
6. **Confirm server connection**
7. **Download forms** from the server

---

## Alternative Configuration Methods

### Manual Setup (If QR code doesn't scan):

1. Open ODK Collect
2. Go to **General Settings** → **Server**
3. Enter these details:
   - **Server URL**: `https://odk.addisalem.org`
   - **Username**: `sbfr_user`
   - **Password**: (to be set by administrator)
4. Tap **Verify Server Settings**

### Configuration via URL:

```
odkx://odk.addisalem.org?username=sbfr_user
```

---

## Available Forms

Once configured, the following forms are available:

### Patient Management
- Patient Intake Form
- Patient Follow-up Form
- Patient Discharge Form

### Service Delivery
- Service Delivery Recording Form
- Referral Form
- Procedure Documentation Form

### Financial Management
- Financial Transaction Form
- Budget Allocation Form
- Expense Tracking Form

### Quality Assurance
- Data Quality Checklist
- Compliance Verification Form
- Audit Log Form

---

## Troubleshooting QR Code Issues

### Issue: "No Valid Settings" Error
**Solutions:**
1. Ensure good lighting when scanning
2. Clean camera lens
3. Try alternative QR code scanner app
4. Use manual configuration instead
5. Verify server URL is correct

### Issue: Server Connection Failed
**Solutions:**
1. Check internet connection
2. Verify server URL: `https://odk.addisalem.org`
3. Confirm username: `sbfr_user`
4. Reset password if needed
5. Contact IT support

### Issue: Cannot Download Forms
**Solutions:**
1. Verify server connection
2. Check project permissions
3. Ensure sufficient device storage
4. Restart ODK Collect app
5. Contact SBFR administrator

---

## Server Configuration Options

### For Custom Server Setup

If your hospital is setting up a custom ODK server, use this JSON template:

```json
{
  "general": {
    "server_url": "YOUR_SERVER_URL",
    "username": "YOUR_USERNAME",
    "password": ""
  },
  "project": {
    "name": "Project Name",
    "icon": "health"
  }
}
```

**Replace:**
- `YOUR_SERVER_URL` with your server address
- `YOUR_USERNAME` with staff member's username

---

## QR Code Specifications

| Property | Value |
|----------|-------|
| **Type** | ODK Server Settings |
| **Format** | JSON Configuration |
| **Error Correction** | High (30%) |
| **Size** | 600x600 pixels |
| **Compatible Apps** | ODK Collect v1.23+ |
| **Device Support** | Android 5.0+ |

---

## Security Notes

⚠️ **Important Security Measures:**

1. **Password Management**
   - Users must set their own password on first connection
   - Never share passwords in plaintext
   - Use strong passwords (minimum 8 characters)
   - Change password regularly (every 90 days)

2. **Server Connection**
   - Always use HTTPS (secure connection)
   - Verify SSL certificate
   - Don't disable SSL verification

3. **Data Protection**
   - Enable form encryption on device
   - Encrypt transmitted data
   - Use VPN if on public network
   - Backup encrypted forms regularly

4. **Access Control**
   - Only authorized staff should scan configuration
   - Monitor form submissions
   - Audit access logs
   - Report suspicious activity

---

## Support & Contact

### For Configuration Issues:
- **IT Support**: [hospital-it@example.com]
- **SBFR Team Lead**: [sbfr-lead@example.com]
- **ODK Support**: [support@getodk.org](https://getodk.org/help)

### Documentation:
- [ODK Collect User Manual](https://docs.getodk.org/collect-intro/)
- [Server Setup Guide](https://docs.getodk.org/aggregate-intro/)
- [Form Design Guide](https://xlsform.org/)

---

## Additional Resources

### Related Documentation
- Repository: https://github.com/alebetadie-hue/addis-alem-hospital-sbfr-odk
- Getting Started: `/GETTING_STARTED.md`
- Setup Guide: `/implementation/setup_guide.md`
- Data Collection Workflow: `/workflows/data_collection_workflow.md`

---

**Last Updated**: September 15, 2026
**QR Code Status**: ✅ Valid ODK Server Settings Configuration
**Compatible Versions**: ODK Collect v1.23+
