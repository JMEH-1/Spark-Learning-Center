# Enterprise Deployment Mission Statement

Spark Learning Center is an agile, emerging technical institution dedicated to providing high-quality IT education. To facilitate seamless, day-to-day operations and student learning, this infrastructure deployment establishes a scalable Active Directory foundation optimized for on-site, hardware-intensive lab environments. 

This environment is engineered to enforce strict institutional branding consistency, streamline endpoint administration, and provide an elastic, standardized structural layout designed to absorb immediate organizational and headcount growth.

---

# Directory Hierarchy Map

![Spark Learning Center OU Structure](OUSTRUCT.png)

* 📁 **Spark Learning Center (OU)**
  * 📁 **Finance (OU)**
    * 👤 Peter (User)
  * 📁 **HR (OU)**
    * 👤 Sara (User)
  * 📁 **IT (OU)**
    * 👤 Ali (User)
  * 📁 **Students (OU)**
    * 👤 Tommy (User)
  * 📁 **SecGroups (OU)**
    * 🛡️ Finance_SecGroup (Security Group)
    * 🛡️ HR_SecGroup (Security Group)
    * 🛡️ IT_SecGroup (Security Group)
    * 🛡️ Staff_SecGroup (Security Group)
    * 🛡️ Students_SecGroup (Security Group)

---

# File Share & Network Drive Specifications

To optimize day-to-day learning and operations, network shares are provisioned via Group Policy Preferences (GPP) and secured using Access-Based Enumeration (ABE) to maintain institutional confidentiality.

| Drive | Share Name | Target Directory UNC Path | Target OU / Audience |
| :---: | :--- | :--- | :--- |
| **[F:]** | FIN | `\\server\shares\finance` | Finance Department |
| **[H:]** | HR | `\\server\shares\hr` | HR Department |
| **[I:]** | IT | `\\server\shares\it` | IT Department |
| **[S:]** | Students | `\\server\shares\students` | Students Department |

---

# Active Directory Security Group Nesting

 A hierarchical nested group structure minimizes administrative overhead and establishes a ready-made framework for future organizational growth.

### Structure
* 🛡️ **Staff_SecGroup**
  * 🛡️ Finance_SecGroup *(Member)*
  * 🛡️ HR_SecGroup *(Member)*
  * 🛡️ IT_SecGroup *(Member)*

### Technical Justification
* **Inheritance-Based Access:** Granting the parent `Staff_SecGroup` Remote Desktop Protocol (RDP) permissions automatically passes those rights down to the child specialized staff groups (Finance, HR, IT). 
* **Administrative Efficiency:** Prevents the duplication of access control lists (ACLs) across individual departments and centralizes endpoint access management.

---

# Group Policy Objects (GPO) Core Configuration

**Linked OU:** `Spark Learning Center > Students`

* **Policy Setting:** Enforcement of a static, unchangeable desktop background.
* **Technical Path:** `User Configuration > Policies > Administrative Templates > Desktop > Desktop > "Desktop Wallpaper" (Enabled) & "Prevent changing wallpaper" (Enabled)`
* **Business Case:** Maintains institutional branding consistency across on-site learning PCs, ensures a standardized technical environment, and maintains an elite professional look across lab workstations.
