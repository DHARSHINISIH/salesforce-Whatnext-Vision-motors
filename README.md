
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

Example dashboard components:

```text
┌────────────────────┐
│ Vehicle Inventory  │
└────────────────────┘

┌────────────────────┐
│ Order Activity     │
└────────────────────┘

┌────────────────────┐
│ Test Drive Status  │
└────────────────────┘

┌────────────────────┐
│ Service Requests   │
└────────────────────┘
```

This allows management to understand business activity quickly.

---

# 🔐 Security

Security is implemented using Salesforce's standard security mechanisms.

### Security Components

* **Profiles** – Define basic user permissions.
* **Roles** – Help control record visibility.
* **Role Hierarchy** – Provides hierarchical access.
* **Permission Sets** – Provide additional permissions.
* **Sharing Rules** – Extend record access when required.
* **Object-Level Permissions** – Control access to objects.

The objective is to ensure that users have access only to the information required for their responsibilities.

---

# 🧪 Testing

The application was tested using multiple functional scenarios.

| Test Case                          | Expected Result                                  |
| ---------------------------------- | ------------------------------------------------ |
| Create valid vehicle               | Vehicle record created successfully              |
| Confirm order with available stock | Order can be processed                           |
| Confirm order with zero stock      | Order confirmation prevented                     |
| Create upcoming test drive         | Reminder automation triggered                    |
| Process pending order              | Order processed when required stock is available |

Testing helps ensure that the business rules, automation, and Apex logic work as expected.

---

# 🔄 Complete Business Workflow

The overall system workflow can be represented as:

```text
Customer
   ↓
Select Vehicle
   ↓
Schedule Test Drive
   ↓
Test Drive Reminder
   ↓
Create Vehicle Order
   ↓
Check Vehicle Stock
   ↓
┌──────────────────────┐
│ Stock Available?     │
└──────────┬───────────┘
           │
      ┌────┴────┐
      │         │
     YES        NO
      │         │
      ▼         ▼
Confirm      Keep Order
Order        Pending
      │
      ▼
Assign Dealer
      │
      ▼
Update Vehicle Stock
      │
      ▼
Vehicle Purchase
      │
      ▼
Service Request
      │
      ▼
Reports & Dashboards
```

---

# 🛠️ Technology Stack

### Salesforce

* Salesforce CRM
* Lightning Experience
* Custom Objects
* Custom Fields
* Object Relationships
* Validation Rules
* Salesforce Flow
* Apex
* Apex Triggers
* Reports
* Dashboards
* Profiles
* Roles
* Permission Sets
* Sharing Rules
* Dynamic Forms

### Development

* Apex
* SOQL
* Salesforce Flow
* Lightning Experience

---

# 📁 Project Structure

```text
WhatNext-Vision-Motors/
│
├── README.md
│
├── force-app/
│   └── main/
│       └── default/
│           ├── classes/
│           ├── triggers/
│           ├── objects/
│           ├── flows/
│           ├── layouts/
│           ├── permissionsets/
│           └── tabs/
│
├── docs/
│   ├── Project-Documentation.pdf
│   └── Screenshots/
│
└── sfdx-project.json
```

> Update the folder names above according to the actual structure of your Salesforce GitHub repository.

---

# 🚀 Deployment

The Salesforce metadata can be deployed between Salesforce environments using Salesforce deployment tools.

The project contains components such as:

* Custom Objects
* Custom Fields
* Relationships
* Validation Rules
* Flows
* Apex Classes
* Apex Triggers
* Lightning Pages
* Reports
* Dashboards

After deployment, each component should be tested to verify that the complete workflow is functioning correctly.

---

# 🔧 Maintenance & Troubleshooting

For maintaining the application, Salesforce monitoring tools can be used.

### Troubleshooting Process

```text
Identify Issue
      ↓
Reproduce the Issue
      ↓
Check Configuration
      ↓
Check Flow / Apex
      ↓
Review Debug Logs
      ↓
Fix the Issue
      ↓
Retest
      ↓
Deploy
```

For Apex-related issues, **Debug Logs and Apex Jobs** can be reviewed.

For Flow-related issues, Flow error details can be checked.

---

# 🌟 Key Features

* ✅ Centralized automotive CRM
* ✅ Vehicle inventory management
* ✅ Customer management
* ✅ Dealer management
* ✅ Vehicle order management
* ✅ Stock availability validation
* ✅ Automated dealer assignment
* ✅ Test-drive reminder automation
* ✅ Service request management
* ✅ Apex business logic
* ✅ Apex Trigger
* ✅ Lightning Experience UI
* ✅ Reports and Dashboards
* ✅ Salesforce security configuration
* ✅ Data validation
* ✅ End-to-end testing

---

# 🎓 Learning Outcomes

Through this project, I gained practical experience in:

* Salesforce CRM development
* Custom Object creation
* Object relationships
* Salesforce Flow automation
* Validation Rules
* Apex programming
* Apex Triggers
* SOQL
* Lightning Experience
* Reports and Dashboards
* Salesforce security
* Data management
* Testing and troubleshooting

The project helped me understand how **declarative Salesforce features and programmatic development can be combined to solve real-world business requirements.**

---

# 👩‍💻 Developer

**Dharshini Sivakumar**

Computer Science and Engineering – Allied with ARVR
RMK Engineering College

### Areas of Interest

* Salesforce Development
* Java Full Stack Development
* MERN Stack
* UI/UX Design
* AR/VR

---

# 📜 Project

**Project Name:** WhatNext Vision Motors – Shaping the Future of Mobility with Innovation and Excellence

**Platform:** Salesforce CRM

**Project Type:** Automotive Dealership Management System

---

## ⭐ If you find this project useful

Feel free to explore the project, review the Salesforce implementation, and provide feedback.

**Thank you for visiting this repository!** 🚗☁️


