# 📘 Splunk Roles & Role-Based Access Control (RBAC)

---

# 1️⃣ Learning Objective

By the end, you will understand:

- Default roles in Splunk
- What each role does
- How to create a new role
- Role inheritance
- Role-Based Access Control (RBAC)
- Best practices for secure role management

---

# 2️⃣ Where to View Roles

Navigate to:

Settings → Access Controls → Roles

Here you will see default roles:

- admin
- can_delete
- power
- splunk-system-role
- user

You can also create custom roles.

---

# 3️⃣ Default Roles in Splunk

---

## 🔹 1. Admin Role

Highest privilege level.

Capabilities:

- Full system control
- Manage users
- Manage roles
- Manage indexes
- Configure authentication
- Install apps
- Modify system settings
- Access all indexes

Admin can:

- Create/delete roles
- Assign permissions
- Configure data inputs
- Modify retention policies

⚠ Should be assigned carefully.

---

## 🔹 2. can_delete Role

Purpose:

Allows deletion capabilities.

Capabilities include:

- delete_by_keyword
- edit_own_objects
- run_collect
- run_mcollect

Risks:

- Potential data loss
- Index deletion
- Search result removal

Use cautiously.

---

## 🔹 3. Power Role

Advanced search user.

Capabilities:

- Write complex SPL queries
- Create dashboards
- Create reports
- Save searches
- Advanced data analysis

Does NOT have:

- Full administrative privileges

Suitable for:

- SOC analysts
- Advanced users
- Reporting teams

---

## 🔹 4. splunk-system-role

System-level management.

Capabilities:

- Monitor Splunk health
- Manage system performance
- Configure data inputs
- Index-level operations

Primarily used for:

- Infrastructure administrators

---

## 🔹 5. User Role

Standard user role.

Capabilities:

- Run searches
- View dashboards
- Save searches
- Access permitted indexes

Limitations:

- Cannot manage users
- Cannot modify system settings

Default role for new users.

---

# 4️⃣ Creating a New Role

Steps:

1. Go to Settings → Roles
2. Click New Role
3. Enter Role Name
4. (Optional) Inherit from existing role
5. Assign capabilities
6. Assign index permissions
7. Save

⚠ Role name cannot be changed after creation.

---

## 🔹 Role Inheritance

You can inherit permissions from:

- admin
- power
- user
- can_delete

Example:

NewRole inherits from power → gets search capabilities  
Add custom permissions on top.

---

# 5️⃣ What Can Be Configured in a Role?

Inside role configuration:

---

## 🔹 Capabilities

Define:

- What actions user can perform
- Administrative privileges
- Search permissions
- App permissions

---

## 🔹 Indexes

Control:

- Which indexes user can search
- Read access
- Write access
- Restricted indexes

---

## 🔹 Restrictions

Define:

- Search filters
- Data access limitations
- Index restrictions

---

## 🔹 Resources

Set limits on:

- Search concurrency
- Disk usage
- CPU usage
- Scheduled searches

---

# 6️⃣ What is Role-Based Access Control (RBAC)?

RBAC = Role-Based Access Control

Instead of assigning permissions to each user:

Users are assigned roles.

Roles contain permissions.

This simplifies access management.

---

# 7️⃣ Benefits of RBAC in Splunk

---

## 🔹 Granular Access Control

- Define fine-grained permissions
- Restrict index access
- Control capabilities precisely

---

## 🔹 Reduced Administrative Complexity

- Manage roles, not individual permissions
- Scales easily

---

## 🔹 Enhanced Security

- Prevent unauthorized access
- Restrict sensitive data exposure

---

## 🔹 Audit & Compliance

- Clear access mapping
- Role-based activity tracking
- Regulatory compliance readiness

---

# 8️⃣ Implementing RBAC – Step-by-Step

---

## Step 1: Define Organizational Roles

Examples:

- Administrator
- Security Analyst
- SOC Manager
- Data Viewer

---

## Step 2: Assign Capabilities

Determine:

- Who can search?
- Who can delete?
- Who can manage users?
- Who can modify indexes?

---

## Step 3: Configure Role in Splunk

Settings → Roles → Create or Edit Role

---

## Step 4: Assign Users to Roles

Settings → Users → Assign Role

---

# 9️⃣ Principle of Least Privilege

Golden Rule:

Give only necessary permissions.

Avoid:

- Assigning admin role unnecessarily
- Giving delete capabilities broadly
- Allowing unrestricted index access

Least privilege reduces:

- Insider threats
- Data breaches
- Configuration damage

---

# 🔟 Best Practices for RBAC

✔ Carefully design roles before implementation  
✔ Regularly review role assignments  
✔ Remove unused roles  
✔ Audit role capability changes  
✔ Test roles in staging before production  
✔ Document role structures  

---

# 1️⃣1️⃣ Real-World Role Structure Example

---

## Administrator

- Full system control
- User management
- Configuration changes

---

## Analyst

- Run searches
- Create dashboards
- Access security indexes

---

## Data Viewer

- View dashboards only
- No search modification
- Limited index access

---

# 1️⃣2️⃣ Brief Explanation

Splunk implements Role-Based Access Control (RBAC), where users are assigned roles instead of individual permissions. Each role defines capabilities, index access, and system privileges. Default roles include admin, power, user, can_delete, and splunk-system-role. RBAC improves security, simplifies administration, and enforces least privilege principles. Custom roles can be created with inherited capabilities and fine-grained index control.

---

# 🔥 Final Takeaway

Roles define power.
Users inherit capabilities.
RBAC controls access.

Without RBAC:

Chaos.

With properly designed RBAC:

Secure, scalable, enterprise-grade Splunk deployment.

---

**✍️ Notes By Abhishek (Ez Abyss)**
