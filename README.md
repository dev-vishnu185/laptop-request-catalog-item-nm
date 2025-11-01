# 💻 Laptop Request Catalog Item

Here you will find all the document files related to the **Laptop Request Catalog Item** project.

---

## 📅 Document Submission

**NOTE:** All dates mentioned in the PDFs are based on when this GitHub repository was submitted to faculty for review.

---

## 👥 Team Details

**Team ID:** NM2025TMID08851  
**Team Size:** 5  
**Team Leader:** Vishnukumar S  
**Team Members:**  
- Prabhaharan D  
- Prem Kumar M V  
- Pavankanth V  
- Mohammed Arsath K

---

## 📘 Project Overview

This project implements a **dynamic Service Catalog Item** within the ServiceNow platform to modernize and automate the organizational process for requesting work laptops. It replaces a slow, manual, and error-prone workflow with a fast, user-guided digital experience, ensuring accurate data collection and robust deployment governance.

This solution was developed as part of the **SmartInternz NME program** in collaboration with **ServiceNow** and **SmartBridge**.

---

## 🎯 Problem Statement

Employees rely on a quick, efficient process to get essential equipment. The previous manual process resulted in **delays, confusion, and inaccurate data capture** due to the lack of dynamic form behavior and clear guidance.

The objective was to create a Catalog Item that provides:
1. **Speed and Efficiency:** A single digital submission point  
2. **User Guidance:** Dynamic fields and clear instructions  
3. **Usability:** A form reset option for better user experience (UX)  
4. **Governance:** All configurations tracked for safe deployment

---

## 🛠️ Implementation Steps

The following outlines the configuration sequence within the ServiceNow instance to deploy this solution:

### Step 1: Governance Setup
- Created and activated a **Local Update Set** named **"Laptop Request"** to capture all configuration changes

### Step 2: Service Catalog Item Creation
- Created the main item: **Laptop Request**  
- Configured under the **Service Catalog** and **Hardware** category

### Step 3: Variables Definition

| Variable Name         | Type              | Technical Name           |
|-----------------------|-------------------|---------------------------|
| Laptop Model          | Single Line Text  | `laptop_model`           |
| Justification         | Multi Line Text   | `justification`          |
| Additional Accessories| Checkbox          | `additional_accessories` |
| Accessories Details   | Multi Line Text   | `accessories_details`    |

### Step 4: Dynamic Behavior Implementation
- Created a **Catalog UI Policy** (*Show Accessories Details*)  
- **Condition:** `additional_accessories` is `true`  
- **Action:** Set `accessories_details` to **Visible: True** and **Mandatory: True**

### Step 5: User Experience Action
- Created a **Client UI Action** named **"Reset Form"**  
- **Table:** `sc_cart`  
- **Script:** Uses `g_form.clearForm()` to clear fields and confirm with an alert

### Step 6: Deployment & Migration
- Marked Update Set as **Complete** and **Exported to XML**  
- Imported, Previewed, and **Committed** in the target instance

---

## 🔐 Instance Access & Policy Note

Due to security and platform compliance, the **NM instance link is not publicly shared** in this repository.

ServiceNow’s Developer Program Terms of Use specify that:
> “Developer instances are intended for personal use and learning. Sharing access or exposing instance links publicly may result in suspension or termination of access.”

To ensure responsible usage and protect proprietary configurations, this project follows best practices by keeping instance access private.

To view the working demo, please visit the **SmartInternz project workspace** and click on the **DEMO LINK** section.  
The ServiceNow instance link is attached there as a document and has been verified for evaluator access.
