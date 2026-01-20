

---

# 🛠 How the System Works – Step by Step

---

## 1️⃣ Shop Owner Creates Bill (Frontend)

**What happens:**

* Shop owner opens the web app (React.js / Next.js).
* Adds a new customer or selects an existing customer.
* Adds products purchased, quantity, and price.
* Frontend calculates total in real-time (JavaScript logic).
* Shop owner clicks “Generate Bill”.

**Technologies involved:**

* **Frontend:** HTML, CSS, JS, React, Tailwind
* **Frontend logic:** Calculating totals using JS
* **API call:** Send bill data to backend (Axios / Fetch)

---

## 2️⃣ Backend Receives Bill Data

**What happens:**

* Backend (Node.js + Express.js) receives the bill data via API.
* Validates input (Joi / Zod).
* Checks if the customer exists in the database.
* Creates a new bill record in the database (MySQL / PostgreSQL).

**Technologies involved:**

* Node.js + Express.js
* REST API endpoints (POST /bill, GET /bill)
* Validation: Joi / Zod
* Database: MySQL / PostgreSQL

---

## 3️⃣ Bill and Bill Items Stored in Database

**What happens:**

* Bill details saved in **BILL table**.
* Each purchased product saved as **BILL_ITEM** (with quantity, price, total).
* Links to **Customer** and **ShopOwner** using foreign keys.

**Technologies involved:**

* SQL Tables: BILL, BILL_ITEM, CUSTOMER, PRODUCT, SHOP_OWNER
* ORM (optional): Prisma / Sequelize
* Foreign Key relationships from ERD

---

## 4️⃣ Google Sheets Backup (Optional but Recommended)

**What happens:**

* Backend sends a copy of bill + customer data to **Google Sheets** using API.
* Creates a log for reporting and backup.
* Ensures even if database fails, the data is accessible.

**Technologies involved:**

* Google Sheets API (Node.js)
* Service account authentication
* JSON → Sheet rows mapping

---

## 5️⃣ WhatsApp Notification Sent

**What happens:**

* Backend generates a **WhatsApp message** using bill info.
* Sends it to the customer’s phone using WhatsApp Business API.
* Stores delivery status in **WHATSAPP_MESSAGE table**.

**Example Message:**

```
Hello Ali, your bill #123
Items:
- Product A x2 = $50
- Product B x1 = $30
Total = $80
Thank you for shopping with us!
```

**Technologies involved:**

* WhatsApp Business API (Twilio or Meta Cloud API)
* Node.js service triggers API call
* Stores status in database

---

## 6️⃣ Customer Receives Bill

**What happens:**

* Customer receives WhatsApp message instantly.
* Can check the bill details.
* Optionally, data stored in Google Sheets or Database for future reference.

---

## 7️⃣ Optional: Reporting & Analytics

* Shop owner can view past bills.
* Filter by customer, date, or total amount.
* Google Sheets can generate simple reports.

**Technologies involved:**

* Frontend tables & filters
* Backend queries (SQL)
* Google Sheets as reporting dashboard

---

# 🔗 Full Flow Diagram (Simplified)

```
[Shop Owner UI] ---> [Frontend Logic (React.js)] ---> [Backend API (Node.js/Express)]
          |                                     |
          v                                     v
    [Bill Calculation]                   [Database: MySQL/PostgreSQL]
          |                                     |
          v                                     v
   [WhatsApp Notification] <--- [Google Sheets Backup]
          |
          v
     [Customer receives bill]
```

---

# ✅ How Each Stack Part Works Together

| Layer                       | Role in Flow                                         |
| --------------------------- | ---------------------------------------------------- |
| Frontend (React, JS)        | Captures input, calculates totals, displays UI       |
| Backend (Node, Express)     | Validates input, creates bill, triggers WhatsApp API |
| Database (MySQL/PostgreSQL) | Stores all records (bill, customer, products)        |
| Google Sheets API           | Backup + reporting                                   |
| WhatsApp API                | Sends bill messages to customer                      |

---

💡 **Important Note:**

* **Frontend calculates totals first**, then backend **confirms totals and stores data**.
* **Google Sheets is optional**, but good for backup and simple analytics.
* **WhatsApp message is triggered automatically** by backend after bill is saved.

---


