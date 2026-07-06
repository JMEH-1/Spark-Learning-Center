========================================================================
📋 DEPLOYMENT OVERVIEW
========================================================================
Spark Learning Center is a small and growing IT technical school. This 
Active Directory deployment provides a practical organizational layout to 
support day-to-day learning and on-site lab computers. The directory 
structure is built to streamline user management, ensure consistent 
desktop branding across student PCs, and provide a clear framework that 
can easily expand as the school grows.

========================================================================
📁 DIRECTORY HIERARCHY MAP
========================================================================
📁 Spark Learning Center (OU)
├── 📁 Finance (OU)
│   └── 👤 Peter (User)
├── 📁 HR (OU)
│   └── 👤 Sara (User)
├── 📁 IT (OU)
│   └── 👤 Ali (User)
├── 📁 Students (OU)
│   └── 👤 Tommy (User)
└── 📁 SecGroups (OU)
    ├── 🛡️ Finance_SecGroup (Security Group)
    ├── 🛡️ HR_SecGroup (Security Group)
    ├── 🛡️ IT_SecGroup (Security Group)
    ├── 🛡️ Staff_SecGroup (Security Group)
    └── 🛡️ Students_SecGroup (Security Group)

========================================================================
💾 FILE SHARE & NETWORK DRIVE SPECIFICATIONS
========================================================================
To optimize day-to-day learning and operations, network shares are 
provisioned via Group Policy Preferences (GPP) and secured using Access-
Based Enumeration (ABE) to maintain institutional confidentiality.

Drive | Share Name    | Target Directory UNC Path        | Target Security Group
------|---------------|----------------------------------|----------------------
 [F:] | FIN           | \\server\shares\finance          | Finance_SecGroup
 [H:] | HR            | \\server\shares\hr               | HR_SecGroup
 [I:] | IT            | \\server\shares\it               | IT_SecGroup
 [S:] | Students      | \\server\shares\students         | Students_SecGroup

========================================================================
🛡️ ACTIVE DIRECTORY SECURITY GROUP NESTING
========================================================================
A hierarchical nested group structure minimizes administrative overhead 
and establishes a ready-made framework for future organizational growth.

Structure:
└── 🛡️ Staff_SecGroup
    ├── 🛡️ Finance_SecGroup (Member)
    ├── 🛡️ HR_SecGroup (Member)
    └── 🛡️ IT_SecGroup (Member)

Implementation Notes:
* Role-Based Access: RDP permissions are assigned to the parent Staff_SecGroup.
  Users in nested departmental security groups (Finance, HR, and IT)
  receive the same access through group membership, simplifying permission
  management. 
* Administrative Efficiency: Prevents the duplication of access control 
  lists (ACLs) across individual departments and centralizes endpoint 
  access management.

========================================================================
⚙️ GROUP POLICY OBJECTS (GPO) CORE CONFIGURATION
========================================================================
Linked OU: Spark Learning Center > Students

* Policy Setting: Enforcement of a static, unchangeable desktop background.
* Technical Path: User Configuration > Policies > Administrative Templates 
  > Desktop > Desktop > "Desktop Wallpaper" (Enabled) & "Prevent changing 
  wallpaper" (Enabled).
* Business Case: Maintains institutional branding consistency across 
  on-site learning PCs, ensures a standardized technical environment, 
  and maintains a professional look across lab workstations.

========================================================================
🖼️ ARCHITECTURE DIAGRAM ATTACHMENT
========================================================================
View the complete Active Directory structure visualization by opening the included
png named OUSTRUCT.png
