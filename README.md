# Salesforce To-Do Application

This project is a simple Salesforce To-Do application built to demonstrate core Salesforce concepts such as custom objects, validations, Lightning apps, list views, and record-triggered flows.

The goal of this project is to showcase hands-on Salesforce development skills in a clean and interview-ready manner.

---

##  Features Implemented

### 1. Custom Object: To-Do
A custom object is created to manage To-Do items.

**Key Fields:**
- To Do Name (Text)
- Status (Picklist: Pending, In Progress, Completed)
- Priority (Picklist: Low, Medium, High)
- Due Date (Date)
- Description (Long Text)
- Is Completed (Checkbox)
- Overdue Status(Formula)

---

### 2. Lightning App
A custom Lightning App is created to provide a dedicated workspace for managing To-Do records.

- Includes To-Do object
- Clean navigation
- Easy access to list views and records

---

### 3. Page Layout Customization
Custom page layout is configured to:
- Organize fields logically
- Improve usability
- Display important fields prominently

---

### 4. List Views
Custom List Views are created for better task tracking:
- All To-Dos
- Completed To-Dos
- Pending To-Dos

These list views help users quickly filter and manage tasks.

---

### 5. Validation Rule 
Initially, a validation rule was created with the following logic:

- If `Status = Completed`
- Then `Is Completed` checkbox must be checked

This ensured data consistency but caused usability issues during automation.

---

### 6. Record-Triggered Flow Automation (Final Solution for validation rule issue)

To improve user experience and automate business logic, the validation rule was removed and replaced with a **Record-Triggered Flow**.

#### Flow Details
- **Flow Type:** Record-Triggered Flow (After Save)
- **Trigger:** When a To-Do record is created or updated
- **Entry Condition:** Status equals `Completed`
- **Action:** Automatically updates `Is_Completed__c` to `TRUE`

#### Why Flow Instead of Validation Rule?
Validation rules execute **before** record-triggered flows.  
This caused save-time errors when users marked a task as completed without manually checking the checkbox.

By using a record-triggered flow:
- The checkbox is updated automatically
- User-facing errors are avoided
- Business logic is handled by automation
- Salesforce order of execution is respected

This approach follows Salesforce automation best practices.

---
## Due Date Field Feature:


### 7. GitHub Documentation
This repository includes:
- Complete project documentation
- Screenshots of configuration (Object, Flow, App)
- Clear explanation of design decisions

---

##  How to Test the Application

1. Open the Salesforce To-Do App
2. Create a new To-Do record
3. Set Status to `Completed`
4. Leave `Is Completed` unchecked
5. Save the record

Result:  
The record saves successfully and the `Is Completed` checkbox is automatically checked by the flow.

---

##  Key Learnings
- Custom object and field creation
- Lightning App configuration
- Validation rule limitations
- Salesforce Order of Execution
- Record-triggered flow automation
- Best practices for user-friendly automation

---

##  Future Enhancements
- Due date reminders using scheduled flows
- Task priority field
- Email notifications
- Dashboard for task tracking

---

##  Author
**Harsh Saini**  
Salesforce Developer  
