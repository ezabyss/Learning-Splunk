# 📘 Managing Users in Splunk

---

# 1️⃣ Learning Objective

By the end, you will understand:

- How to view existing users in Splunk
- How to edit user settings
- How to assign roles
- How to create new users
- How user privileges work
- How administrators manage access

---

# 2️⃣ Accessing User Management

Navigate to:

Settings → Access Controls → Users

Here you can view:

- Username
- Status (Active/Inactive)
- Last login
- Assigned roles
- Default app

---

# 3️⃣ Default Administrator Account

When Splunk is installed:

- An admin account is created
- This account has full privileges
- It is assigned the `admin` role

The administrator can:

- Manage users
- Create roles
- Install apps
- Manage indexes
- Configure authentication
- Control system settings

---

# 4️⃣ Editing an Existing User

Click on:

Username → Edit

Or use:

Actions → Edit

---

## 🔹 Editable Settings

You can modify:

- Email address
- Password
- Time zone
- Default app
- Assigned roles
- Force password change on next login

---

## 🔹 Password Requirements

Minimum requirement:

- At least 8 characters

(Password policy can be strengthened depending on configuration.)

---

# 5️⃣ Additional User Actions

Under "Actions", you can:

---

## 🔹 Edit

Modify user details.

---

## 🔹 Clone

Creates a new user with:

- Same roles
- Same permissions
- Same default app

Useful for quickly duplicating role structure.

---

## 🔹 View Capabilities

Shows:

- All capabilities assigned through roles
- Permissions inherited

Admin users will see most capabilities enabled.

---

## 🔹 View Indexes

Shows:

- Which indexes the user has access to
- Inherited index permissions

---

## 🔹 Search As

Allows:

- Perform search as that specific user
- Useful for troubleshooting access issues

---

# 6️⃣ Creating a New User

Click:

New User

---

## 🔹 Required Fields

- Username
- Password
- Confirm password
- Role assignment

Optional:

- Email address
- Custom time zone
- Default app selection

---

## 🔹 Default Role Behavior

If created by admin:

- Default assigned role is `user`

You can change role before saving.

---

# 7️⃣ Assigning Roles

Roles determine:

- What the user can do
- Which indexes they can access
- Whether they can install apps
- Whether they can manage users

Example roles:

- user
- power
- admin
- custom roles

---

# 8️⃣ Example Scenario

Administrator creates new user:

Username: Ravi  
Role: user  

Result:

- Limited permissions
- Cannot manage indexes
- Cannot manage users
- Can search data (based on role permissions)

After login:

- Last login timestamp updates
- Status remains active

---

# 9️⃣ Managing Multiple Users

Administrator can:

- Create multiple users
- Assign different roles
- Separate responsibilities
- Enforce least privilege

Example structure:

Security Analyst → Search access only  
SOC Manager → Dashboard + Reporting access  
Administrator → Full system access  

---

# 🔟 Active vs Inactive Users

Each user has status:

- Active
- Disabled

Disabled users:

- Cannot log in
- Retain configuration

Useful for:

- Employee exit management
- Temporary suspension

---

# 1️⃣1️⃣ Best Practices for User Management

✔ Follow Least Privilege principle  
✔ Avoid giving admin role unnecessarily  
✔ Regularly review user accounts  
✔ Disable inactive users  
✔ Enforce password complexity  
✔ Monitor login activity  
✔ Audit user capability changes  

---

# 1️⃣2️⃣ Security Considerations

User mismanagement can lead to:

- Data leaks
- Unauthorized access
- Compliance violations
- Privilege escalation

Proper user management ensures:

- Controlled access
- Secure operations
- Compliance readiness

---

# 1️⃣3️⃣ Brief Explanation

Splunk user management is handled through the Access Controls section. Administrators can create, edit, clone, and disable users. Each user is assigned one or more roles that determine their capabilities and index access. The system follows Role-Based Access Control (RBAC), where permissions are inherited from roles rather than assigned individually. Proper user management ensures secure and controlled access to the Splunk environment.

---

# 🔥 Final Takeaway

Users in Splunk are:

- Identity entities
- Role-driven
- Capability-controlled
- Security-sensitive

Admin controls access.
Roles define power.
Users inherit permissions.

Understanding user management = Secure Splunk deployment.

---

**✍️ Notes By Abhishek (Ez Abyss)**
