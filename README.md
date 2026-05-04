# User Management UI Specification

## Overview
This document defines the user interface requirements and behavior for the User Management screen. It is intended for developers who will implement the frontend.

## Assumptions
- This is a web-based admin panel
- Data is provided via REST API
- Authentication is already handled

## Purpose
The User Management screen enables administrators to:
- View users
- Create new users
- Edit existing users
- Enable/disable users
- Filter users

---

## Layout Structure

The screen is divided into two main sections:

### Left Panel (User List)
- Displays a table of existing users
- Columns:
  - ID
  - User Name
  - Email
  - Enabled (true/false)
- Controls:
  - **+ New User** button → clears the form on the right
  - **Hide Disabled User** checkbox → filters out disabled users

---

### Right Panel (User Form)
- Displays a form for creating or editing a user
- Fields:
  - Username (required)
  - Display Name (required)
  - Phone (optional)
  - Email (required, valid format)
  - User Roles (Dropdown: Guest, Admin, SuperAdmin)
  - Enabled (Checkbox)
- Action:
  - **Save User** button → saves or updates user data

---

## Initial Page State
When the page loads:
- A loading spinner is displayed while fetching data
- The user list is populated on the left panel
- The form on the right is empty and ready for input
- If no users exist → display: **"No users found"**

---

## UI Components

### 1. Header
- Title: **User Management**

---

### 2. User Table (Left Panel)

| Column   | Description              |
|----------|--------------------------|
| ID       | Unique identifier        |
| User Name| Username                 |
| Email    | User email               |
| Enabled  | true / false             |

---

### 3. User Form (Right Panel)

Form fields:
- Username → text input
- Display Name → text input
- Phone → text input
- Email → email input
- User Roles → dropdown (Guest, Admin, SuperAdmin)
- Enabled → checkbox

---

## User Interactions

### Create New User
- Clicking **New User**:
  - Clears all form fields
  - Sets default values (Enabled = false)

---

### Select User
- Clicking a row in the table:
  - Populates the form with selected user data

---

### Save User
- Clicking **Save User**:
  - Validates all required fields
  - Sends data to backend (POST or PUT)
  - Shows success message on completion

---

### Hide Disabled Users
- When checked:
  - Filters out users where Enabled = false
- Works in real-time

---

## Validation Rules

- Username → required
- Display Name → required
- Email → required and must be valid
- Role → must be selected

---

## States & Feedback

### Loading State
- Show spinner while fetching users

### Empty State
- Show: "No users found"

### Error State
- Show: "Something went wrong. Please try again."

### Success Messages
- "User saved successfully"

---

## Accessibility
- All inputs must have labels
- Keyboard navigation must be supported
- Proper focus handling required

---

## Responsive Design

### Desktop
- Two-column layout (table + form)

### Mobile
- Stack layout (table above form)
- Scrollable table

---

## Performance
- Debounce filtering (Hide Disabled toggle)
- Avoid unnecessary re-renders

---

## Security
- Only authorized users can access
- Backend must validate all inputs
