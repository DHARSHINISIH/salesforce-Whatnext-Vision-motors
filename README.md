# 🚗 WhatNext Vision Motors – Salesforce CRM

### Shaping the Future of Mobility with Innovation and Excellence

A Salesforce CRM solution designed for an automotive dealership to manage **vehicles, customers, dealers, vehicle orders, test drives, and service requests** in a centralized platform.

---

## 📌 Project Overview

**WhatNext Vision Motors** is a customized **Salesforce CRM application** developed to simplify and automate the major operations of an automotive dealership.

The system provides a centralized platform where dealership users can manage vehicle inventory, customer information, dealers, vehicle purchases, test-drive appointments, and service requests.

The project combines Salesforce's **declarative tools** such as Flows and Validation Rules with **programmatic development** using Apex and Triggers.

The main goal is to reduce manual work, improve data accuracy, prevent invalid vehicle orders, and provide better visibility into dealership operations.

---

## 🎯 Objectives

* Centralize dealership-related information in Salesforce.
* Manage vehicle inventory and availability.
* Maintain customer and dealer information.
* Manage vehicle purchase orders.
* Prevent orders for unavailable vehicles.
* Automate dealer assignment.
* Automate test-drive reminder notifications.
* Manage vehicle service requests.
* Maintain data accuracy using Validation Rules and Apex.
* Provide business insights using Reports and Dashboards.
* Implement secure and controlled access to Salesforce data.

---

## 🏗️ Main Modules

### 🚘 1. Vehicle Management

The Vehicle module manages the vehicles available in the dealership.

It stores information such as:

* Vehicle Model
* Vehicle Type
* Price
* Stock Quantity
* Availability Status
* Dealer

This module helps users monitor the available vehicle inventory.

---

### 👤 2. Customer Management

The Customer module stores customer information.

It includes:

* Customer Name
* Email
* Phone Number
* Address
* Preferred Vehicle Type

Customer records can be associated with orders, test drives, and service requests.

---

### 🏢 3. Dealer Management

The Dealer module maintains dealer information such as:

* Dealer Name
* Dealer Code
* Location
* Phone Number
* Email Address

Dealers can be associated with vehicles and vehicle orders.

---

### 🛒 4. Vehicle Order Management

The Vehicle Order module manages customer vehicle purchases.

An order connects:

**Customer → Vehicle → Dealer → Order**

The system checks vehicle stock before an order can be confirmed.

If the vehicle is unavailable, the order is prevented from being confirmed.

---

### 🚗 5. Test Drive Management

The Test Drive module manages customer test-drive appointments.

It stores:

* Customer
* Vehicle
* Test Drive Date
* Test Drive Status

Automated reminders are sent for upcoming test drives.

---

### 🔧 6. Service Request Management

The Service Request module handles post-purchase service requirements.

It stores:

* Customer
* Vehicle
* Service Date
* Issue Description
* Service Status

This allows dealership users to track service requests efficiently.

---

# 🗂️ Salesforce Data Model

The project contains six major custom objects:

| Custom Object                | Purpose                                  |
| ---------------------------- | ---------------------------------------- |
| `Vehicle__c`                 | Stores vehicle and inventory information |
| `Vehicle_Dealer__c`          | Stores dealer information                |
| `Vehicle_Customer__c`        | Stores customer information              |
| `Vehicle_Order__c`           | Manages vehicle purchase orders          |
| `Vehicle_Test_Drive__c`      | Manages test-drive appointments          |
| `Vehicle_Service_Request__c` | Manages vehicle service requests         |

### Relationship Overview

```text
                  ┌──────────────────┐
                  │     Customer     │
                  └────────┬─────────┘
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
        Vehicle Order   Test Drive   Service Request
             │             │             │
             ▼             ▼             ▼
          Vehicle       Vehicle       Vehicle
             │
             ▼
           Dealer
```

---

# ⚙️ Automation

## 🔄 Salesforce Flow

Salesforce Flow is used to automate repetitive business processes.

### 1. Dealer Assignment Flow

When a new vehicle order is created:

```text
New Vehicle Order
        ↓
Get Order Information
        ↓
Identify Appropriate Dealer
        ↓
Assign Dealer to Order
        ↓
Update Order
```

This reduces manual dealer assignment and improves the order workflow.

---

### 2. Test Drive Reminder Flow

The system monitors upcoming test-drive appointments.

```text
Test Drive Created
        ↓
Check Appointment Date
        ↓
Identify Upcoming Test Drive
        ↓
Send Reminder Email
```

This helps reduce missed appointments and improves customer communication.

---

# 🛡️ Validation Rules

A major business rule in the project is **Vehicle Stock Validation**.

The system should not allow an order to be confirmed when the selected vehicle has no available stock.

### Example

```text
Vehicle Stock = 0
        ↓
User tries to Confirm Order
        ↓
Stock Validation
        ↓
❌ Order Confirmation Prevented
```

If stock is available:

```text
Vehicle Stock > 0
        ↓
Order Confirmation
        ↓
Stock Updated
        ↓
✅ Order Successfully Processed
```

This prevents incorrect orders and maintains inventory accuracy.

---

# 💻 Apex Development

Apex is used to implement advanced business logic that cannot be handled only through declarative configuration.

The project includes Apex logic for:

* Vehicle order processing
* Stock validation
* Order management
* Business logic handling

## Apex Trigger

An Apex Trigger is used in the vehicle order process.

The trigger:

1. Checks vehicle stock.
2. Prevents invalid order processing.
3. Processes confirmed transactions.
4. Updates vehicle stock.
5. Supports order status handling.

The trigger is kept lightweight, while the main business logic is handled through separate Apex classes.

### Order Processing Flow

```text
Vehicle Order
      ↓
Check Vehicle Stock
      ↓
 ┌───────────────┐
 │ Stock Available? │
 └───────┬───────┘
         │
    ┌────┴────┐
    │         │
   YES        NO
    │         │
    ▼         ▼
Confirm    Prevent Order
Order
    │
    ▼
Update Stock
```

---

# 🎨 Lightning Experience

The project uses **Salesforce Lightning Experience** to provide a centralized and user-friendly interface.

The Lightning application provides navigation to:

* 🚘 Vehicles
* 🏢 Dealers
* 👤 Customers
* 🛒 Orders
* 🚗 Test Drives
* 🔧 Service Requests

### UI Configuration

The project uses:

* Lightning App
* Lightning Record Pages
* Page Layouts
* Dynamic Forms
* Highlights Panel
* Related Lists
* Tabs

This provides users with easy access to relevant information.

---

# 📊 Reports & Dashboards

Reports and Dashboards are used to provide business visibility.

### Reports

Reports can be created to analyze:

* Vehicle inventory
* Vehicle orders
* Customers
* Test drives
* Service requests
* Pending orders

### Dashboards

Dashboards provide visual summaries of dealership operations.

Example dashboard c
