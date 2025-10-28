# laptop-request-catalog-item-nm
ServiceNow Catalog Item to automate laptop requests with dynamic forms, UI policies, and update set governance.

# 💻 Laptop Request Catalog Item

## Project Overview

This project implements a **dynamic Service Catalog Item** within the ServiceNow platform to modernize and automate the organizational process for requesting work laptops. It replaces a slow, manual, and error-prone workflow with a fast, user-guided digital experience, ensuring accurate data collection and robust deployment governance.

This solution was developed as part of the SmartInternz NME program in collaboration with ServiceNow and SmartBridge.

---

## 🎯 Problem Statement

Employees rely on a quick, efficient process to get essential equipment. The previous manual process resulted in **delays, confusion, and inaccurate data capture** due to the lack of dynamic form behavior and clear guidance.

The objective was to create a Catalog Item that provides:
1.  **Speed and Efficiency:** A single digital submission point.
2.  **User Guidance:** Dynamic fields and clear instructions.
3.  **Usability:** A form reset option for better user experience (UX).
4.  **Governance:** All configurations tracked for safe deployment.

---

## ✨ Key Features Implemented

| Feature | ServiceNow Component | Benefit to the User/Process |
| :--- | :--- | :--- |
| **Dynamic Form Fields** | **Catalog UI Policy** | Shows the **'Accessories Details'** field only when the **'Additional Accessories'** checkbox is selected, ensuring required details are captured when relevant. |
| **Form Reset Functionality** | **UI Action** on `sc_cart` table | Allows the user to quickly clear the form and start over, significantly improving UX. |
| **Version Control & Migration** | **Local Update Set** | All changes are bundled into the **'Laptop Request'** update set, guaranteeing safe and traceable deployment to other instances. |
| **Structured Request** | **Catalog Item & Variables** | Replaces unstructured emails/forms with a clear, mandatory set of data points (e.g., Laptop Model, Justification). |

---

## 🛠️ Implementation Steps:

The following outlines the configuration sequence within the ServiceNow instance to deploy this solution:

### Step 1: Governance Setup
1.  Create and activate a **Local Update Set** named **"Laptop Request"** to capture all subsequent configuration changes.

### Step 2: Service Catalog Item Creation
1.  Created the main item: **Laptop Request**.
2.  Configured the item under the **Service Catalog** and **Hardware** category.

### Step 3: Variables Definition
Variables were defined to structure data capture:
| Variable Name | Type | Technical Name |
| :--- | :--- | :--- |
| Laptop Model | Single Line Text | `laptop_model` |
| Justification | Multi Line Text | `justification` |
| Additional Accessories | Checkbox | `additional_accessories` |
| Accessories Details | Multi Line Text | `accessories_details` |

### Step 4: Dynamic Behavior Implementation
1.  Created a **Catalog UI Policy** (Short Description: *Show Accessories Details*).
2.  **Condition:** `additional_accessories` **is** `true`.
3.  **UI Policy Action:** Set `accessories_details` to **Visible: True** and **Mandatory: True**.

### Step 5: User Experience Action
1.  Created a **Client UI Action** named **"Reset Form"**.
2.  **Table:** `sc_cart` (to appear on the form/cart view).
3.  **Script:** Uses `g_form.clearForm()` to clear the fields and confirm with an alert.

### Step 6: Deployment & Migration
1.  Set the Update Set to **Complete** and **Exported to XML**.
2.  Imported, Previewed, and **Committed** the Update Set in the target instance for final deployment.
