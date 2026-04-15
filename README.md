# Adjust S2S Events API — GTM Server-Side Template

[![GTM Template](https://img.shields.io/badge/GTM-Server--Side-blue)](https://tagmanager.google.com/)
[![License](https://img.shields.io/badge/License-Apache%202.0-orange.svg)](LICENSE)

A custom Google Tag Manager (Server-Side) tag template that enables high-precision event tracking for the **Adjust S2S Events API**. This template sends mobile app events directly from your server to Adjust, bypassing client-side limitations and ensuring 100% attribution reliability.

---

## 🌟 Key Features

*   **100% Data Accuracy**: Direct server-to-server communication protects events from ad blockers, VPNs, and browser tracking restrictions.
*   **Zero Mobile Code Changes**: Manage and map new events entirely within the GTM interface without requiring an app store release.
*   **Built-in Hardware IDs**: Supports all critical identifiers (ADID, IDFA, IDFV, GPS ADID) for accurate multi-platform attribution.
*   **Revenue Tracking**: Comprehensive support for revenue events with dynamic currency and environment (Sandbox/Production) settings.
*   **Custom Parameters**: Share callback and partner parameters directly with your internal backend or ad platforms like Facebook and Google.

---

## 📖 Beginner's Guide: Setting Up Adjust S2S in GTM Server-Side

This guide will walk you through sending your app data to Adjust using our Google Tag Manager (GTM) template.

### Step 1: Add the Adjust Template
First, we need to add the Adjust "brain" to your GTM. You have two options:

#### Option A: The "App Store" Method (Gallery)
1.  Open your Server-Side GTM Container.
2.  Click **Templates** on the left menu.
3.  In the Tag Templates section, click **Search Gallery**.
4.  Search for "Adjust S2S Events" and click **Add to Workspace**.

#### Option B: The "Manual Download" Method (GitHub)
1.  **Download the File**: Go to our GitHub Releases Page and click on the `.tpl` file to download it to your computer.
<a href="https://github.com/Daam-Al-Arabia/adjust-s2s-gtm-template/blob/main/template.tpl" download>
  <img src="https://img.shields.io/badge/Download-Adjust%20GTM%20Template-blue?style=for-the-badge&logo=github" alt="Download Template">
</a>
2.  **Go to GTM**: Click **Templates** > **Tag Templates** > **New**.
3.  **Import**: Click the three vertical dots (⋮) in the top right corner and select **Import**.
4.  **Upload**: Select the `.tpl` file you just downloaded from your computer.
5.  **Save**: Click the blue **Save** button in the top right and close the editor.

### Step 2: Create Your Variables
Variables are like "shortcuts." Instead of typing long technical codes every time, we save them once.

1.  Click **Variables** on the left menu.
2.  Under **User-Defined Variables**, click **New**.
3.  Click **Variable Configuration** and choose **Event Data**.
4.  In the Key Path field, type: `x-ga-resettable_device_id`
5.  Name it `ED - Device ID` and click **Save**.
    *(Repeat this if you need others like x-ga-platform or currency.)*

### Step 3: Create the Adjust Tag
This is the "package" that sends your data to Adjust.

1.  Click **Tags** > **New**.
2.  Click **Tag Configuration** and select the **Adjust S2S** template you just added.
3.  **S2S Number**: Enter your version (e.g., 1).
4.  **App Token**: Paste your unique App Token from your Adjust Dashboard.
5.  **Event Mapping**: Click **Add Row**.
    *   Type your GTM event (e.g., `purchase`) on the left.
    *   Paste your Adjust Event Token on the right.
6.  **Device Identifiers**: Click the **+** icon next to the Device ID field and select the `ED - Device ID` variable you made in Step 2.

### Step 4: Set the Trigger (The "When")
1.  Click the **Triggering** box at the bottom of the tag.
2.  Click the **+** icon in the top right.
3.  Choose **Custom** as the trigger type.
4.  Set it to fire on **Some Events** where **Event Name** equals `purchase`.
5.  Name it `Trigger - Purchase` and click **Save**.

### Step 5: Test in Preview Mode
1.  Click the blue **Preview** button in the top right of GTM.
2.  Send a test event from your app.
3.  In the Preview window, click on your event in the left sidebar.
4.  Check if your Adjust Tag appears under **Tags Fired**.

### Step 6: Checking the Console for Success
Click the **Console** tab at the top of the Preview screen. This is where the tag tells you if it succeeded.

| Message | What it means | Action |
| :--- | :--- | :--- |
| `Status: 200` | Success! Data reached Adjust. | None! You are done. |
| `Status: 400/401` | Invalid Token. | Re-copy your App Token from Adjust. |
| `Error: Device ID missing` | Missing Identity. | Check if your app is sending the Device ID to GTM. |
| `Warning: IP missing` | Thin Data. | The event sent, but geolocation might be off. |

### Final Step
Once you see that **Status: 200**, click **Publish** in your main GTM workspace to make the changes live for all users!

---

## 📡 Device Identifiers & Attribution

For accurate event attribution, every S2S request must include at least one valid device identifier. If you are using the **Event Data** (Option 2) source for parameters, ensure these keys are present in your incoming signals.

| Key | Description |
| :--- | :--- |
| `adid` | **Adjust Device ID**: Adjust's unique internal identifier. Essential for matching device data when `idfa` is unavailable. |
| `idfa` | **Identifier for Advertisers**: Apple's primary identifier for iOS. Requires user consent via ATT. |
| `idfv` | **Identifier for Vendors**: Secondary identifier for iOS matching. |
| `gps_adid` | **Google Play Services ADID**: The primary identifier for Android devices. |
| `ip_address` | **IP Address**: Essential for probabilistic matching and geolocation accuracy. |
| `user_agent` | **User Agent**: Essential for device signaling and hardware identification. |

> [!TIP]
> For more information on identifier requirements, refer to the [Adjust S2S Events Documentation](https://dev.adjust.com/en/api/s2s-api/events/).

---

## 🛰️ Technical Details

*   **API Endpoint**: `https://s2s.adjust.com/event`
*   **Request Method**: `POST`
*   **Payload Format**: `application/x-www-form-urlencoded`
*   **Permissions Required**:
    *   `logging`: Enabled for debug mode logs.
    *   `read_event_data`: Access to specific device and event parameters.
    *   `send_http`: Restricted to Adjust's official S2S endpoint.

---


### 📚 Need More Details?
If you want to learn more about how Adjust processes these events or see a full list of available data fields, check out the official **Adjust S2S Events API Documentation**.

* **[Visit the Adjust S2S API Docs →](https://dev.adjust.com/en/api/s2s-api/events/)**
    * *Best for:* Understanding technical limits, checking currency codes, or troubleshooting specific server responses.


---

## 🤝 Support & Contribution

Developed and maintained by **Daam Al Arabia**.

*   **Website**: **[https://daam.com.sa/](https://daam.com.sa/)**

For bugs, feature requests, or custom implementation inquiries, please open an issue in this repository or contact us via our website.

---

## ⚖️ License
This project is licensed under the **Apache 2.0 License** - see the [LICENSE](LICENSE) file for details.
