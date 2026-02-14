# Day 09 – Linux User & Group Management

## Objective
The objective of Day 09 was to gain hands-on experience with **Linux user and group management**.  
This included creating users and groups, assigning users to multiple groups, and configuring shared directories with proper permissions for collaboration.

## Users & Groups
- Users created:
    - tokyo
    - berlin
    - professor
    - nairobi

- Groups created:
    - developers
    - admins
    - project-team

---

## Group Assignments
| User      | Groups Assigned           |
|-----------|---------------------------|
| tokyo     | developers, project-team  |
| berlin    | developers, admins        |
| professor | admins                    |
| nairobi   | project-team              |

---

## Task 1: User Creation

Create three users with home directories and passwords:
- `tokyo`
- `berlin`
- `professor`

<img width="703" height="363" alt="image" src="https://github.com/user-attachments/assets/c9cf208d-31af-439f-b9d7-cc8bf4252e0a" />

**Verify:** Check `/etc/passwd` and `/home/` directory

<img width="981" height="700" alt="image" src="https://github.com/user-attachments/assets/3a2b1da9-c424-4eb4-9702-76d54135fe03" />

---

### Task 2: Create Groups 

Create two groups:
- `developers`
- `admins`
  
<img width="953" height="702" alt="image" src="https://github.com/user-attachments/assets/12c65020-14d7-4be7-bd19-ed3a5d37a21c" />

**Verify:** Check `/etc/group`

<img width="1070" height="317" alt="image" src="https://github.com/user-attachments/assets/29e09516-7be7-407b-98de-e98567d2e7d7" />

---

### Task 3: Assign to Groups 

Assign users:
- `tokyo` → `developers`
- `berlin` → `developers` + `admins` (both groups)
- `professor` → `admins`

<img width="931" height="85" alt="image" src="https://github.com/user-attachments/assets/9a86b5d7-3db2-4477-92da-8f89e44a481d" />

**Verify:** Use appropriate command to check group membership

<img width="1367" height="84" alt="image" src="https://github.com/user-attachments/assets/69f30c14-5119-413a-8d19-4d1b06c6fc94" />
<img width="1366" height="174" alt="image" src="https://github.com/user-attachments/assets/d03a5d4a-014e-4b02-8ca1-fe7e63687cf9" />

---
