# 📘 ER Diagram Design — Company Structure

## 📝 Task Overview

This repository contains an **Entity-Relationship (ER) diagram** based on a company's structure and its key business rules. The focus is on capturing relationships between employees, departments, projects, and dependents in a realistic business scenario.

---

## 🧱 Entities & Attributes

### 👨‍💼 Employee
- **Attributes**:  
  - `SSN` (Primary Key)  
  - `Fname`  
  - `Lname`  
  - `BirthDate`  
  - `Gender`  
- **Business Rules**:  
  - Each employee is **assigned to exactly one department**  
  - May **supervise other employees** (recursive relationship)  
  - May **have dependents** (if still employed)  
  - Can **work on multiple projects**, with `WorkingHours` recorded for each

### 🏢 Department
- **Attributes**:  
  - `DNUM` (Primary Key)  
  - `DName`  
  - `Locations` (Multivalued)  
- **Business Rules**:  
  - **Managed by one employee**, with `HireDate` as part of the relationship  
  - May **include multiple employees**  
  - May **manage multiple projects**

### 🗂️ Project
- **Attributes**:  
  - `PNumber` (Primary Key)  
  - `PName`  
  - `Location`  
  - `City`  
- **Business Rules**:  
  - **Assigned to one department**  
  - **Many employees work on each project**, with `WorkingHours` tracked

### 👨‍👩‍👧 Dependent
- **Attributes**:  
  - `DependentName` (Primary Key under Employee)  
  - `Gender`  
  - `BirthDate`  
- **Business Rules**:  
  - Linked to **one employee only**  
  - **Exists only** while the employee is employed

---

## 🔁 Relationships & Constraints

- **Supervision (Recursive)**  
  - One employee may supervise others (self-relationship)

- **Works On**  
  - Many-to-many between `Employee` and `Project`  
  - Relationship includes `WorkingHours`

- **Manages**  
  - One-to-one between `Employee` and `Department`  
  - Includes `HireDate` as an attribute

- **Belongs To**  
  - One-to-many: A department has many employees  
  - Each employee belongs to exactly one department

- **Assigned To**  
  - One-to-many: A department has many projects

- **Has Dependent**  
  - One-to-many: An employee may have multiple dependents  
  - Dependents are deleted when the employee leaves

---

## 📌 Design Guidelines

When designing the ER diagram:
- Use **rectangles** for entities  
- Use **ovals** for attributes  
- Use **diamonds** for relationships  
- Mark **primary keys**, **foreign keys**, and **multivalued attributes** clearly  
- Show **cardinality** (e.g., 1:N, M:N) and **participation** (total or partial)

---
