# 🚀 Enterprise Infrastructure Deployment: Spark Learning Center

## 🎯 Strategic Project Mission
Spark Learning Center is an agile, emerging technical institution dedicated to providing high-quality IT education. To facilitate seamless, day-to-day operations and student learning, this infrastructure deployment establishes a scalable Active Directory foundation optimized for on-site, hardware-intensive lab environments. 

This environment is engineered to enforce strict institutional branding consistency, streamline endpoint administration, and provide an elastic, standardized structural layout designed to absorb immediate organizational and headcount growth.

---

## 🗺️ Active Directory Logical Architecture

### Organizational Unit (OU) Topology

![Spark Learning Center OU Structure](OUSTRUCT.png)

```text
Spark Learning Center [OU]
├── Finance [OU]
│   └── Peter [User]
├── HR [OU]
│   └── Sara [User]
├── IT [OU]
│   └── Ali [User]
├── Students [OU]
│   └── Tommy [User]
└── SecGroups [OU]
    ├── Finance_SecGroup [Global Security Group]
    ├── HR_SecGroup [Global Security Group]
    ├── IT_SecGroup [Global Security Group]
    ├── Staff_SecGroup [Global Security Group]
    └── Students_SecGroup [Global Security Group]
```

### Identity Access Management (IAM) Group Hierarchies
To optimize administrative overhead, a hierarchical nested group structure is implemented to manage network and workstation access permissions.

```text
Staff_SecGroup (Parent)
├── Finance_SecGroup (Nested Member)
├── HR_SecGroup (Nested Member)
└── IT_SecGroup (Nested Member)
```

*   **Inheritance-Based Access:** Granting the parent `Staff_SecGroup` Remote Desktop Protocol (RDP) permissions automatically passes those rights down to the child specialized staff groups (Finance, HR, IT). 
*   **Administrative Efficiency:** Prevents the duplication of access control lists (ACLs) across individual departments and centralizes endpoint access management.

---

## 💾 Storage & Policy Provisioning Matrix

### Network File Shares
To optimize day-to-day learning and operations, network shares are provisioned via Group Policy Preferences (GPP) and secured using Access-Based Enumeration (ABE) to maintain institutional confidentiality.

| Mapping | Volume Name | Logical Path (UNC) | Target Identity Scope |
| :---: | :--- | :--- | :--- |
| **F:** | FIN | `\\server\shares\finance` | Finance Department Staff |
| **H:** | HR | `\\server\shares\hr` | HR Department Staff |
| **I:** | IT | `\\server\shares\it` | IT Infrastructure Staff |
| **S:** | Students | `\\server\shares\students` | Enrolled Student Cohorts |

### Group Policy Enforcement Profiles

#### Desktop Environment Constraints
*   **Target Boundary:** `Spark Learning Center > Students` [OU Scope]
*   **Enforced Configurations:**
    1.  *Desktop Wallpaper* (Status: **Enabled**)
    2.  *Prevent changing wallpaper* (Status: **Enabled**)
*   **Registry/GPO Node Path:** `User Configuration > Policies > Administrative Templates > Desktop > Desktop`
*   **Business Justification:** Maintains institutional branding consistency across on-site learning PCs, ensures a standardized technical environment, and maintains an elite professional look across lab workstations.
