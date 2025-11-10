# 💊 Pharmacy Stock Assistant — n8n Automation

An automated **pharmacy inventory monitoring system** built with [n8n](https://n8n.io/).  
This workflow automatically checks a Google Sheet for **low-stock**, **expired**, and **soon-to-expire** medicines, then sends **email alerts via Gmail** — ensuring no shortage or unsafe medicine reaches patients.

---

## 🚀 Features

✅ **Automated Stock Monitoring**  
Runs on a schedule (daily or weekly) to fetch live inventory data from Google Sheets.

✅ **Low Stock Alerts**  
Detects medicines whose current stock falls below the minimum threshold and notifies the pharmacy team instantly.

✅ **Expired Item Detection**  
Flags and reports items past their expiry date for immediate removal.

✅ **Upcoming Expiry Warning** *(Proactive)*  
Alerts for items expiring within the next 30 days to help prevent wastage.

✅ **Email Notifications (Gmail)**  
Sends plain-text alerts for each issue directly to your inbox.

✅ **Scalable and Customizable**  
Easily extend the automation to send summary reports, log actions, or integrate with Slack, Telegram, or WhatsApp.

---

## 🧩 Workflow Overview

[Schedule Trigger]
↓
[Fetch Inventory Data (Google Sheets)]
↓
┌────────────────────────────┬────────────────────────────┬────────────────────────────┐
│ │ │
[Check Low Stock] [Check Expired Items] [Check Upcoming Expiry]
│ │ │
[Send Low Stock Alert] [Send Expired Item Alert] [Send Upcoming Expiry Alert]


---

## 📊 Google Sheet Structure

| Item Name | Batch No | Current Stock | Min Stock | Expiry Date | Pharmacist Name |
|------------|-----------|----------------|------------|--------------|-----------------|
| Paracetamol 500mg | B1234 | 20 | 50 | 2025-12-01 | Dr. Yohannes |
| Amoxicillin 250mg | A4567 | 10 | 15 | 2025-11-20 | Dr. Yohannes |

- **Item Name** → Medicine name  
- **Batch No** → Manufacturer batch identifier *(optional)*  
- **Current Stock** → Current available units  
- **Min Stock** → Minimum threshold before alert  
- **Expiry Date** → In `YYYY-MM-DD` format  
- **Pharmacist Name** → Used in alert messages  

---

## ⚙️ Gmail Alert Templates

### 🔸 Low Stock Alert

**Subject:**


⚠️ Low Stock Alert: {{ $json["Item Name"] }}


**Body:**


Hello {{ $json["Pharmacist Name"] || "Team" }},

The following item is running low in stock:

Item: {{ $json["Item Name"] }}
Current Stock: {{ $json["Current Stock"] }}
Minimum Required Stock: {{ $json["Min Stock"] }}

Please restock this item as soon as possible to avoid shortages.

Best regards,
Pharmacy Stock Assistant


---

### 🔸 Expired Item Alert

**Subject:**


🚨 Expired Item Detected: {{ $json["Item Name"] }}


**Body:**


Hello {{ $json["Pharmacist Name"] || "Team" }},

The following item has expired:

Item: {{ $json["Item Name"] }}
Expiry Date: {{ $json["Expiry Date"] }}
Batch Number: {{ $json["Batch No"] || "N/A" }}

Please remove this item from circulation immediately to ensure patient safety.

Regards,
Pharmacy Stock Assistant


---

### 🔸 Upcoming Expiry Alert

**Subject:**


⚠️ Upcoming Expiry Alert: {{ $json["Item Name"] }}


**Body:**


Hello {{ $json["Pharmacist Name"] || "Team" }},

Please note that the following item will expire soon:

Item: {{ $json["Item Name"] }}
Expiry Date: {{ $json["Expiry Date"] }}
Days Remaining: {{ Math.ceil((new Date($json["Expiry Date"]) - new Date()) / (1000 * 60 * 60 * 24)) }}

Kindly prioritize dispensing or returning this item before the expiry date to prevent losses.

Best regards,
Pharmacy Stock Assistant


---

## 🛠️ Setup Instructions

1. **Clone or Import Workflow**
   - Export your n8n workflow JSON and import it into your instance.
   - Alternatively, recreate it using the structure above.

2. **Connect Google Sheets**
   - Create a new Google Sheet matching the column structure.
   - Add your credentials in the “Google Sheets” node.

3. **Connect Gmail**
   - Add your Gmail account in the “Send Email” nodes.
   - Customize sender name and recipient email.

4. **Configure Schedule**
   - Edit the Schedule Trigger to run daily or weekly.

5. **Test the Workflow**
   - Click “Execute Workflow” in n8n to verify alerts are sent correctly.

---

## 🧠 Future Improvements

- 📧 Daily summary email (consolidated low stock + expiry report)  
- 🧾 Automatic “Restock Needed” list in Google Sheets  
- 🔔 Slack/Telegram integration for instant notifications  
- 📅 Dashboard or Notion sync for visual inventory tracking  

---

## 👨‍💻 Author

**Yohannes T.**  
Pharmacy Stock Automation Developer  
Built using [n8n](https://n8n.io/) + Google Sheets + Gmail  
🔗 Portfolio-ready project for automation, healthcare, and inventory systems.

---

## 🧾 License

This project is licensed under the MIT License — free to use and modify with attribution.

---


