# Active-Directory-Group-Policy-Windows-Server-2016-
Objectives
Set up Active Directory Domain Services, create users and Organizational Units, and apply (GPO) to enforce user restrictions.

Environment
Windows Server 2016 (Domain Controller)
VirtualBox VM
Domain: lab1.local

# Step 1: Install Active Directory Domain Services
Open Server Manger
Click manager-Add Roles and Features
Select: Role-based or feature-based installation
Choose server: Active Directory Domain Services and install

# Step 2: Promote to Domain Controller
Click notification flag
Select Promote this server to a domain controller
Choose:Add a new forest
Domain name:lab1.local and set DSRM password
complete installation and reset

# Step 3: Create Organizational Unit 
Open Active Directory Users and Computers
Right-click domain: lab1.local
Click:New then Organizational Unit
Name:Employees

# Step 4: Create User Account
Right-click Employees OU
Click:New → User
Enter:First name: John, Last name: Doe, Username: jdoe
Set password

# Step 5: Create Group Policy Object (GPO)
Open:gpmc.msc
Navigate:Domains → lab1.local → Group Policy Objects
Right-click → New
Name:Employee Lockdown Policy

# Step 6: Configure GPO Settings
Edit the GPO:
Navigate:User Configuration → Administrative Templates → Control Panel
Set:Prohibit access to Control Panel → Enabled

# Step 7: Link GPO to OU
Domains → lab1.local → Employees
Right-click:Link an Existing GPO
Select:Employee Lockdown Policy

# Step 8: Apply Group Policy
Login as user:LAB1\jdoe
Run:gpupdate /force
Log out and log back in.

# Step 9: Verify Policy Application
Run:gpresult /r
Confirm: Employee Lockdown Policy

# Step 10: Test Restriction
open cmd
Run:control
Expected result:"Access to Control Panel is blocked"

# Key Skills Learned
Active Directory setup and domain configuration
User and OU management
Group Policy creation and deployment
Troubleshooting GPO application issues
Understanding user vs computer policies

# Troubleshooting Performed
Resolved login restriction issues caused by User Rights Assignment
Fixed GPO not applying due to incorrect OU placement
Verified policy application using gpresult
Ensured correct domain login format (LAB1\username)
Allow vs Deny logic
