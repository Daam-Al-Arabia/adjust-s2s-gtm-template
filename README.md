# Adjust S2S Events API — GTM Server-Side Template

[![GTM Template](https://img.shields.io/badge/GTM-Server--Side-blue)](https://tagmanager.google.com/)
[![License](https://img.shields.io/badge/License-Apache%202.0-orange.svg)](LICENSE)

A custom Google Tag Manager (Server-Side) tag template that enables high-precision event tracking for the **Adjust S2S Events API**. This template sends mobile app events directly from your server to Adjust, bypassing client-side limitations and ensuring 100% attribution reliability.

---

## 🌟 Key Features

*   **100% Data Accuracy**: Direct server-to-server communication protects events from ad blockers, VPNs, and browser tracking restrictions.
*   **Zero Mobile Code Changes**: Manage and map new events entirely within the GTM interface without requiring an app store release.
*   **Built-in Hardware IDs**: Supports all critical identifiers (IDFA, IDFV, GPS ADID) for accurate multi-platform attribution.
*   **Revenue Tracking**: Comprehensive support for revenue events with dynamic currency and environment (Sandbox/Production) settings.
*   **Custom Parameters**: Share callback and partner parameters directly with your internal backend or ad platforms like Facebook and Google.

---

## 🚀 Quick Setup Guide

### 1. Installation
Simply import the `template.tpl` into your Googe Tag Manager Server-Side container, or install it directly from the Community Template Gallery (search for "Adjust S2S Even ts API").

### 2. Basic Configuration
1.  Create a **New Tag** and select **Adjust S2S Events API**.
2.  Paste your **Adjust App Token** (12-character unique ID from your Adjust dashboard).
3.  Choose the appropriate **Environment** (Sandbox for testing, Production for live data).

### 3. Event Mapping
Use the **Event Token Mapping** table to link your incoming GTM event names to Adjust's event tokens:

| GTM Event Name | Adjust Event Token |
| :--- | :--- |
| `purchase` | `abc1234` |
| `registration` | `xyz9876` |

---

## 📡 Technical Details

*   **API Endpoint**: `https://s2s.adjust.com/event`
*   **Request Method**: `POST`
*   **Payload Format**: `application/x-www-form-urlencoded`
*   **Permissions Required**:
    *   `logging`: Enabled for debug mode logs.
    *   `read_event_data`: Access to specific device and event parameters.
    *   `send_http`: Restricted to Adjust's official S2S endpoint.

---

## 🤝 Support & Contribution

Developed and maintained by **Daam Al Arabia**.

*   **Website**: [https://daam.com.sa/](https://daam.com.sa/)
*   **Documentation**: [Tools Portal](https://daam.com.sa/tools/adjust-s2s-events-api/)

For bugs, feature requests, or custom implementation inquiries, please open an issue in this repository or contact us via our website.

---

## ⚖️ License
This project is licensed under the **Apache 2.0 License** - see the [LICENSE](LICENSE) file for details.
