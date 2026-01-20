# 📦 Automated WhatsApp Grocery Billing & Notification System

A lightweight, mobile-first system that enables grocery shop owners to **automatically generate monthly bills and send them to customers via WhatsApp Business**.

---

## 📖 Table of Contents

1. Introduction  
2. Problem Statement  
3. Proposed Solution  
4. Objectives  
5. Scope  
6. Target Users  
7. Functional Requirements  
8. Non-Functional Requirements  
9. System Architecture  
10. Software Development Life Cycle (SDLC)  
11. Use Case Diagram  
12. Use Case Descriptions  
13. Data Design  
14. Message Format  
15. Security Considerations  
16. Deployment Strategy  
17. Risk Analysis  
18. Future Enhancements  
19. Tools & Technologies  
20. Author  
21. License  

---

## 1️⃣ Introduction

The **Automated WhatsApp Grocery Billing & Notification System** is designed to help small grocery shop owners digitize monthly billing operations using **WhatsApp Business**.

The system calculates grocery bills, utility charges, and other expenses, then automatically sends a **professional bill message** to each customer.

---

## 2️⃣ Problem Statement

Small grocery shop owners face challenges such as:

- Manual bill calculation
- Paper-based customer records
- Missed or delayed payment reminders
- Communication gaps with customers
- Lack of technical resources

---

## 3️⃣ Proposed Solution

This system provides:

- Centralized customer billing data
- Automated monthly bill calculations
- WhatsApp-based bill delivery
- Minimal technical dependency
- Mobile-only usability

---

## 4️⃣ Objectives

- Automate monthly grocery billing
- Reduce manual errors
- Improve customer communication
- Ensure timely bill notifications
- Enable digital transformation for small shops

---

## 5️⃣ Scope

### Included
- Customer record management
- Monthly bill calculation
- WhatsApp message notifications

### Excluded
- Online payment processing
- Mobile application (future scope)

---

## 6️⃣ Target Users

- Grocery Shop Owners
- Kirana Store Owners
- Small Retail Businesses
- Non-technical users

---

## 7️⃣ Functional Requirements

| ID | Requirement |
|----|------------|
| FR-01 | Add, edit, delete customer records |
| FR-02 | Store monthly billing data |
| FR-03 | Calculate total monthly bill |
| FR-04 | Send bill via WhatsApp |
| FR-05 | Send payment reminders |

---

## 8️⃣ Non-Functional Requirements

- System must be simple to use
- Messages must be delivered reliably
- Customer data must remain confidential
- System should be scalable

---

## 9️⃣ System Architecture
```mermaid
erDiagram

    SHOP_OWNER {
        int owner_id PK
        string owner_name
        string mobile_number
        string shop_name
    }

    CUSTOMER {
        int customer_id PK
        string customer_name
        string customer_phone
    }

    PRODUCT {
        int product_id PK
        string product_name
        float unit_price
    }

    BILL {
        int bill_id PK
        date bill_date
        float total_amount
        int customer_id FK
        int owner_id FK
    }

    BILL_ITEM {
        int bill_item_id PK
        int bill_id FK
        int product_id FK
        int quantity
        float price
    }

    WHATSAPP_MESSAGE {
        int message_id PK
        int bill_id FK
        string phone_number
        string message_text
        string delivery_status
        datetime sent_time
    }

    GOOGLE_SHEET {
        int sheet_id
        string stored_customer_data
        string stored_bill_data
        datetime last_updated
    }

    SHOP_OWNER ||--o{ CUSTOMER : manages
    CUSTOMER ||--o{ BILL : receives
    SHOP_OWNER ||--o{ BILL : generates
    BILL ||--o{ BILL_ITEM : contains
    PRODUCT ||--o{ BILL_ITEM : includes
    BILL ||--|| WHATSAPP_MESSAGE : sends
    CUSTOMER ||--o{ GOOGLE_SHEET : stored_in
    BILL ||--o{ GOOGLE_SHEET : stored_in





---

## 🔁 10️⃣ Software Development Life Cycle (SDLC)

### 1. Requirement Analysis
- Identify billing needs
- Identify communication medium

### 2. System Design
- Data structure
- Message format
- Workflow design

### 3. Implementation
- Google Sheets setup
- WhatsApp Business configuration

### 4. Testing
- Bill accuracy testing
- Message delivery testing

### 5. Deployment
- Live usage by shop owner

### 6. Maintenance
- Monthly data updates
- Customer record updates

---

## 11️⃣ Use Case Diagram





🛒 ABC Grocery Store

Customer: Ali Khan
Billing Month: January 2026

🧾 Grocery Bill: Rs. 8,500
💡 Electricity Bill: Rs. 1,200
📦 Other Charges: Rs. 300

🔴 Total Payable: Rs. 10,000

Please pay before 10 January.
Thank you 🙏





---

## 15️⃣ Security Considerations

- Restricted access to billing data
- Customer privacy protection
- Use of WhatsApp Business only

---

## 16️⃣ Deployment Strategy

- Run using WhatsApp Business App
- Maintain billing data in Google Sheets
- Manual or scheduled monthly execution

---

## 17️⃣ Risk Analysis

| Risk | Mitigation |
|-----|------------|
| Data loss | Regular backups |
| Message failure | Manual resend option |
| Human error | Validation checks |

---

## 18️⃣ Future Enhancements

- WhatsApp Cloud API automation
- PDF invoice generation
- Payment gateway integration
- Admin dashboard
- Mobile application

---

## 19️⃣ Tools & Technologies

- WhatsApp Business
- Google Sheets
- Internet Connectivity

---

## 20️⃣ Author

**Muhammad Soman**  
Software Engineering Student  
Iqra University, Karachi  

---

## 21️⃣ License

This project is licensed for **educational and small business usage only**.

---

⭐ *This system enables small businesses to move toward digital automation using simple and accessible tools.*



