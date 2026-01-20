

```md
# Automated WhatsApp Billing & Notification System for Grocery Shop

A professional, low-cost automation system that sends **monthly grocery and utility bill notifications to customers via WhatsApp**.  
Designed specifically for **small to medium grocery shops** using WhatsApp Business.

---

## 📌 Project Overview

Grocery shops often manage monthly billing manually, which leads to:
- Human errors
- Delayed payments
- Poor customer communication

This system automates **monthly WhatsApp billing reminders** using:
- Node.js
- WhatsApp Web automation
- Google Sheets as a lightweight database

---

## 🎯 Objectives

- Automate monthly billing notifications
- Reduce manual effort and calculation errors
- Improve customer communication
- Ensure WhatsApp-safe usage (no spam)
- Enable future scalability (API, dashboard, payments)

---

## 🗺️ Project Roadmap

### Phase 1 (Current – Core Automation)
⏱ Estimated Time: **2–4 weeks**

- WhatsApp Web automation
- Google Sheets data source
- Monthly scheduling using cron
- Local deployment (PC/Laptop)

### Phase 2 (Future – Professional Scale)
- WhatsApp Business API
- Admin dashboard (Web)
- Payment integration (JazzCash / EasyPaisa)
- Invoice PDF generation
- Cloud deployment

---

## 🧰 Technology Stack

### Phase 1 Stack

| Layer | Technology | Purpose |
|-----|-----------|--------|
| Backend | Node.js | Core logic & automation |
| WhatsApp | whatsapp-web.js | WhatsApp Web integration |
| Database | Google Sheets / JSON | Customer & billing data |
| Scheduler | node-cron | Monthly automation |
| Runtime | Local PC / Laptop | Always-on execution |
| Mobile | WhatsApp Business | QR authentication |

---

## 📚 Learning Path

Recommended learning order (1–2 days each):

1. **Node.js Basics**
   - Async / Await
   - Modules
   - File I/O  
   📖 freeCodeCamp Node.js

2. **whatsapp-web.js**
   - QR authentication
   - Client initialization
   - `client.sendMessage()`  
   📖 https://pinault.org/blog/whatsapp-web-js-a-comprehensive

3. **Google Sheets Integration**
   - `google-spreadsheet` package
   - Service account setup
   - Read/write rows  
   📖 https://blog.stephsmith.io/tutorial-google-sheets-api-node-js/

4. **node-cron**
   - Cron expressions
   - Monthly scheduling  
   📖 https://www.freecodecamp.org/news/schedule-a-job-in-node-with-nodecron/

5. **Best Practices**
   - Message delays (1–2 seconds)
   - One message per month
   - WhatsApp Business account usage

---

## 🧱 System Architecture

```

Google Sheets (Customer Data)
↓
Node.js Application
↓
node-cron (Monthly Trigger)
↓
whatsapp-web.js
↓
WhatsApp Business
↓
Customer

````

---

## 📊 Data Structure (Google Sheet)

| Column Name | Description |
|------------|------------|
| CustomerName | Customer full name |
| WhatsAppNumber | Phone number (92xxxxxxxxxx) |
| GroceryBill | Monthly grocery amount |
| ElectricBill | Monthly electricity amount |
| LastSent | Last message date |

---

## ✉️ Message Template

```text
Assalam-o-Alaikum {{CustomerName}},

🛒 Grocery Bill: Rs {{Grocery}}
💡 Electric Bill: Rs {{Electric}}
---------------------
💰 Total Bill: Rs {{Total}}

Kindly pay by due date.

Shukriya,
{{ShopName}}
````

---

## ⚙️ Step-by-Step Implementation

### 1️⃣ Project Setup

```bash
mkdir whatsapp-billing
cd whatsapp-billing
npm init -y
npm install whatsapp-web.js qrcode-terminal google-spreadsheet node-cron
```

---

### 2️⃣ Prepare Google Sheet

* Create a Google Sheet
* Add required columns
* Create Google Cloud **Service Account**
* Share sheet with service email

---

### 3️⃣ WhatsApp Client

* Initialize WhatsApp client
* Scan QR using WhatsApp Business
* Persist session to avoid re-login

---

### 4️⃣ Data Handling

* Read customers from Google Sheets
* Calculate total bill
* Validate phone numbers

---

### 5️⃣ Message Logic

* Generate message from template
* Send via `client.sendMessage()`
* Add delay between messages

---

### 6️⃣ Scheduler

```js
cron.schedule('0 10 1 * *', async () => {
  // Send monthly messages
});
```

🕙 Runs on **1st of every month at 10:00 AM**

---

### 7️⃣ Manual Testing

* Add manual trigger (CLI / flag)
* Send test message to admin number

---

## 🚀 Deployment & Maintenance

### Local Deployment

* Keep PC & internet ON
* Run using **PM2**

```bash
npm install -g pm2
pm2 start index.js
```

### Monitoring

* Check logs monthly
* Validate Google Sheet data
* Ensure WhatsApp session is active

---

## ⚠️ Risk Mitigation

| Risk           | Mitigation                |
| -------------- | ------------------------- |
| WhatsApp Ban   | 1 message/month, 2s delay |
| Data Errors    | Sheet validation & review |
| Downtime       | PM2 auto-restart          |
| Session Expiry | Persist session data      |

---

## 📈 Success Criteria

* 100% customers receive monthly messages
* Reduced manual billing work
* Improved on-time payments
* Zero WhatsApp policy violations

---

## 🔮 Future Enhancements

* WhatsApp Business API
* Admin dashboard
* Payment links
* Invoice PDF
* Cloud hosting

---

## 👨‍💻 Author

**Muhammad Soman**
Software Engineering Student
Automated WhatsApp Billing System – 2026

---

## 📜 License

This project is for **educational and small business use**.
Commercial use requires compliance with WhatsApp policies.

```


