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
Defination- Lightning App is a Salesforce UI configuration that provides a customized workspace for users.It allows developers to control which objects, tabs, and navigation items appear on the frontend, without writing any code.

-> What I Built Using Lightning App
For the To-Do application, a custom Lightning App was created to provide a focused and clean user interface.
The app was configured using Salesforce App Manager and includes only the To-Do custom object.
This helps users easily access To-Do records, list views, and record details without unnecessary navigation.

---

### 3. Page Layout Customization
Defination- Page Layout Customization in Salesforce is used to control how a record’s detail page appears to users.It defines which fields, buttons, and related lists are visible, their order, and how they are grouped on the page.
Custom page layout is configured to:
- Organize fields logically
- Improve usability
- Display important fields prominently
For the To-Do application, the page layout was customized to improve clarity and usability.
Only relevant fields such as Task Name, Due Date, Status, and Completion flag were displayed.
Fields were arranged logically so users can quickly understand task details and update records efficiently.

---

### 4. List Views
Defination- List Views in Salesforce are used to display a filtered list of records based on specific criteria.They allow users to quickly view, filter, and manage records without opening each record individually.
In the To-Do application, multiple List Views were created to organize tasks based on their status and due dates.
Examples include:
- Pending Tasks – tasks that are not yet completed
- Overdue Tasks – tasks whose due date has passed
- Completed Tasks – tasks marked as completed
These list views help users quickly filter and manage tasks.

---

### 5. Validation Rule 
Initially, a validation rule was created with the following logic:

- If `Status = Completed`
- Then `Is Completed` checkbox must be checked

This ensured data consistency but caused usability issues during automation.

---

### 6. Record-Triggered Flow Automation (Final Solution for validation rule issue)
Defination- Record-Triggered Flow is a Salesforce automation that runs automatically when a record is created, updated, or deleted.
It is used to perform actions without any manual user intervention, based on changes in data.

To improve user experience and automate business logic, the validation rule was removed and replaced with a **Record-Triggered Flow**.

#### Flow Details
- **Flow Type:** Record-Triggered Flow (After Save)
- **Trigger:** When a To-Do record is created or updated
- **Entry Condition:** Status equals `Completed`
- **Action:** Automatically updates `Is_Completed__c` to `TRUE`

#### Why Flow Instead of Validation Rule?
Validation rules execute **before** record-triggered flows.  
This caused save-time errors when users marked a task as completed without manually checking the checkbox.

- A Record-Triggered Flow was used to automatically synchronize the task status with the completion checkbox.
- A separate Validation Rule was implemented to ensure that a Due Date is provided for every To-Do record.
- Both were kept independent to maintain clear separation between data validation and automation logic.

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
