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

